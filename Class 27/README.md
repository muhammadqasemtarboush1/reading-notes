# Class 27

Live link: [API Deployment](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2027/)

## Configuring Django Settings: Best Practices

### Managing Django Settings: Issues

1. Different environments.
2. Sensitive data.
3. Sharing settings between team members.
4. Django settings are a Python code.

### Setting Configuration: Different Approaches

There is no built-in universal way to configure Django settings without hardcoding them.

But books, open-source and work projects provide a lot of recommendations and approaches on
how to do it best.

Let’s take a brief look at the most popular ones to examine their weaknesses and strengths.

1. settings_local.py
   The basic idea of this method is to extend all environment-specific settings in the
   settings_local.py file, which is ignored by VCS.
   ex: settings.py file:

```python
ALLOWED_HOSTS = ['example.com']
DEBUG = False
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'production_db',
        'USER': 'user',
        'PASSWORD': 'password',
        'HOST': 'db.example.com',
        'PORT': '5432',
        'OPTIONS': {
            'sslmode': 'require'
        }
    }
}
from .settings_local import *
```

in settings_local.py file:

```python
ALLOWED_HOSTS = ['localhost']
DEBUG = True
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'local_db',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

Pros: Secrets not in VCS.

Cons:

* settings_local.py is not in VCS, so you can lose some of your Django environment settings.
* The Django settings file is a Python code, so settings_local.py can have some non-obvious logic.
* You need to have settings_local.example (in VCS) to share the default configurations for developers.

### Separate settings file for each environment

This is an extension of the previous approach. It allows you to keep all configurations in
VCS and to share default settings between developers.

```html
settings/
├── __init__.py
├── base.py
├── ci.py
├── local.py
├── staging.py
├── production.py
└── qa.py
```

settings/local.py:

```python
from .base import *

ALLOWED_HOSTS = ['localhost']
DEBUG = True
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'local_db',
        'HOST': '127.0.0.1',
        'PORT': '5432',
    }
}
```

To run a project with a specific configuration, you need to set an additional parameter:
python manage.py runserver --settings=settings.local

```
python manage.py runserver --settings=settings.local
```

Pros:

* All environments are in VCS.
* It’s easy to share settings between developers.
  Cons:
* You need to find a way to handle secret passwords and tokens.
* “Inheritance” of settings can be hard to trace and maintain.

### Environment variables

To solve the issue with sensitive data, you can use environment variables.

```python
import os

SECRET_KEY = os.environ['SECRET_KEY']
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': os.environ['DATABASE_NAME'],
        'HOST': os.environ['DATABASE_HOST'],
        'PORT': int(os.environ['DATABASE_PORT']),
    }
}
```

This is the simplest example using Python os.environ and it has several issues:

* You need to handle KeyError exceptions.
* You need to convert types manually (see DATABASE_PORT usage).

To fix KeyError, you can write your own custom wrapper. For example:

```python
import os

from django.core.exceptions import ImproperlyConfigured


def get_env_value(env_variable):
    try:
        return os.environ[env_variable]
    except KeyError:
        error_msg = 'Set the {} environment variable'.format(var_name)
        raise ImproperlyConfigured(error_msg)


SECRET_KEY = get_env_value('SECRET_KEY')
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': get_env_value('DATABASE_NAME'),
        'HOST': get_env_value('DATABASE_HOST'),
        'PORT': int(get_env_value('DATABASE_PORT')),
    }
}
```

Also, you can set default values for this wrapper and add type conversion. But actually there is no need to write this
wrapper, because you can use a third-party library (we’ll talk about this later).

Pros:

* Configuration is separated from code.
* Environment parity – you have the same code for all environments.
* No inheritance in settings, and cleaner and more consistent code.
* There is a theoretical grounding for using environment variables – 12 Factors.
  Cons:
* You need to handle sharing default config between developers.

### 12 Factors

12 Factors is a collection of recommendations on how to build distributed web-apps that will be easy to deploy and scale
in the Cloud. It was created by Heroku, a well-known Cloud hosting provider.
As the name suggests, the collection consists of twelve parts:

1. Codebase
2. Dependencies
3. Config
4. Backing services
5. Build, release, run
6. Processes
7. Port binding
8. Concurrency
9. Disposability
10. Dev/prod parity
11. Logs
12. Admin processes

### django-environ

Based on the above, we see that environment variables are the perfect place to store settings.

Writing code using os.environ could be tricky sometimes and require additional effort to handle errors. It’s better to
use django-environ instead.
Technically it’s a merge of:

* envparse
* honcho
* dj-database-url
* dj-search-url
* dj-config-url
* django-cache-url

This app gives a well-functioning API for reading values from environment variables or text files, handful type
conversion

settings.py

```python
import environ

root = environ.Path(__file__) - 3  # get root of the project
env = environ.Env()
environ.Env.read_env()  # reading .env file

SITE_ROOT = root()

DEBUG = env.bool('DEBUG', default=False)
TEMPLATE_DEBUG = DEBUG

DATABASES = {'default': env.db('DATABASE_URL')}

public_root = root.path('public/')
MEDIA_ROOT = public_root('media')
MEDIA_URL = env.str('MEDIA_URL', default='media/')
STATIC_ROOT = public_root('static')
STATIC_URL = env.str('STATIC_URL', default='static/')

SECRET_KEY = env.str('SECRET_KEY')

CACHES = {'default': env.cache('REDIS_CACHE_URL')}
```

.env file:

```
DEBUG=True
DATABASE_URL=postgres://user:password@db.example.com:5432/production_db?sslmode=require
REDIS_CACHE_URL=redis://user:password@cache.example.com:6379/1
SECRET_KEY=Some-Autogenerated-Secret-Key
```

### Setting Structure

Instead of splitting settings by environments, you can split them by the source: Django, third- party apps (Celery, DRF,
etc.), and your custom settings.
File structure:

```
project/
├── apps/
├── settings/
│   ├── __init__.py
│   ├── djano.py
│   ├── project.py
│   └── third_party.py
└── manage.py
```

__init__.py file:

```python
from .django import *  # All Django related settings
from .third_party import *  # Celery, Django REST Framework & other 3rd parties
from .project import *  # You custom settings
```

Each module could be done as a package, and you can split it more granularly:

```
project/
├── apps/
├── settings/
│   ├── project
│   │   ├── __init__.py
│   │   ├── custom_module_foo.py
│   │   ├── custom_module_bar.py
│   │   └── custom_module_xyz.py
│   ├── third_party
│   │   ├── __init__.py
│   │   ├── celery.py
│   │   ├── email.py
│   │   └── rest_framework.py
│   ├── __init__.py
│   └── djano.py
└── manage.py
```

### Naming Conventions

Naming of variables is one of the most complex parts of development.

So is naming of settings. We can’t imply on Django or third-party applications,
but we can follow these simple rules for our custom (project) settings:

1. Give meaningful names to your settings.
2. Always use the prefix with the project name for your custom (project) settings.
3. Write descriptions for your settings in comments.

### Django Settings: Best practices

* Keep settings in environment variables.
* Write default values for production configuration (excluding secret keys and tokens).
* Don’t hardcode sensitive settings, and don’t put them in VCS.
* Split settings into groups: Django, third-party, project.
* Follow naming conventions for custom (project) settings.

---

### Conclusion

The Settings file is a small but very important part of any Django project.

If you do it wrong, you’ll have a lot of issues during all phases of development.

But if you do it right, it will be a good basis for your project that will allow it to grow
and scale in the future.

Using the environment variables approach, you can easily switch from a monolith to
microservice architecture, wrap your project in Docker containers,
and deploy it in any VPS or Cloud hosting platform such as: Amazon, Google Cloud, or
your own Kubernetes cluster.

---

## SSH

### What Is SSH?

SSH, or Secure Shell Protocol, is a remote administration protocol that allows users to
access, control, and modify their remote servers over the internet.

SSH service was created as a secure replacement for the unencrypted Telnet and uses
cryptographic techniques to ensure that all communication to and from the remote server
happens in an encrypted manner.

It provides a mechanism for authenticating a remote user,
transferring inputs from the client to the host, and relaying the output back to the client.

### Encryption techniques

* Symmetrical encryption
  * Symmetric encryption is a form of encryption where a secret key is used for both encryption and decryption of a
      message by both the client and the host. Effectively, anyone possessing the key can decrypt the message being
      transferred.
* Asymmetrical encryption
  * Unlike symmetrical encryption, asymmetrical encryption uses two separate keys for encryption and decryption. These
      two keys are known as the public key and the private key. Together, both these keys form a public-private key
      pair.
* Hashing
  * One-way hashing is another form of cryptography used in Secure Shell Connections. One-way-hash functions differ
      from the above two forms of encryption in the sense that they are never meant to be decrypted. They generate a
      unique value of a fixed length for each input that shows no clear trend which can be exploited. This makes them
      practically impossible to reverse.

### How Does SSH Work With These Encryption Techniques

The way SSH works is by making use of a client-server model to allow for authentication of two remote systems and
encryption of the data that passes between them.

### Conclusion

1. Gaining an in-depth understanding of the underlying how SSH works can help users
   understand the security aspects of this technology.
2. Most people consider this process to be extremely complex and un-understandable,
   but it is much simpler than most people think.
3. If you’re wondering how long it takes for a computer to calculate a hash and authenticate a user, well, it happens in
   less than a second. In fact, the maximum amount of time is spent in transferring data across the Internet.

---

## Resources

### [Django Settings: Best practices](https://djangostars.com/blog/configuring-django-settings-best-practices/)

### [SSH](https://www.hostinger.com/tutorials/ssh-tutorial-how-does-ssh-work)

### [whitenoise](http://whitenoise.evans.io/en/stable/)

### [Infrastructure as a service](https://en.wikipedia.org/wiki/Infrastructure_as_a_service)

### [Platform as a service](https://en.wikipedia.org/wiki/Platform_as_a_service)

### [Cross-origin resource sharing](https://en.m.wikipedia.org/wiki/Cross-origin_resource_sharing)

---
