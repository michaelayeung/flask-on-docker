# Flask on Docker

## Overview
This repository follows this tutorial: https://testdriven.io/blog/dockerizing-flask-with-postgres-gunicorn-and-nginx/. The tutorial demonstrates how to structure and containerize a Flask application using Docker and integrating it with Postgres, Gunicorn, and Nginx using a modified Instragram tech stack. 

The Flask application allows users to upload and serve images, shown in the gif below. 
## Image Upload Example

![Upload Image](https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExY2t2bmhkNmkzM2VzN2twOHU4ejJhbG14cGswMmFuZ2p3NnN4OThsZiZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/FdTRLxGdgZmRdjRFdp/giphy.gif)


## Build Instructions
To set up and run the Flask application, do the following:

1. **Clone the Repository:**

```
$ git clone https://github.com/michaelayeung/flask-on-docker
$ cd flask-on-docker
```

2. **Create Environment Files:**
In the project root, create a file .env.prod.db that contains the following:

```
POSTGRES_USER={your username}
POSTGRES_PASSWORD={your password}
POSTGRES_DB={your db name}
```

3. **Build and Start Containers**:

```
$ docker compose -f docker-compose.prod.yml up -d --build
$ docker compose -f docker-compose.prod.yml exec web python manage.py create_db
```

4. **Access the Web Application:**
Open a browser and upload an image at the following link.

```
http://localhost:8080/upload
```


5. **View the Image:**
To view the image go to the following link on your web browser.

```
http://localhost:8080/media/IMAGE_FILE_NAME
```

6. **Shut Down the Containers:**
Run the following to remove the containers and volumes.
```
$ docker compose -f docker-compose.prod.yml down -v
```

