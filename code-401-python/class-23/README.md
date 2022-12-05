# Class-22
## Django Custom User
#### Custom User Model
- Django's built-in User model is good enough for many cases while also having a room for customization. Why would you need to tweak some of the functionalities of the default User model?

    - Maybe you want to make email field the primary unique identifier of users instead of username.
    - Maybe you want to include other unique fields for authentication like phone number.
    - Maybe you want to stack all user information, be it auth related or non-auth fields all in the User model.
- **Setup**
To start, create a new Django project from the command line. We need to do several things:

    - create and navigate into a dedicated directory called accounts for our code
    - install Django
    - make a new Django project called django_project
    - make a new app accounts
    - start the local web serve
- **AbstractUser vs AbstractBaseUser**
If you need full control over User model, it is better to use ```AbstractBaseUser``` but if you are just adding things to the existing user, for example, you just want to add an extra field bio ,location field or any other profile data then use ```AbstractUser```.
- **Custom User Model**
Creating our initial custom user model requires four steps:

    - update django_project/settings.py
    - create a new CustomUser model
    - create new UserCreation and UserChangeForm
    - update the admin
- **Superuser**
It's helpful to create a superuser that we can use to log in to the admin and test out log in/log out 
    ```python manage.py createsuperuser```

- Templates/Views/URLs
    1. Start by updating settings.py to use a project-level templates directory.
        ```python
        TEMPLATES = [
            {
                ...
                "DIRS": [BASE_DIR / "templates"],  # new
                ...
            },
        ]
        ``` 
    2. Set the redirect links for log in and log out, which will both go to our home template. Add these two lines at the bottom of the file.
        ```python
        # django_project/settings.py
        LOGIN_REDIRECT_URL = "home"
        LOGOUT_REDIRECT_URL = "home"
        ```
    3. Create a new project-level templates folder and within it a registration folder as that's where Django will look for the log in template.
        ```
        (.venv) > mkdir templates
        (.venv) > mkdir templates/registration
        ```
    4. Then create four templates
        ```
        (.venv) > touch templates/registration/login.html
        (.venv) > touch templates/registration/signup.html
        (.venv) > touch templates/base.html
        (.venv) > touch templates/home.html
        ```    
    5. Update the pervious templates.
    6. for urls.py files at the project and app level.
        ```python
        from django.contrib import admin
        from django.urls import path, include
        from django.views.generic.base import TemplateView

        urlpatterns = [
            path("", TemplateView.as_view(template_name="home.html"), name="home"),
            path("admin/", admin.site.urls),
            path("accounts/", include("accounts.urls")),
            path("accounts/", include("django.contrib.auth.urls")),
        ]
        ```
    7. Create a urls.py file in the accounts app.
        ```python
        # accounts/urls.py
        from django.urls import path

        from .views import SignUpView

        urlpatterns = [
            path("signup/", SignUpView.as_view(), name="signup"),
        ]
        ```
    8. Last step is views.py file in the accounts app which will contain signup form.
        ```python
        # accounts/views.py
        from django.urls import reverse_lazy
        from django.views.generic.edit import CreateView

        from .forms import CustomUserCreationForm

        class SignUpView(CreateView):
            form_class = CustomUserCreationForm
            success_url = reverse_lazy("login")
            template_name = "registration/signup.html"
        ```
![](https://learndjango.com/static/images/tutorials/custom_user_model/home_loggedout.png)

![](https://learndjango.com/static/images/tutorials/custom_user_model/login.png)

![](https://learndjango.com/static/images/tutorials/custom_user_model/signup.png)

![](https://learndjango.com/static/images/tutorials/custom_user_model/admin.png)