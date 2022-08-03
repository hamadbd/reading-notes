# Django in Python

## Meet Django
Django is a high-level Python web framework that encourages rapid development and clean, pragmatic design. Built by experienced developers, it takes care of much of the hassle of web development, so you can focus on writing your app without needing to reinvent the wheel. It’s free and open source.

- Ridiculously fast.
Django was designed to help developers take applications from concept to completion as quickly as possible.
- Reassuringly secure.
Django takes security seriously and helps developers avoid many common security mistakes.
- Exceedingly scalable.
Some of the busiest sites on the web leverage Django’s ability to quickly and flexibly scale.

# Django Models 
A model is a class that represents table or collection in our DB, and where every attribute of the class is a field of the table or collection. Models are defined in the app/models.py (in our example: myapp/models.py)

## Creating a Model
Following is a Dreamreal model created as an example −
```
from django.db import models

class Dreamreal(models.Model):

   website = models.CharField(max_length = 50)
   mail = models.CharField(max_length = 50)
   name = models.CharField(max_length = 50)
   phonenumber = models.IntegerField()

   class Meta:
      db_table = "dreamreal"
```

Every model inherits from django.db.models.Model.

Our class has 4 attributes (3 CharField and 1 Integer), those will be the table fields.

The Meta class with the db_table attribute lets us define the actual table or collection name. Django names the table or collection automatically: myapp_modelName. This class will let you force the name of the table to what you like.

After creating your model, you will need Django to generate the actual database −
```
$python manage.py syncdb
```

# Manipulating Data (CRUD)
Let's create a "crudops" view to see how we can do CRUD operations on models. Our myapp/views.py will then look like −

myapp/views.py
```
from myapp.models import Dreamreal
from django.http import HttpResponse

def crudops(request):
   #Creating an entry
   
   dreamreal = Dreamreal(
      website = "www.polo.com", mail = "sorex@polo.com", 
      name = "sorex", phonenumber = "002376970"
   )
   
   dreamreal.save()
   
   #Read ALL entries
   objects = Dreamreal.objects.all()
   res ='Printing all Dreamreal entries in the DB : <br>'
   
   for elt in objects:
      res += elt.name+"<br>"
   
   #Read a specific entry:
   sorex = Dreamreal.objects.get(name = "sorex")
   res += 'Printing One entry <br>'
   res += sorex.name
   
   #Delete an entry
   res += '<br> Deleting an entry <br>'
   sorex.delete()
   
   #Update
   dreamreal = Dreamreal(
      website = "www.polo.com", mail = "sorex@polo.com", 
      name = "sorex", phonenumber = "002376970"
   )
   
   dreamreal.save()
   res += 'Updating entry<br>'
   
   dreamreal = Dreamreal.objects.get(name = 'sorex')
   dreamreal.name = 'thierry'
   dreamreal.save()
   
   return HttpResponse(res)
```
# Other Data Manipulation

Let's explore other manipulations we can do on Models. Note that the CRUD operations were done on instances of our model, now we will be working directly with the class representing our model.

Let's create a 'datamanipulation' view in myapp/views.py
```
from myapp.models import Dreamreal
from django.http import HttpResponse

def datamanipulation(request):
   res = ''
   
   #Filtering data:
   qs = Dreamreal.objects.filter(name = "paul")
   res += "Found : %s results<br>"%len(qs)
   
   #Ordering results
   qs = Dreamreal.objects.order_by("name")
   
   for elt in qs:
      res += elt.name + '<br>'
   
   return HttpResponse(res)
```
# Linking Models
Django ORM offers 3 ways to link models −

One of the first case we will see here is the one-to-many relationships. As you can see in the above example, Dreamreal company can have multiple online websites. Defining that relation is done by using django.db.models.ForeignKey −

myapp/models.py
```
from django.db import models

class Dreamreal(models.Model):
   website = models.CharField(max_length = 50)
   mail = models.CharField(max_length = 50)
   name = models.CharField(max_length = 50)
   phonenumber = models.IntegerField()
   online = models.ForeignKey('Online', default = 1)
   
   class Meta:
      db_table = "dreamreal"

class Online(models.Model):
      domain = models.CharField(max_length = 30)
   
   class Meta:
      db_table = "online"
```
As you can see in our updated myapp/models.py, we added the online model and linked it to our Dreamreal model.

Let's check how all of this is working via manage.py shell −

First let’s create some companies (Dreamreal entries) for testing in our Django shell −

```
$python manage.py shell

>>> from myapp.models import Dreamreal, Online
>>> dr1 = Dreamreal()
>>> dr1.website = 'company1.com'
>>> dr1.name = 'company1'
>>> dr1.mail = 'contact@company1'
>>> dr1.phonenumber = '12345'
>>> dr1.save()
>>> dr2 = Dreamreal()
>>> dr1.website = 'company2.com'
>>> dr2.website = 'company2.com'
>>> dr2.name = 'company2'
>>> dr2.mail = 'contact@company2'
>>> dr2.phonenumber = '56789'
>>> dr2.save()
```
Now some hosted domains −

```
>>> on1 = Online()
>>> on1.company = dr1
>>> on1.domain = "site1.com"
>>> on2 = Online()
>>> on2.company = dr1
>>> on2.domain = "site2.com"
>>> on3 = Online()
>>> on3.domain = "site3.com"
>>> dr2 = Dreamreal.objects.all()[2]
>>> on3.company = dr2
>>> on1.save()
>>> on2.save()
>>> on3.save()
```
Accessing attribute of the hosting company (Dreamreal entry) from an online domain is simple −
```
>>> on1.company.name
```

And if we want to know all the online domain hosted by a Company in Dreamreal we will use the code −
```
>>> dr1.online_set.all()
```
To get a QuerySet, note that all manipulating method we have seen before (filter, all, exclude, order_by....)

You can also access the linked model attributes for filtering operations, let's say you want to get all online domains where the Dreamreal name contains 'company' −

```
>>> Online.objects.filter(company__name__contains = 'company'
```

# Custom User Model in Django
## Step 1: Set up a Django project.
1) Create a python virtual environment and activate it.

2) Install Django and Django rest framework.
```
pip install django djangorestframework
```
3) Start a new project:
```
django-admin startproject config .
```
4) Run the following command to see if the installation is correct.
```
py manage.py runserver
```
Now, create a new app users and add it to installed apps.
```
py manage.py startapp users
```
settings.py
```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',

    # Third-party apps
    'rest_framework',

    # Local apps
    'users',
]
```
When you have projects that require a different authentication that the built-in User model can’t provide, you have to create your own custom User model by extending from either AbstractUser or AbstractBaseUser Now, the question is which one should you extend from?

- AbstractUser : Are you satisfied with the existing fields in the built-in User model but you want to use email as the primary unique identifier of your users or perhaps remove the username field? If yes, AbstractUser is the right option for you.
- AbstractBaseUser : There are two things to consider whenever starting a new project :
User model focused on authentication, and another model like Profile that keeps app-related information of the user. Here you may use AbstractBaseUser if you have additional auth-related attributes that you want to include in your User model.
User model that stores all information (auth related or non-auth attributes) all in one. You may want to do this to avoid using additional database queries to retrieve related model. If you want to take this approach, AbstractBaseUser is the right option.

```
from django.contrib.auth.models import AbstractUser


class User(AbstractUser):
    pass
```
For the purpose of this article, we are going to use AbstractUser but the steps for AbstractBaseUser are also similar.

## Step 2: Custom Model Manager
Manager is a class that provides an interface through which database query operations are provided to Django models. You can have more than one manager for your model.

Consider this model:
```
from django.db import models

class Car(models.Model):
    pass
```
To get all instances of Car, you will use Car.objects.all()
objects is the default name that Django managers use. To change this name:
```
from django.db import models

class Car(models.Model):
    cars = models.Manager();
```
Now, to get all instances of car, you should use Car.cars.all().

For our custom user model, we need to define a custom manager class because we are going to modify the initial Queryset that the default Manager class returns. We do this by extending from BaseUserManager and providing two additional methods create_user and create_superuser.

Create a file named managers.py inside users app and put the following.
managers.py
```
from django.contrib.auth.base_user import BaseUserManager
from django.utils.translation import gettext as _

class CustomUserManager(BaseUserManager):
    """
    Custom user model manager where email is the unique identifier
    for authentication instead of usernames.
    """

    def create_user(self, email, password, **extra_fields):
        if not email:
            raise ValueError(_('Users must have an email address'))
        email = self.normalize_email(email)
        user = self.model(email=email, **extra_fields)
        user.set_password(password)
        user.save()
        return user

    def create_superuser(self, email, password, **extra_fields):
        extra_fields.setdefault('is_staff', True)
        extra_fields.setdefault('is_superuser', True)
        extra_fields.setdefault('is_active', True)

        if extra_fields.get('is_staff') is not True:
            raise ValueError(_('Superuser must have is_staff=True.'))
        if extra_fields.get('is_superuser') is not True:
            raise ValueError(_('Superuser must have is_superuser=True.'))
        return self.create_user(email, password, **extra_fields)
```
## Step 3: The User Model
models.py
```
from django.contrib.auth.models import AbstractUser
from django.db import models
from django.utils.translation import gettext as _

from .managers import CustomUserManager

class CustomUser(AbstractUser):
    email = models.EmailField(_('email address'), unique=True)

    USERNAME_FIELD = 'email'
    REQUIRED_FIELDS = ('username',)

    objects = CustomUserManager()

    def __str__(self):
        return self.email
```
- USERNAME_FIELD specifies the name of the field on the user model that is used as the unique identifier. In our case it’s email.
- REQUIRED_FIELDS A list of the field names that will be prompted for when creating a superuser via the createsuperuser management command. This doesn’t have any effect in other parts of Django like when creating a user in the admin panel.

## Step 4: The Settings
We now have to tell Django our new model that should be used to represent a User. This is done as follows.

settings.py
```
AUTH_USER_MODEL = 'users.CustomUser'
```
→ You can now create and apply migrations.
```
py manage.py makemigrations
py manage.py migrate
```
## Step 5: Forms
Django’s built-in UserCreationForm and UserChangeForm forms must be extended to let them know the new user model that we are working with.

Create a file named forms.py inside users app and add the following:

forms.py
```
from django.contrib.auth.forms import UserCreationForm, UserChangeForm

from .models import CustomUser

class CustomUserCreationForm(UserCreationForm):

    class Meta:
        model = CustomUser
        fields = ('email',)

class CustomUserChangeForm(UserChangeForm):

    class Meta:
        model = CustomUser
        fields = ('email',)
```

## Step 6: Admin
Tell the admin panel to use these forms by extending from UserAdmin in users/admin.py

admin.py
```
from django.contrib import admin
from django.contrib.auth.admin import UserAdmin

from .forms import CustomUserCreationForm, CustomUserChangeForm
from .models import CustomUser

class CustomUserAdmin(UserAdmin):
    add_form = CustomUserCreationForm
    form = CustomUserChangeForm

    model = CustomUser

    list_display = ('username', 'email', 'is_active',
                    'is_staff', 'is_superuser', 'last_login',)
    list_filter = ('is_active', 'is_staff', 'is_superuser')
    fieldsets = (
        (None, {'fields': ('username', 'email', 'password')}),
        ('Permissions', {'fields': ('is_staff', 'is_active',
         'is_superuser', 'groups', 'user_permissions')}),
        ('Dates', {'fields': ('last_login', 'date_joined')})
    )
    add_fieldsets = (
        (None, {
            'classes': ('wide',),
            'fields': ('username', 'email', 'password1', 'password2', 'is_staff', 'is_active')}
         ),
    )
    search_fields = ('email',)
    ordering = ('email',)

admin.site.register(CustomUser, CustomUserAdmin)
```
- add_form and form specifies the forms to add and change user instances.
- fieldsets specifies the fields to be used in editing users and add_fieldsets specifies fields to be used when creating a user.

