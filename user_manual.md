# User Manual
This manual is made in order to follow step by step what to do in a specific situation regarding on the project and what the ecommerce expects to do. 

# Table of Contents 
- [User Manual](#user-manual)
- [Table of Contents](#table-of-contents)
- [Starting a new app](#starting-a-new-app)
- [Generating a new model](#generating-a-new-model)
- [Adding media files to the system](#adding-media-files-to-the-system)
- [Generate automatically a field regarding on another field](#generate-automatically-a-field-regarding-on-another-field)

# Starting a new app 
1. Go to the shell and type the following command 
```bash
    python manage.py startapp app_name
```
2. Once created go to the settings.py file of the root directory. 
3. Once there add a new app into the INSTALLED_APPS list and add the app. 
```python   
    INSTALLED_APPS = [
    'appname.apps.AppnameConfig',
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```
1. It must follow the pattern app name + .apps + .app name in upercase + Config concatenated to the app name. 

# Generating a new model 
1. Navigate to the model's file in the app desired 
2. Configure the class with the parameters that you want the class to have. 
```python
class Product(models.Model):
    product_name = models.CharField(max_length=200, unique=True)
    slug = models.CharField(max_length=200, unique=True)
    description = models.TextField(max_length=500, blank=True)
    price = models.FloatField()
    images = models.ImageField(upload_to='photos/products')
    stock = models.IntegerField()
    is_available = models.BooleanField(default=True)
    category = models.ForeignKey(Category, on_delete=models.CASCADE)
    create_date = models.DateTimeField(auto_now_add=True)
    modified_date = models.DateTimeField(auto_now=True)
```
3. Then update the str method in order to display a field in the admin site 
```python
def __str__(self):
    return self.product_name
```

# Adding media files to the system 
1. Configure the media in setting.py

```python 
    MEDIA_URL = '/media/'
    MEDIA_ROOT = BASE_DIR / 'media'
```
2. Go to urls.py and import these two modules
```python
    from django.conf.urls.static import static
    from django.conf import settings
```
3. Once imported, we have to concatenate the correct media to the urlpattern in the root urls.py
```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.home, name='home'),
] + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

# Generate automatically a field regarding on another field
1. Navigate to the admin that holds the model that you want to modify with this info 
2. Generate an admin class of the model
```python
    class CategoryAdmin(admin.ModelAdmin):
        pass
```
3. Then pass the following elements to the class. Change the fields if needed.
```python 
    prepopulated_fields = {'slug': ('category_name',)}
    list_display = ('category_name', 'slug')
``` 