# Class-20
## Django Models
### Using Models
###### Designing the LocalLibrary models
- Once we've decided on our models and field, we need to think about the relationships. Django allows you to define relationships that are one to one (OneToOneField), one to many (ForeignKey) and many to many (ManyToManyField).
- **Model primer**
    - Models are usually defined in an application's models.py file. They are implemented as subclasses of django.db.models.Model, and can include fields, methods and metadata.
    - **Fields**
        A model can have an arbitrary number of fields, of any type — each one represents a column of data that we want to store in one of our database tables. Each database record (row) will consist of one of each field value.

| COMMON FIELD ARGUMENTS | COMMON FIELD TYPES |
|-----------------|-----------|
| help_text | CharField |
| verbose_name | TextField | 
| default | IntegerField| 
| null | DateField and DateTimeField |
| blank | EmailField | 
| choices |  AutoField  | 
| primary_key |  ForeignKey  | 
| - |  ManyToManyField  | 

- **Metadata**
    - One of the most useful features of this metadata is to control the default ordering of records returned when you query the model type. You do this by specifying the match order in a list of field names to the ordering attribute.
    ```python
    class Meta:
    ordering = ['-my_field_name']
    ```
    - Other useful attributes allow you to create and apply new "access permissions" for the model (default permissions are applied automatically), allow ordering based on another field, or to declare that the class is "abstract" (a base class that you cannot create records for, and will instead be derived from to create other models).
- **Methods**
    ```python
    '''Returns a human-readable string for each object'''
    def __str__(self):
    return self.field_name


    def get_absolute_url(self):
    """Returns the URL to access a particular instance of the model."""
    return reverse('model-detail-view', args=[str(self.id)])
    ```
- **Model management**
    - To create a record you can define an instance of the model and then call ```save()```
    - You can search for records that match certain criteria using the model's ```objects``` attribute.
    - We can get all records for a model as a QuerySet, using ```objects.all()```
    - ```filter()``` method allows us to filter the returned QuerySet to match a specified text or numeric field against particular criteria.
----------------------
###### Django admin site
- **The Django admin** application can use your models to automatically build a site area that you can use to create, view, update, and delete records. This can save you a lot of time during development, making it very easy to test your models and get a feel for whether you have the right data.
- **Registering models**
    ```python
    from django.contrib import admin
    # Register your models here.
    ```
    - This code imports the models and then calls admin.site.register to register each of them.
- **Creating a superuser**
    ```python3 manage.py createsuperuser```
- **Advanced configuration**
- Django does a pretty good job of creating a basic admin site using the information from the registered models:

- Each model has a list of individual records, identified by the string created with the model's __str__() method, and linked to detail views/forms for editing. 
- The model detail record forms for editing and adding records contain all the fields in the model, laid out vertically in their declaration order.

- You can further customize the interface to make it even easier to use. Some of the things you can do are:

    - List views:
        - Add additional fields/information displayed for each record.
        - Add filters to select which records are listed, based on date or some other selection value.
        - Add additional options to the actions menu in list views and choose where this menu is displayed on the form.
    - Detail views
        - Choose which fields to display (or exclude), along with their order, grouping, whether they are editable, the widget used, orientation etc.
    - Add related fields to a record to allow inline editing .