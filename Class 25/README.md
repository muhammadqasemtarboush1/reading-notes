# Class 25

Live link: [Permissions & Postgresql](https://muhammadqasemtarboush1.github.io/reading-notes/Class%2025/)

## Permissions

---
Permission checks are always run at the very start of the view, before any other code is allowed to proceed. Permission checks will typically use the authentication information in the request.user and request.auth properties to determine if the incoming request should be permitted.

#### Used Case
Permissions are used to grant or deny access for different classes of users to different parts of the API.

### How permissions are determined
Permissions in REST framework are always defined as a list of permission classes.

When the permission checks fail, either a "403 Forbidden" or a "401 Unauthorized" response will be returned, according to the following rules:
* The request was successfully authenticated, but permission was denied. — An HTTP 403 Forbidden response will be returned.
* The request was not successfully authenticated, and the highest priority authentication class does not use WWW-Authenticate headers. — An HTTP 403 Forbidden response will be returned.
* The request was not successfully authenticated, and the highest priority authentication class does use WWW-Authenticate headers. — An HTTP 401 Unauthorized response, with an appropriate WWW-Authenticate header will be returned.

### Object level permissions
REST framework permissions also support object-level permissioning. Object level permissions are used to determine if a user should be allowed to act on a particular object, which will typically be a model instance.

Object level permissions are run by REST framework's generic views when .get_object() is called. As with view level permissions, an exceptions.PermissionDenied exception will be raised if the user is not allowed to act on the given object.

### Setting the permission policy
The default permission policy may be set globally, using the DEFAULT_PERMISSION_CLASSES setting.

### API Reference:
* AllowAny:
  * The AllowAny permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.
  * This permission is not strictly required, since you can achieve the same result by using an empty list or tuple for the permissions setting, but you may find it useful to specify this class because it makes the intention explicit.
* IsAuthenticated:
  * The IsAuthenticated permission class will deny permission to any unauthenticated user, and allow permission otherwise. 
  * This permission is suitable if you want your API to only be accessible to registered users.
* IsAdminUser:
  * The IsAdminUser permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.
  * This permission is suitable if you want your API to only be accessible to a subset of trusted administrators.
* IsAuthenticatedOrReadOnly:
  * The IsAuthenticatedOrReadOnly will allow authenticated users to perform any request. Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; GET, HEAD or OPTIONS.
  * This permission is suitable if you want to your API to allow read permissions to anonymous users, and only allow write permissions to authenticated users.
* DjangoModelPermissions:
  * This permission class ties into Django's standard django.contrib.auth model permissions. This permission must only be applied to views that have a .queryset property or get_queryset() method. Authorization will only be granted if the user is authenticated and has the relevant model permissions assigned. for more details see the [Link](https://www.django-rest-framework.org/api-guide/permissions/#djangomodelpermissions)
* DjangoModelPermissionsOrAnonReadOnly:
  * Similar to DjangoModelPermissions, but also allows unauthenticated users to have read-only access to the API.
* DjangoObjectPermissions:
  * This permission class ties into Django's standard object permissions framework that allows per-object permissions on models. In order to use this permission class, you'll also need to add a permission backend that supports object-level permissions, such as django-guardian.

### Custom permissions:
To implement a custom permission, override BasePermission and implement either, or both, of the following methods:




## Notes
* With the exception of DjangoObjectPermissions, the provided permission classes in rest_framework.permissions do not implement the methods necessary to check object permissions.

* If you wish to use the provided permission classes in order to check object permissions, you must subclass them and implement the has_object_permission() method described in the Custom permissions section (below).

* when you set new permission classes via the class attribute or decorators you're telling the view to ignore the default list set in the settings.py file.

* If you need object level view permissions for GET, HEAD and OPTIONS requests and are using django-guardian for your object-level permissions backend, you'll want to consider using the DjangoObjectPermissionsFilter class provided by the djangorestframework-guardian package. It ensures that list endpoints only return results including objects for which the user has appropriate view permissions.

* The instance-level has_object_permission method will only be called if the view-level has_permission checks have already passed. Also note that in order for the instance-level checks to run, the view code should explicitly call .check_object_permissions(request, obj). If you are using the generic views then this will be handled for you by default. (Function-based views will need to check object permissions explicitly, raising PermissionDenied on failure.)



---
Resources:

## [Permissions](https://www.django-rest-framework.org/api-guide/permissions/)
## [SQL](https://codefellows.github.io/common_curriculum/prep_work/SQL)
## [Classy Django REST Framework.](https://www.cdrf.co/)
## [Generic View](https://www.django-rest-framework.org/api-guide/generic-views/)

---

