# Docker Sandbox Examples
This project has some basic examples with docker. The purpose is to be a personal reference for me but I i'm sharing because I hope this can be useful for someone. To run those examples be sure to run commands inside each directory.

# Table of Contents
- [Example 1: A basic Dockerfile](#1-build-first-example)
- [Example 2: Passing arguments for container](#2-build-with-arg-example)
- Example 3: (Removed)
- [Example 4: Running containers and copy files for it](#4-build-with-copy-example)
- [Example 5: Running an container as a simple python server](#5-build-dev-example)

## <a name="1-build-first-example">A basic Dockerfile</a>
In this example we download a simple image of nginx server and start the container runing a simple comand to echo 'hello'.

```
docker image build -t ex-simple-build
run docker image ls
```
Take a look on the image. Now lets start it:
```
docker container run -p 80:80 ex-simple-build
```

## <a name="2-build-with-arg-example">Passing arguments for container</a>
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
Foo

## <a name="5-build-dev-example">Example 5: Running an container as a simple python server</a>
Foo