# djangogirls-tutorial

For this tutorial we will be using a new directory djangogirls from your home directory:

command-line
$ mkdir djangogirls
$ cd djangogirls

We will make a virtualenv called myvenv. The general command will be in the format:
We can create a virtualenv on both Linux and OS X by running python3 -m venv myvenv. It will look like this:

command-line
$ python3 -m venv myvenv

Start your virtual environment by running:

command-line
$ source myvenv/bin/activate
Remember to replace myvenv with your chosen virtualenv name!

You will know that you have virtualenv started when you see that the prompt in your console is prefixed with (myvenv).

command-line
(myvenv) ~$ python -m pip install --upgrade pip

A requirements file keeps a list of dependencies to be installed using pip install:

First create a requirements.txt file inside of the djangogirls/ folder, using the code editor that you installed earlier. You do this by opening a new file in the code editor and then saving it as requirements.txt in the djangogirls/ folder. Your directory will look like this:

djangogirls
├── myvenv
│   └── ...
└───requirements.txt
In your djangogirls/requirements.txt file you should add the following text:

djangogirls/requirements.txt
Django~=2.2.4
Now, run pip install -r requirements.txt to install Django.

command-line
(myvenv) ~$ pip install -r requirements.txt
Collecting Django~=2.2.4 (from -r requirements.txt (line 1))
  Downloading Django-2.2.4-py3-none-any.whl (7.1MB)
Installing collected packages: Django
Successfully installed Django-2.2.4

Installing Git
Download Git from git-scm.com and follow the instructions.

Create a PythonAnywhere account 
PythonAnywhere is a service for running Python code on servers "in the cloud". We'll use it for hosting our site, live and on the Internet.

We will be hosting the blog we're building on PythonAnywhere. Sign up for a "Beginner" account on PythonAnywhere (the free tier is fine, you don't need a credit card).

www.pythonanywhere.com
Note When choosing your username here, bear in mind that your blog's URL will take the form yourusername.pythonanywhere.com, so choose either your own nickname or a name for what your blog is all about. Also, be sure to remember your password (add it to your password manager, if you use one).

Creating a PythonAnywhere API token
This is something you only need to do once. When you've signed up for PythonAnywhere, you'll be taken to your dashboard. Find the link near the top right to your "Account" page:

Account link on the top right on the page

then select the tab named "API token", and hit the button that says "Create new API token".

The API token tab on the Account page

We're going to create a small blog!

The first step is to start a new Django project. Basically, this means that we'll run some scripts provided by Django that will create the skeleton of a Django project for us. This is just a bunch of directories and files that we will use later.

The names of some files and directories are very important for Django. You should not rename the files that we are about to create. Moving them to a different place is also not a good idea. Django needs to maintain a certain structure to be able to find important things.

Remember to run everything in the virtualenv. If you don't see a prefix (myvenv) in your console, you need to activate your virtualenv. We explained how to do that in the Django installation chapter in the Working with virtualenv part.

In your Mac OS X or Linux console, you should run the following command. Don't forget to add the period (or dot) . at the end!

command-line
(myvenv) ~/djangogirls$ django-admin startproject mysite .

The period . is crucial because it tells the script to install Django in your current directory (for which the period . is a short-hand reference).



django-admin.py is a script that will create the directories and files for you. You should now have a directory structure which looks like this:

djangogirls
├── manage.py
├── mysite
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── myvenv
│   └── ...
└── requirements.txt
Note: in your directory structure, you will also see your venv directory that we created before.

Let's make some changes in mysite/settings.py. Open the file using the code editor you installed earlier.

It would be nice to have the correct time on our website. Go to Wikipedia's list of time zones and copy your relevant time zone (TZ) (e.g. Europe/Berlin).

In settings.py, find the line that contains TIME_ZONE and modify it to choose your own timezone. For example:

mysite/settings.py
TIME_ZONE = 'Asia/Dhaka'

We'll also need to add a path for static files. (We'll find out all about static files and CSS later in the tutorial.) Go down to the end of the file, and just underneath the STATIC_URL entry, add a new one called STATIC_ROOT:

mysite/settings.py
STATIC_URL = '/static/'
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
When DEBUG is True and ALLOWED_HOSTS is empty, the host is validated against ['localhost', '127.0.0.1', '[::1]']. This won't match our hostname on PythonAnywhere once we deploy our application so we will change the following setting:

mysite/settings.py
ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']

Set up a database
There's a lot of different database software that can store data for your site. We'll use the default one, sqlite3.

This is already set up in this part of your mysite/settings.py file:

mysite/settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': os.path.join(BASE_DIR, 'db.sqlite3'),
    }
}
To create a database for our blog, let's run the following in the console: python manage.py migrate (we need to be in the djangogirls directory that contains the manage.py file). If that goes well, you should see something like this:

command-line
(myvenv) ~/djangogirls$ python manage.py migrate
Operations to perform:
  Apply all migrations: auth, admin, contenttypes, sessions
Running migrations:
  Rendering model states... DONE
  Applying contenttypes.0001_initial... OK
  Applying auth.0001_initial... OK
  Applying admin.0001_initial... OK
  Applying admin.0002_logentry_remove_auto_add... OK
  Applying contenttypes.0002_remove_content_type_name... OK
  Applying auth.0002_alter_permission_name_max_length... OK
  Applying auth.0003_alter_user_email_max_length... OK
  Applying auth.0004_alter_user_username_opts... OK
  Applying auth.0005_alter_user_last_login_null... OK
  Applying auth.0006_require_contenttypes_0002... OK
  Applying auth.0007_alter_validators_add_error_messages... OK
  Applying auth.0008_alter_user_username_max_length... OK
  Applying auth.0009_alter_user_last_name_max_length... OK
  Applying sessions.0001_initial... OK
And we're done! Time to start the web server and see if our website is working!



Starting the web server
You need to be in the directory that contains the manage.py file (the djangogirls directory). In the console, we can start the web server by running python manage.py runserver:

command-line
(myvenv) ~/djangogirls$ python manage.py runserver

Now you need to check that your website is running. Open your browser (Firefox, Chrome, Safari, Internet Explorer or whatever you use) and enter this address:

browser
http://127.0.0.1:8000/

Note that a command window can only run one thing at a time, and the command window you opened earlier is running the web server. As long as the web server is running and waiting for additional incoming requests, the terminal will accept new text but will not execute new commands.

We reviewed how web servers work in the How the Internet works chapter.

To type additional commands while the web server is running, open a new terminal window and activate your virtualenv -- to review instructions on how to open a second terminal window, see Introduction to the command line. To stop the web server, switch back to the window in which it's running and press CTRL+C - Control and C keys together (on Windows, you might have to press Ctrl+Break).


Creating an application
To keep everything tidy, we will create a separate application inside our project. It is very nice to have everything organized from the very beginning. To create an application we need to run the following command in the console (from djangogirls directory where manage.py file is):

Mac OS X and Linux:
(myvenv) ~/djangogirls$ python manage.py startapp blog

You will notice that a new blog directory is created and it contains a number of files now. The directories and files in our project should look like this:

djangogirls
├── blog
│   ├── admin.py
│   ├── apps.py
│   ├── __init__.py
│   ├── migrations
│   │   └── __init__.py
│   ├── models.py
│   ├── tests.py
│   └── views.py
├── db.sqlite3
├── manage.py
├── mysite
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── myvenv
│   └── ...
└── requirements.txt
After creating an application, we also need to tell Django that it should use it. We do that in the file mysite/settings.py -- open it in your code editor. We need to find INSTALLED_APPS and add a line containing 'blog.apps.BlogConfig', just above ]. So the final product should look like this:

mysite/settings.py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'blog.apps.BlogConfig',
]

Creating a blog post model
In the blog/models.py file we define all objects called Models – this is a place in which we will define our blog post.

Let's open blog/models.py in the code editor, remove everything from it, and write code like this:

blog/models.py
from django.conf import settings
from django.db import models
from django.utils import timezone


class Post(models.Model):
    author = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=200)
    text = models.TextField()
    created_date = models.DateTimeField(default=timezone.now)
    published_date = models.DateTimeField(blank=True, null=True)

    def publish(self):
        self.published_date = timezone.now()
        self.save()

    def __str__(self):
        return self.title
Double-check that you use two underscore characters (_) on each side of str. This convention is used frequently in Python and sometimes we also call them "dunder" (short for "double-underscore").

Create tables for models in your database
The last step here is to add our new model to our database. First we have to make Django know that we have some changes in our model. (We have just created it!) Go to your console window and type python manage.py makemigrations blog. It will look like this:

command-line
(myvenv) ~/djangogirls$ python manage.py makemigrations blog
Migrations for 'blog':
  blog/migrations/0001_initial.py:
  - Create model Post
 
 
 

Django prepared a migration file for us that we now have to apply to our database. Type python manage.py migrate blog and the output should be as follows:

command-line
(myvenv) ~/djangogirls$ python manage.py migrate blog
Operations to perform:
  Apply all migrations: blog
Running migrations:
  Applying blog.0001_initial... OK
Hurray! Our Post model is now in our database!


Django admin
To add, edit and delete the posts we've just modeled, we will use Django admin.

Let's open the blog/admin.py file in the code editor and replace its contents with this:

blog/admin.py
from django.contrib import admin
from .models import Post

admin.site.register(Post)

Remember to run python manage.py runserver in the console to run the web server. Go to your browser and type the address http://127.0.0.1:8000/admin/. You will see a login page


To log in, you need to create a superuser - a user account that has control over everything on the site. Go back to the command line, type python manage.py createsuperuser, and press enter.

Remember, to write new commands while the web server is running, open a new terminal window and activate your virtualenv. We reviewed how to write new commands in the Your first Django project! chapter, in the Starting the web server section.

Mac OS X or Linux:
(myvenv) ~/djangogirls$ python manage.py createsuperuser

When prompted, type your username (lowercase, no spaces), email address, and password. Don't worry that you can't see the password you're typing in – that's how it's supposed to be. Type it in and press enter to continue. The output should look like this (where the username and email should be your own ones):

Username: ola
Email address: ola@example.com
Password:
Password (again):
Superuser created successfully.
Return to your browser. Log in with the superuser's credentials you chose; you should see the Django admin dashboard.



