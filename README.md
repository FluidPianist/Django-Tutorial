# DJango Basic Tutorial

## For first time setup of VirtualEnv

#### 1. Run the following Commands :

```sh
   pip install virtualenv
   pip install virtualenvwrapper
   gedit ~/.bashrc
```

#### 2. Add and save the following lines :

```sh
   export WORKON_HOME=your-virtual-env-path
   mkdir -p $WORKON_HOME
   source ~/.local/bin/virtualenvwrapper.sh
```

#### 3. To create an environment in your-path :

```sh
mkvirtualenv <custom-env-name>
```

## For Activating and Deactivating your virtual-env

#### Navigate to the directory in terminal and run :

```sh
source \bin\activate
```

#### For Deactivating :

```sh
deactivate
```

## Creating and Working with Django Project

#### 1. Install Django in the virtual environment:

```sh
pip install django
```

#### 2. Navigate to your desired directory and create :

```sh
django-admin startproject <project-name>
```

#### 3. Starting the App :

```sh
python manage.py runserver your-port
```

#### 4. Running and Applying migrations :

Migrations will contain the sql commands to apply to your schema for reflecting the changes you have made to your model

```sh
python manage.py makemigrations
python manage.py migrate
```

#### 5. Setting up code-formatting in vs-code :

1. Install autopep8 extension, add the following field to your settings.json :

```json

  "[python]": {
    "editor.defaultFormatter": "ms-python.autopep8"
  }

```

2. Install the Django Extension and add the following in Settings.json. This will add django-html and django-txt file formats in vs-code

```json
  "emmet.includeLanguages": {
    "javascript": "javascriptreact",
    "django-html": "html"
  },
  "files.associations": {
    "**/templates/*.html": "django-html",
    "**/templates/*": "django-txt"
  },
```

3. djlint extension for Django :

- install djlint extention from vs code marketplace and then run the following :

```sh
  /bin/python3 -m pip install -U djlint
```

- Add the following line in vscode settings.json :

```json
  "[django-html]": {
    "editor.defaultFormatter": "monosans.djlint"
  }
```

- For ignoring a purticular lint rule, add such lines at the top of the html file :

```html
{# djlint:off H030 H020 H031 H023#}
```

## Django Notes

- A Django Project or Web Application can contain many services or apps, inside it. Each app will have its own directory.

- An app can be created as follows inside the project directory : `python manage.py startapp groceries_app`

- add the app name in INSTALLED_APPS list in settings.py present in the project name subfolder

- the project name sub folder will containt configs and code pertaining to all the apps while the app name subfolder will hold the same for a purticular service

- view will contain the functions which will be executed on hitting a purticular url.

- a url is mapped with the function/template defined in view inside the urls.py file

- For a purticular app (See groceries app for reference):

  1. add a urls.py file inside the app and map the function in view.
  2. include the urls of app inside the urls.py file of the project subdirectory or you can say root app subdirectory

- create a tempelate folder to add the html code and then render it in view function

- create a static folder and add css stylesheets there, see base.html for reference

- we can create a base template and then import it in other html templates

- Creating a SuperUser in the built in default python app : `python manage.py createsuperuser`

- Run the server and login with the credentials created previously to view the user management system for your app.

- it is recommended to use this app for user management unless your app requirements are quite different.

- Database Functionality will have to be implemented by you in case this app is used

- Before Comitting to gihub :

  1. Create a .gitigmore and add .env to it in root.
  2. copy SECRET_KEY from settings.py and paste it .env
  3. In settings.py, import the creds from .env. Refer to settings.py to see how.
  4. To create requirements.txt of the python libraries installed in virtual env : `pip freeze > requirements.txt`
  5. To install the requirements :`pip install -r requirements.txt`
