# python-Django-mysql-blog

## Django2SimpleBlog

[![Build Status](https://travis-ci.org/Tony133/Django2SimpleBlog.svg?branch=master)](https://travis-ci.org/Tony133/Django2SimpleBlog)

Simple Example Blog with Django 2.0

## Create Virtual Environment

```
    $ python -m venv myvenv or python3 -m venv myvenv
```
## Start up Environment

```
    $ source myvenv/bin/activate
```
## Install Django

```
    $ pip install django or pip install django==2.0
```

## Getting Migrate Table on database

```
    $ python manage.py migrate
```

## Create SuperUser for Admin

```
    $ python manage.py createsuperuser
```

## Getting Fixtures

```
    $ python manage.py loaddata data.json 
```

## Run App
```
    $ python manage.py runserver


-------------------------------------------
NEED TO RUN EVERY DAY

python3 -m venv myvenv
source myvenv/bin/activate
python manage.py runserver
-------------------------------------------






---------------------------------------------
---------------------------------------------
http://www.marinamele.com/taskbuster-django-tutorial/install-and-configure-mysql-for-django

Install the MySQL Django adapter, mysqlclient
Next, we need to install a MySQL database adapter for Python: the mysqlclient package. In the development enviroment:


$ pip install mysqlclient
1
$ pip install mysqlclient
and add it into your requirements/base.txt file as:


# requirements/base.txt
...
mysqlclient==1.3.6
1
2
3
# requirements/base.txt
...
mysqlclient==1.3.6
Next you have to install it into your testing environment, where you can use:


$ pip install -r requirements/testing.txt
1
$ pip install -r requirements/testing.txt
Configure the Django Database Settings
Now, we need to edit the settings for developing and testing (only local). Edit the files settings/testing.py and settings/development.py and add the following:


DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': get_env_variable('DATABASE_NAME'),
        'USER': get_env_variable('DATABASE_USER'),
        'PASSWORD': get_env_variable('DATABASE_PASSWORD'),
        'HOST': '',
        'PORT': '',
    }
}
1
2
3
4
5
6
7
8
9
10
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': get_env_variable('DATABASE_NAME'),
        'USER': get_env_variable('DATABASE_USER'),
        'PASSWORD': get_env_variable('DATABASE_PASSWORD'),
        'HOST': '',
        'PORT': '',
    }
}
Remember that these files import from the settings/base.py file, in which we defined the get_env_variable function as:


from django.core.exceptions import ImproperlyConfigured

def get_env_variable(var_name):
    try:
        return os.environ[var_name]
    except KeyError:
        error_msg = "Set the %s environment variable" % var_name
        raise ImproperlyConfigured(error_msg)
1
2
3
4
5
6
7
8
from django.core.exceptions import ImproperlyConfigured
 
def get_env_variable(var_name):
    try:
        return os.environ[var_name]
    except KeyError:
        error_msg = "Set the %s environment variable" % var_name
        raise ImproperlyConfigured(error_msg)
Next, edit the postactivate file of each environment:


$ vi $VIRTUAL_ENV/bin/postactivate
1
$ vi $VIRTUAL_ENV/bin/postactivate
and add the Database settings:


export DATABASE_NAME='taskbuster_db'
export DATABASE_USER='myusername'
export DATABASE_PASSWORD='mypassword'
1
2
3
export DATABASE_NAME='taskbuster_db'
export DATABASE_USER='myusername'
export DATABASE_PASSWORD='mypassword'
Now edit the predeactivate file of each enviroment and add:


unset DATABASE_NAME
unset DATABASE_USER
unset DATABASE_PASSWORD
1
2
3
unset DATABASE_NAME
unset DATABASE_USER
unset DATABASE_PASSWORD
To make these changes effective, you need to deactivate and activate the environments.

 

Ok, now we are ready to check, sync and migrate our database.


$ python manage.py check
$ python manage.py migrate
1
2
$ python manage.py check
$ python manage.py migrate
You will be asked to create a super user, so create one now 😉 If you’re not asked to create one, you might want to do so with:


$ python manage.py createsuperuser
1
$ python manage.py createsuperuser
Finally, let’s run our tests to see that everything works as expected!


$ python manage.py test
1
$ python manage.py test


-----------------------------------------------------
-----------------------------------------------------
