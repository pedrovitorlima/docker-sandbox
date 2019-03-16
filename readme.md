# Docker Sandbox Examples
This project has some basic examples with docker. The purpose is to be a personal reference for me but I i'm sharing because I hope this can be useful for someone. To run those examples be sure to run commands inside each directory.

# Table of Contents
- [Example 1: A basic Dockerfile](#1-build-first-example)
- [Example 2: Passing arguments for container](#2-build-with-arg-example)
- Example 3: (Removed)
- [Example 4: Running containers and copy files for it](#4-build-with-copy-example)
- [Example 5: Running an container as a simple python server](#5-build-dev-example)
- [Example 6: A AMPP environment using docker-compose](#x-ampp-environment-docker-compose)
- [Example 7: Simple docker-compose example](#7-docker-compose-example)

## <a name="1-build-first-example">Example 1: A basic Dockerfile</a>
In this example we download a simple image of nginx server and start the container runing a simple comand to echo 'hello'.

```
docker image build -t ex-simple-build
run docker image ls
```
Take a look on the image. Now lets start it:
```
docker container run -p 80:80 ex-simple-build
```

## <a name="2-build-with-arg-example">Example 2: Passing arguments for container</a>
In this example we download a debian image and start a simple container with. In Dockerfile we have declared some variables that can be assigned with a docker command.

```
docker image build -t ex-build-arg .
docker container run ex-build-arg bash -c 'echo $S3_BUCKET'
```
The 'file' value will be showed because we dont build the image saying his value. Now we can see:
```
docker image build --build-arg S3_BUCKET=myapp . -t ex-build-arg .
docker container run ex-build-arg bash -c 'echo $S3_BUCKET'
```

## <a name="4-build-with-copy-example">Example 4: Running containers and copy files for it</a>
In this example we create a file a html file and make a copy of it to inside of our nginx container. After run, we can see the html content in localhost. Please take a look inside of Dockerfile.

```
docker image build -t ex-build-copy .
docker container run -p 80:80 ex-build-copy
```

## <a name="5-build-dev-example">Example 5: Running an container as a simple python server</a>
This is a little more complex example. In the example's folder we have a .py script that represents a server. The Dockerfile will download and run a image and start the server. After that we can see the result accessing localhost.

```
docker image build -t 5-build-dev-example .
docker container run -it -v $(pwd):/app -p 80:8000 --name python-server 5-build-dev-example
```

Also, after this, we can push our image to dockerhub.
Before all, tag your image:
```docker image tag 5-build-dev-example YOUR_USER/YOUR-BUILD:VERSION```

1) Make login on dockerhub:
```docker login --YOUR_LOGIN```
2) Enter your password
3) After login succeeded, push the image:
```docker image push YOUR_LOGIN/YOUR-BUILD```

## <a name="x-ampp-environment-docker-compose">Example 6: A AMPP environment using docker-compose</a>

First, you need to download docker-compose (for Ubuntu, read this: https://linuxize.com/post/how-to-install-and-use-docker-compose-on-ubuntu-18-04/).

Inside the example's folder we have 2 subfolders:
-apache has a Dockerfile to the Apache, needed to PHP;
-php has a Dockerfile to the PHP also;

Others stuffs are inside docker-compose.yml, like mysql and phpmyadmin image descriptions and configuration. 

To run it, just type this command:
```docker-compose up```

## <a name="7-docker-compose-example">Example 7: A docker-compose example</a>
In this example we create a docker-compose.yml and configure three items: backend, frontend and database. The backend has app.js to proccess requests and frontend just show a simple string on screen.

To run it, just type this command:
```docker-compose up``` 