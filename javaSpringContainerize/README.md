# Welcome to this repository about how to Containerize a Java Application
A step by step guide to containerize a Java Application using Docker as container

## Prerequisites

Before you begin, ensure you have the following:

- The latest version of **Docker Desktop** installed.
- A **Git client** installed.

## Overview

This guide walks you through containerizing and running a Java application using Docker.

## Get the Sample Application

Clone the sample Spring Boot application to your local development machine by running the following command:

```sh
$ git clone https://github.com/spring-projects/spring-petclinic.git
```

The sample application is built using Maven. For more details, check the `README.md` file in the repository.

## Initialize Docker Assets

Once you have the application, you need to create the necessary Docker assets for containerization. You can do this using Docker's built-in `docker init` feature.

### Using Docker Init

Inside the `spring-petclinic` directory, run the following command:

```sh
$ docker init
```

You'll be prompted with several questions about your application. Use the following responses:

```
? Do you want to overwrite them? Yes
? What application platform does your project use? Java
? What's the relative directory (with a leading .) for your app? ./src
? What version of Java do you want to use? 21
? What port does your server listen on? 8080
```

After running `docker init`, you should have the following files in your `spring-petclinic` directory:

- `Dockerfile`
- `.dockerignore`
- `docker-compose.yaml`

## Run the Application

To build and run the application inside a container, execute the following command:

```sh
$ docker compose up --build
```

Once the application is running, open a browser and go to:

```
http://localhost:8080
```

To stop the application, press `Ctrl + C` in the terminal.

## Run the Application in the Background

To run the application in detached mode (background), use the `-d` option:

```sh
$ docker compose up --build -d
```

To stop the running container, execute:

```sh
$ docker compose down
```

For more information about Compose commands, refer to the [Compose CLI reference](https://docs.docker.com/compose/).

## Summary

In this guide, you learned how to:

- Containerize a Java Spring Boot application using Docker.
- Use `docker init` to set up the necessary Docker assets.
- Run and stop the containerized application.

## Next Steps

In the next section, you will learn how to develop your Java application using Docker containers.

For more details, check the [Docker documentation](https://docs.docker.com/guides/java/containerize/).
