# Class-26
## DRF Permissions
##### Django REST framework Permissions

![](https://learnbatta.com/assets/images/django/permissions-in-Django-Rest-Framework.png)

- Together with `authentication` and `throttling`, **permissions** determine whether a request should be granted or denied access.
- Permission checks are always run at the very start of the view, before any other code is allowed to proceed. Permission checks will typically use the authentication information in the `request.user` and `request.auth` properties to determine if the incoming request should be permitted.
- **How permissions are determined?** 
    - Before running the main body of the view each permission in the list is checked. If any permission check fails, an `exceptions.PermissionDenied`or `exceptions.NotAuthenticated` exception will be raised, and the main body of the view will not run.
- **Object level permissions**
    - Object level permissions are run by REST framework's generic views when `.get_object()` is called. As with view level permissions, an `exceptions.PermissionDenied` exception will be raised if the user is not allowed to act on the given object.
    ```python
    def get_object(self):
    obj = get_object_or_404(self.get_queryset(), pk=self.kwargs["pk"])
    self.check_object_permissions(self.request, obj)
    return obj
    ```
##### API Reference
- **AllowAny**
    The `AllowAny` permission class will allow unrestricted access, regardless of if the request was authenticated or unauthenticated.
- **IsAuthenticated**
    The `IsAuthenticated` permission class will deny permission to any unauthenticated user, and allow permission otherwise.
- **IsAdminUser**
    The `IsAdminUser` permission class will deny permission to any user, unless user.is_staff is True in which case permission will be allowed.
- **IsAuthenticatedOrReadOnly**
    The `IsAuthenticatedOrReadOnly` will allow authenticated users to perform any request. Requests for unauthorised users will only be permitted if the request method is one of the "safe" methods; `GET`, `HEAD` or `OPTIONS`.
- **DjangoModelPermissions**
    This permission must only be applied to views that have a `.queryset` property or `get_queryset()` method.
##### Custom permissions
- To implement a custom permission, override `BasePermission` and implement either, or both, of the following methods:
```python
.has_permission(self, request, view)
.has_object_permission(self, request, view, obj)
```
- The methods should return True if the request should be granted access, and False otherwise.

##### Third party packages
- **DRF - Access Policy**
    The Django `REST - Access Policy` package provides a way to define complex access rules in declarative policy classes that are attached to view sets or function-based views. The policies are defined in JSON in a format similar to AWS' Identity & Access Management policies.
- **Composed Permissions**
    The `Composed Permissions` package provides a simple way to define complex and multi-depth (with logic operators) permission objects, using small and reusable components.
- **REST Condition**
    The `REST Condition` package is another extension for building complex permissions in a simple and convenient way. The extension allows you to combine permissions with logical operators.
- **Django Rest Framework Roles**
    The `Django Rest Framework Roles` package makes it easier to parameterize your API over multiple types of users.
- **Django REST Framework API Key**
    The `Django REST Framework API Key` package provides permissions classes, models and helpers to add API key authorization to your API. 
