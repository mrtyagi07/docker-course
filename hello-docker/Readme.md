# Docker Project

This project demonstrates the usage of Docker to containerize an application.

## Getting Started

Follow the steps below to build and run the Docker image.

### Step 1: Build the Docker Image

To build the Docker image, run the following command in the terminal:

```shell
docker build -t hello-docker .
```

### Step 2: Check if the Docker image has been successfully created.

```shell
docker images
```

### Step 3: Run Docker image

```shell
docker run hello-docker
```

### Step 4: Run image in Interactive mode

It executes the shell (sh) within the container, allowing you to interact with the container's filesystem and execute commands inside it.

```shell
docker run -it hello-docker sh
```

```
/app # node hello.js
Hello, Docker!
/app #
```
