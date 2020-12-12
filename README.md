# DJango App - Pets Vaccination App

#### Create Django Project Directory
```
django-admin startproject wisdompets
```
<table>
<tr><th>File</th><th> Description </th></tr>
<tr><td>manage.py</td><td> Runs commands</td></tr>
<tr><td>__init__.py</td><td> Tells Python that folder contains Python Code</td></tr>
<tr><td>wsgi.py</td><td> Provides hooks for Server when running Live</td></tr>
<tr><td>settings.py</td><td> Configures Django project</td></tr>
<tr><td>urls.py</td><td> Routes web requests based on URL</td></tr>
</table>

#### To Run the app
```
python manage.py runserver
```

#### Creating Adoptions app

```
python manage.py startapp adoptions
```

Add **'adoptions'** in **INSTALLED_APPS** in **wisdompets/settings.py** file

Files/Folders in adoptions app:

<table>
<tr><th>File</th><th> Description </th></tr>
<tr><td>apps.py </td><td> settings specific to the app</td></tr>
<tr><td>models.py </td><td> provides data layer to construct database schema and queries</td></tr>
<tr><td>admin.py </td><td> defines adminstrative interface </td></tr>
<tr><td>urls.py </td><td> url routing</td></tr>
<tr><td>views.py </td><td> logic and control flow for handling Requests and defines HTTP responses </td></tr>
<tr><td>tests.py </td><td> Writing unit tests for functionality of this app</td></tr>
<tr><td>migrations </td><td> Migrate files </td></tr>
</table>


A **Model** is class inherting from **django.db.models.Model** and it defines database fields as class attributes


Models Defines the structure of the database and 
Migrations Generate Scripts to Change the Database Structure

**Migrations** are required when:
- Adding a Model
- Adding or Changing or Removing a Field

#### Migrations related Commands:
```
python manage.py makemigrations
python manage.py showmigrations
python manage.py migrate
```

makemigrations Compares the Current Model and current Database to a generate migration file
in <APPNAME>/migrations/

Can also run specific migration using:
```
python manage.py migrate <appname> <number>
```

Importing some dummy data from pet_data.csv to make use in views

Code for same in adoptions/management/commands/load_pet_data.py

CMD: ```python manage.py load_pet_data```

One can use Shell to play with ORM or view data:
```python manage.py shell```

#### Create a Admin User
```
python manage.py createsuperuser
```

Making Change in models for better representation of vaccine in pet data view.

And adding **'list_display'** for more details on Pets View.

Adding URL:
Add in **urlpatterns** in **app/urls.py**
Then add view logic in function in **app_name/views.py**

path function: ```path(url/<converter>, view_funtion, name)```
name is later used in template {% url 'name' <id> %}

#### Django template:
```
{{ variable }}
{% control_logic %}
```

Also piping can be used to display in some Format
```{{ variable | Format }}```

Examples:
* {% extends "base.html" %}
* <a href='{% url 'pet_detail' pet.id %}'></a>


In template omit parenthesis if no argument in function.


Add/Store CSS, Images and JS files in Static folder in project directory.

Example Usecase:
```
<img src="{% static 'images/header.jpg' %}" >

<link rel="stylesheet" href="{% static 'style.css' %}">

<script src="{% static 'main.js' %}"></script>
```

