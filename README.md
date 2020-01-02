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


