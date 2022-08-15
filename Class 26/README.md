# Class 26

Live link: [Authentication & Production Server](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2026/)

## Introduction to JSON Web Tokens

---

### What is JSON Web Token?

(JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for
securely transmitting information between parties as a JSON object.

This information can be verified and trusted because it is digitally signed.

JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.
Although JWTs can be encrypted to also provide secrecy between parties, we will focus on
signed tokens.

Signed tokens can verify the integrity of the claims contained within it,
while encrypted tokens hide those claims from other parties.

When tokens are signed using public/private key pairs, the signature also certifies that only the party holding the
private key is the one that signed it.

### When should you use JSON Web Tokens?

* Authorization: This is the most common scenario for using JWT.
* Information Exchange: JSON Web Tokens are a good way of securely transmitting information between parties.

### What is the JSON Web Token structure?

* Header:
  * The header typically consists of two parts: the type of the token, which is JWT,
      and the signing algorithm being used, such as HMAC SHA256 or RSA.
* Payload:
  * The second part of the token is the payload, which contains the claims.
      Claims are statements about an entity (typically, the user) and additional data.
      There are three types of claims: registered, public, and private claims.(check notes to know more).
* Signature:
  * To create the signature part you have to take the encoded header, the encoded payload,
      a secret, the algorithm specified in the header, and sign that.

Putting all together
The output is three Base64-URL strings separated by dots that can be easily passed in HTML
and HTTP environments, while being more compact when compared to XML-based standards such
as SAML.

### Why should we use JSON Web Tokens?

* As JSON is less verbose than XML, when it is encoded its size is also smaller,
  making JWT more compact than SAML. This makes JWT a good choice to be passed in HTML and HTTP environments.
* Security-wise, SWT can only be symmetrically signed by a shared secret using the HMAC
  algorithm. However, JWT and SAML tokens can use a public/private key pair in the form of
  a X.509 certificate for signing. Signing XML with XML Digital Signature without introducing
  obscure security holes is very difficult when compared to the simplicity of signing JSON.
* JSON parsers are common in most programming languages because they map directly to objects.
  Conversely, XML doesn't have a natural document-to-object mapping. This makes it easier
  to work with JWT than SAML assertions.
* Regarding usage, JWT is used at Internet scale. This highlights the ease of client-side
  processing of the JSON Web token on multiple platforms, especially mobile.

## Notes

* Registered claims: These are a set of predefined claims which are not mandatory but recommended, to provide a set of
  useful, interoperable claims.
* Public claims: These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the
  IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.
* Private claims: These are the custom claims created to share information between parties that agree on using them and
  are neither registered or public claims.
* JWT :JSON Web Tokens
* SWT:  Simple Web Tokens
* SAML:  Security Assertion Markup Language Tokens

---

## How to Use JWT Authentication with Django REST Framework

### How JWT Works?

The JWT is just an authorization token that should be included in all requests

The JWT is acquired by exchanging an username + password for an access token and an refresh token.
It’s a security feature and also it’s because the JWT holds a little bit more information.

### Installation & Setup

* pip install djangorestframework_simplejwt
  * settings.py
    *
    * ```python
      REST_FRAMEWORK = {
      'DEFAULT_AUTHENTICATION_CLASSES': [
          'rest_framework_simplejwt.authentication.JWTAuthentication',
      ]}```
      ]}
  * urls.py:
    * path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
    * path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),

### Obtain Token

> First step is to authenticate and obtain the token.

> After that you are going to store both the access token and the refresh token on the client side, usually in the
> localStorage.

> In order to access the protected views on the backend (i.e., the API endpoints that require authentication), you
> should include the access token in the header of all requests

> You can use this access token for the next five minutes.

> After five min, the token will expire, and if you try to access the view again, you are going to get an error.

> To get a new access token, you should use the refresh token endpoint /api/token/refresh/ posting the refresh token.

> The return is a new access token that you should use in the subsequent requests.

### What’s The Point of The Refresh Token?

At first glance the refresh token may look pointless, but in fact it is necessary to make
sure the user still have the correct permissions.

If your access token have a long expire
time, it may take longer to update the information associated with the token.

That’s because the authentication check is done by cryptographic means, instead of querying the
database and verifying the data. So some information is sort of cached.

There is also a security aspect, in a sense that the refresh token only travel in the POST
data. And the access token is sent via HTTP header, which may be logged along the way.

So this also give a short window, should your access token be compromised.

## Notes

* access token:  usually short-lived (expires in 5 min or so, can be customized though).
* refresh token : lives a little bit longer (expires in 24 hours, also customizable). It is comparable to an
  authentication session.

---

## Django Runserver Is Not Your Production Server

### intro

You’ve been running your app locally with python manage.py runserver. That’s a fine command, built for development
convenience, but it’s not meant to be used as part of a production setup.

**DO NOT USE THIS SERVER IN A PRODUCTION SETTING. It has not gone through security audits or performance tests.**_

So the server started with runserver is not guaranteed to be performant (it’s very slow), and it hasn’t been built with
security concerns in mind. Not a good fit for production use.

i### The Conclusion

If you want to run Django in production, be sure to use a production-ready web server like Nginx, and let your app be
handled by a WSGI application server like Gunicorn.

If you plan on running on Heroku, a web server is provided implicitly. You don’t have to take care of it. You just need
to specify a command to run your application server (again, Gunicorn is fine) in the Procfile.

---

## Resources

### [JWT](https://jwt.io/introduction/)

### [JWT Authentication with Django REST Framework](https://simpleisbetterthancomplex.com/tutorial/2018/12/19/how-to-use-jwt-authentication-with-django-rest-framework.html)

### [Django Runserver Is Not Your Production Server](https://vsupalov.com/django-runserver-in-production/)

---
