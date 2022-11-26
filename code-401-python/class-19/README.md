# Class-19
## Intro to Django
### Reading
##### Getting started with Django
- **Django** is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.
![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRlHpEsRq4pIo4vTLAn24qGNwG41dFdXLJwsQ&usqp=CAU)
- Object-relational mapper
```python
from django.db import models

class Band(models.Model):
    """A model of a rock band."""
    name = models.CharField(max_length=200)
    can_rock = models.BooleanField(default=True)

class Member(models.Model):
    """A model of a rock band member."""
    name = models.CharField("Member's name", max_length=200)
    instrument = models.CharField(choices=(
            ('g', "Guitar"),
            ('b', "Bass"),
            ('d', "Drums"),
        ),
        max_length=1
    )
    band = models.ForeignKey("Band")
```
- URLs and views
    To design URLs for an application, you create a Python module called a **URLconf**. Like a table of contents for your app, it contains a simple mapping between URL patterns and your views.
```python
from django.urls import path

from . import views

urlpatterns = [
    path('bands/', views.band_listing, name='band-list'),
    path('bands/<int:band_id>/', views.band_detail, name='band-detail'),
    path('bands/search/', views.band_search, name='band-search'),
]
```
```python
from django.shortcuts import render
from bands.models import Band

def band_listing(request):
    """A view of all bands."""
    bands = Band.objects.all()
    return render(request, 'bands/band_listing.html', {'bands': bands})
```
- Templates
    Django’s template language is designed to strike a balance between power and ease. It’s designed to feel comfortable and easy-to-learn to those used to working with HTML, like designers and front-end developers. But it is also flexible and highly extensible, allowing developers to augment the template language as needed.
```html
<html>
  <head>
    <title>Band Listing</title>
  </head>
  <body>
    <h1>All Bands</h1>
    <ul>
    {% for band in bands %}
      <li>
        <h2><a href="{{ band.get_absolute_url }}">{{ band.name }}</a></h2>
        {% if band.can_rock %}<p>This band can rock!</p>{% endif %}
      </li>
    {% endfor %}
    </ul>
  </body>
</html>
```
- Forms
    Django provides a powerful form library that handles rendering forms as HTML, validating user-submitted data, and converting that data to native Python types. Django also provides a way to generate forms from your existing models and use those forms to create and update data.
```python
from django import forms

class BandContactForm(forms.Form):
    subject = forms.CharField(max_length=100)
    message = forms.CharField()
    sender = forms.EmailField()
    cc_myself = forms.BooleanField(required=False)
```
- Authentication
    Django comes with a full-featured and secure authentication system. It handles user accounts, groups, permissions and cookie-based user sessions. This lets you easily build sites that allow users to create accounts and safely log in/out.
- Admin
    One of the most powerful parts of Django is its automatic admin interface. It reads metadata in your models to provide a powerful and production-ready interface that content producers can immediately use to start managing content on your site. It’s easy to set up and provides many hooks for customization.
-Internationalization
    Django offers full support for translating text into different languages, plus locale-specific formatting of dates, times, numbers, and time zones. It lets developers and template authors specify which parts of their apps should be translated or formatted for local languages and cultures, and it uses these hooks to localize web applications for particular users according to their preferences.
```python
from django.shortcuts import render
from django.utils.translation import gettext

def homepage(request):
    """
    Shows the homepage with a welcome message that is translated in the
    user's language.
    """
    message = gettext('Welcome to our site!')
    return render(request, 'homepage.html', {'message': message})
```

- Security
    Django provides multiple protections against:
    - Clickjacking
    - Cross-site scripting
    - Cross Site Request Forgery (CSRF)
    - SQL injection
    - Remote code execution
