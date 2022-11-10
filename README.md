# Django_app_deploy_to_Docker

Project Scope: To create a Django application and deploy it to Docker, then to Docker compose.

Procedure: 
  1.	Environment setup
    a.	Created a virtual environment
      i.	Cmd to create: python -m venv venv
      ii.	Cmd to start: . venv/scripts/activate
  2.	Create an app folder with a requirements.txt that has the following
   i.	django==3.2.2
   ii.	gunicorn==20.0.4
  iii.	djangorestframework==3.12.4
  iv.	python-decouple==3.4
  v.	psycopg2-binary==2.9.1
  3.	Install packages while in the app folder:
    a.	CMD: python -m pip install -r requirements.txt
  4.	Use django_admin to scaffold out the django project
   a.	CMD: django-admin startproject nc_tutorials .
  5.	Test the development server by commenting out the following: 
  6.	To start the Django Development server run the following command:
    a.	CMD: python manage.py runserver 8000
  7.	Open web browser to verify server is running http://127.0.0.1:8000/
  8.	Create a docker file while in the App folder
    a.	Command palette: Add Docker Files to Workspace
    b.	Select application platform: Python:Django
    c.	Choose the apps entry point: manage.py
    d.	Port to listen to: 8000
    e.	Include option docker compose file? No
    f.	Two files will be generated .dockignore and Dockerfile to build docker image
  9.	In Dockerfile find the very last instruction that binds the Gunicorn server to wsgi file.
    a.	CMD ["gunicorn", "--bind", "0.0.0.0:8000", "nc_tutorials.wsgi"]
    b.	Gunicorn is typically used as a webserver that routes HTTP requests and responses for Django app. Gunicorn is also known as WSGI server.
  10.	Build the docker image then run it on the container
    a.From the folder that has the Dockerfile run the following
    b.Command palette: Docker images: Build image
    c.Select image group: hellodjango
    d.Select image: latest
    e.Confirmed the Django web app can be viewed at http://localhost:8000
