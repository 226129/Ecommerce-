# User Manual
This manual is made in order to follow step by step what to do in a specific situation regarding on the project and what the ecommerce expects to do. 

# Table of Contents 
- [User Manual](#user-manual)
- [Table of Contents](#table-of-contents)
- [Adding media files to the system](#adding-media-files-to-the-system)
- [Generate automatically a field regarding on another field](#generate-automatically-a-field-regarding-on-another-field)


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