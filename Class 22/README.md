# Class 22

Live link: [Django Custom User Model](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2022/)

## Custom User Model

Django ships with a built-in User model for authentication
However, for a real-world project, the official Django documentation highly
recommends using a custom user model instead. This provides far more flexibility
down the line so, as a general rule, always use a custom user model for all new Django
projects.

### Setup

To start, create a new Django project from the command line. We need to do several things:

* create and navigate into a dedicated directory called accounts for our code
* install Django
* make a new Django project called django_project
* make a new app accounts
* start the local web server

'''python
> python -m venv .venv
> .venv\Scripts\activate
> python -m pip install django
> django-admin startproject django_project .
> python manage.py startapp accounts
> python manage.py runserver
'''

Note that we did not run migrate to configure our database. It's important to wait
until after we've created our new custom user model before doing so.

### AbstractUser vs AbstractBaseUser

There are two modern ways to create a custom user model in Django: AbstractUser
and AbstractBaseUser. In both cases we can subclass them to extend existing functionality
however AbstractBaseUser requires much, much more work.
AbstractUser which actually subclasses AbstractBaseUser but provides more default
configuration.

### Custom User Model

Creating our initial custom user model requires four steps:

* update django_project/settings.py
* create a new CustomUser model
* create new UserCreation and UserChangeForm
* update the admin

In settings.py we'll add the accounts app and use the AUTH_USER_MODEL config to tell
Django to use our new custom user model in place of the built-in User model. We'll call our
custom user model CustomUser.

Within INSTALLED_APPS add accounts at the bottom. Then at the bottom of the entire file,
add the AUTH_USER_MODEL config.

## Conclusion

Now that our custom user model is configured you can easily and at any time add additional
fields to it.
You can also check out DjangoX, which is an open-source Django starter framework that
includes a custom user model, email/password by default instead of username/email/password,
social authentication, and more.

---

## Substituting a custom User model

Some kinds of projects may have authentication requirements for which Django’s built-in
User model is not always appropriate. For instance, on some sites it makes more sense to
use an email address as your identification token instead of a username.

Django allows you to override the default user model by providing a value for the
AUTH_USER_MODEL setting that references a custom model:
ex: AUTH_USER_MODEL = 'myapp.MyUser'

### Using a custom user model when starting a project

```python
from django.contrib.auth.models import AbstractUser


class User(AbstractUser):
    pass
```

Don’t forget to point AUTH_USER_MODEL to it. Do this before creating any migrations or
running manage.py migrate for the first time.

Also, register the model in the app’s admin.py:

```python
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```

---

### [django-custom-user-model](https://learndjango.com/tutorials/django-custom-user-model)

### [djangox](https://github.com/wsvincent/djangox)

### [Build a Custom User Model with Extended Fields](https://www.youtube.com/watch?v=Ae7nc1EGv-A&ab_channel=VeryAcademy)

---

## Notes

* **If you’re starting a new project, it’s highly recommended to set up a custom user model,
  even if the default User model is sufficient for you.**
* When you start your project with a custom user model, stop to consider if this is the right choice for your project.
  Keeping all user related information in one model removes the need for additional or more
  complex database queries to retrieve related models.

## Things I want to know more about

How to apply this knowledge in real project
