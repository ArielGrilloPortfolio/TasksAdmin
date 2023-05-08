# TasksAdmin
A simple tasks manager

Based on the following Tutorial
https://www.youtube.com/watch?v=38XWpyEK8IY

Depoloyed in Railways.app
https://tasksadmin-production.up.railway.app/tasks


## BACKEND
* pip install virtualenv
* python -m venv  venv

Install Python extention for visual studio code
* F1, python: select interprete (Seleccionar el de la estrellita, digamos el local)

### Django 
* pip install django
* django-admin startproject django_crud_api . (el punto es para que no cree una carpeta)
* python manage.py startapp tasks

En django_crud_api/settings.py agregamos el nombre de la app 'tasks'

* python manage.py migrate (para que inisialice las migrations)

* python manage.py runserver

# Backend Deployment
## Run server  en producción Django
* pip install gunicorn

## whitenoise
* pip install whitenoise
Config: https://whitenoise.readthedocs.io/en/latest/
Ver la config para añadir el middleware y la config para cache

## DJ Database
pip install dj-database-url # Select database for dev and prod environment

## Pscopg2
* pip install psycopg2 # En prod usamos postgresql

## Dendencias del proyecto en Requirements.txt
* pip freeze > requirements.txt # Crear las dependencias
* pip install -r .\requirements.txt (Instalar las dependencias)

## Settings database
DATABASES = {
    "default": dj_database_url.config(default="sqlite://db.sqlite3")
}


## STATIC_ROOT setting
Añadir en settings.py justo debajo de STATIC_URL
STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')
Debo colocar al principio import os
* python manage.py collectstatic

## Procfile
web: python manage.py collectstatic && gunicorn django_crud_api.wsgi

## runtime.txt
crear el archivo y pegar el resultado de python --version

## Railways CLI
Doc: https://docs.railway.app/develop/cli
* iex "& {$(irm get.scoop.sh)} -RunAsAdmin" #install scoop for admin
* scoop install railway

# Frontend Deployment
## Static files dir incluiding dist
* npm run build # Crear el build en /dist
Edit setting.py para agergar. La idea es incluir el /dist en las staticfiles

STATICFILES_DIRS = [
    os.path.join(BASE_DIR,'client','dist')
]


### Django Rest Framework
Django rest framwork. https://www.django-rest-framework.org/

* pip install djangorestframework
* pip install django-cors-headers (https://pypi.org/project/django-cors-headers/) => Ver para los detalles de la cof. Middleware

Configurar cors-headers al final django_crud_api/settings.py
CORS_ALLOWED_ORIGINS = [
    "http://localhost:5173" # Dónde corre FE
]

### Modelo
Creamos en models.py el modelo task y ejecutamos
* python manage.py makemigration tasks
* python manage.py migrate tasks (aplicamos en sqlite)

* python manage.py createsuperuser (Colocar usr & pass)

## Documentación de la API
* pip install coreapi
Doc: https://www.django-rest-framework.org/coreapi/

## FRONTEND React
ViteJs: https://vitejs.dev/
* npm create vite (seguimos los pasos)

* npm i react-router-dom react-hot-toast axios react-hook-form

#tailwindcss
https://tailwindcss.com/docs/guides/vite

* npm install -D tailwindcss postcss autoprefixer
* npx tailwindcss init -p

Consultar la doc de tailwincss para aplicar los pasos necesarios de la instalación.
