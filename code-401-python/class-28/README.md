# Class-28
## Authentication & Production Server
#### JSON Web Tokens
- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
- When tokens are signed using `public/private` key pairs, the signature also certifies that only the party holding the private key is the one that signed it.
- **When should you use JSON Web Tokens?** 
    - Authorization 
    - Information Exchange
- **What is the JSON Web Token structure?**
    - `Header`: consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.
    - `Payload`: contains the claims. `Claims` are statements about an entity (typically, the user) and additional data. There are three types of claims: **registered, public, and private claims**.
    - `Signature`: is used to verify the message wasn't changed along the way, and, in the case of tokens signed with a private key, it can also verify that the sender of the JWT is who it says it is.
    - `header.payload.signature`
- **How do JSON Web Tokens work?**
    In authentication, when the user *successfully* logs in using their credentials, a JSON Web Token will be **returned**. Since tokens are credentials, great care must be taken to prevent security issues. In general, **you should not keep tokens longer than required.**
- **how a JWT is obtained and used to access APIs or resources?**   
![](https://cdn2.auth0.com/docs/media/articles/api-auth/client-credentials-grant.png)
1. The application or client requests authorization to the authorization server. This is performed through one of the different authorization flows. For example, a typical OpenID Connect compliant web application will go through the /oauth/authorize endpoint using the authorization code flow.
2. When the authorization is granted, the authorization server returns an access token to the application.
3. The application uses the access token to access a protected resource (like an API).

#### DRF JWT Authentication
- use the `djangorestframework_simplejwt` library
- **settings.py**
    ```python
    REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ],
    }
    ```
- **urls.py**
    ```python
    from django.urls import path
    from rest_framework_simplejwt import views as jwt_views

    urlpatterns = [
        # Your URLs...
        path('api/token/', jwt_views.TokenObtainPairView.as_view(), name='token_obtain_pair'),
        path('api/token/refresh/', jwt_views.TokenRefreshView.as_view(), name='token_refresh'),
    ]
    ```
- **Usage**
- Obtain Token:
    - authenticate and obtain the token. The endpoint is `/api/token/` and it only accepts `POST` requests.
    - store both the access token and the refresh token on the client side, usually in the `localStorage`.
    - In order to access the protected views on the backend you should include the access token in the header of all requests
- Refresh Token:
    - use the refresh token endpoint /`api/token/refresh/` posting the refresh token.
    - The `refresh token` is valid for the next *24 hours*. When it finally expires too, the user will need to perform a full authentication again using their username and password to get a new set of *`access token + refresh token`*.
- **What’s The Point of The Refresh Token?**
1. to make sure the user still have the correct permissions.
2. the refresh token only travel in the POST data. And the access token is sent via HTTP header, which may be logged along the way. So this also give a short window, should access token be compromised.
#### Django Runserver Is Not Your Production Server
- **Production Stack**
- A production setup usually consists of multiple components, each designed and built to be really good at one specific thing. They are *fast*, *reliable* and *very focused*.
- **Nginx**
    - it is great at serving static files from disk and handling multiple requests at once. 
    - If the request is not for a static file, but should be processed by application, the webserver is configured to pass this request to the next component.
- **application server**
    - passes "dynamic" requests between your Django website and the webserver.
- **How Does Django Fit In?** 
    - Django project provides a ``uwsgi.py`` file, which contains a function to be called by the application server. This function gets a Python object representing the incoming request.
