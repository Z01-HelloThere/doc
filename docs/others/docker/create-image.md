# How to create a Docker image

<!-- for Joplin users -->
<!-- ${toc} -->

## Image vs Container?

Docker **images** provide the instructions and ingredients, while Docker **containers** are the actual running applications built from those instructions.

### Key differences

- **Function** An image is a template, a container is a running instance.
- **Mutability** Images are read-only, containers are writable. Changes in a container won't affect the original image.
- **Lifespan** Images are meant to be shared and reused, containers are typically created and destroyed as needed.

## List

- [Docker Official Images](https://hub.docker.com/search?q=&type=image&image_filter=official)
- [Verified Publisher](https://hub.docker.com/search?q=&image_filter=store&type=image)

## How to create a docker image

### Create a Dockerfile

```ruby title="Dockerfile" linenums="1"
# syntax=docker/dockerfile:1

# specify the base image to  be used for the application, alpine or ubuntu

FROM golang:1.22-alpine

# create a working directory inside the image

WORKDIR /app

# copy directory files i.e all files ending with .go

COPY . ./

# compile application

RUN go build -o ./ASCII-art-web && apk add --no-cache bash
# tells Docker that the container listens on specified network ports at runtime

EXPOSE 8080

# command to be used to execute when the image is used to start a container

CMD [ "/ASCII-art-web" ]
```

### build the image

```sh
sudo docker build --tag ascii-art-web .
```

##

```sh
sudo docker build --tag ascii_web .
```

### check if image is created

```sh
sudo docker images
```

## How to create and launch a container from the Image

### Commands

```sh
sudo docker container run -p 8080:8080 --detach --name <container_name> <image>
```

> note: you can change the port to `0:8080` to ask to your kernel to handle the attribution of the port. Handy in a script when you don't know if your user port 8080 is free.

### stop a container

```sh
sudo docker stop <container_name>
```

### remove a container

```sh
sudo docker rm <container_name>
```

### :warning: remove an image

```sh
sudo docker rmi <image>
```
