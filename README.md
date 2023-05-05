# TasksAdmin
A simple tasks manager

Based on the following Tutorial
https://www.youtube.com/watch?v=38XWpyEK8IY

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

python manage.py migrate (para que inisialice las migrations)

python manage.py runserver

Django rest framwork. https://www.django-rest-framework.org/
pip install djangorestframework
pip install django-cors-headers (https://pypi.org/project/django-cors-headers/) => Ver para los detalles de la cof. Middleware
Configurar cors-headers al final django_crud_api/settings.py
CORS_ALLOWED_ORIGINS = [
    "http://localhost:5173" # Dónde corre FE
]


Creamos en models.py el modelo task y ejecutamos
python manage.py makemigration tasks
python manage.py migrate tasks (aplicamos en sqlite)

python manage.py createsuperuser
ariel.grillo usr&pass

## Documentación de la API
pip install coreapi
https://www.django-rest-framework.org/coreapi/

## FRONTEND React
ViteJs: https://vitejs.dev/
npm create vite (seguimos los pasos)

npm i react-router-dom react-hot-toast axios react-hook-form

#tailwindcss
https://tailwindcss.com/docs/guides/vite

npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
