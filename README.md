# fermiq_docker
Docker Setup for FermiLib+ProjectQ=FermiQ.

This Docker image will help users to easily install [FermiLib](https://github.com/ProjectQ-Framework/FermiLib.git) and [ProjectQ](https://github.com/ProjectQ-Framework/ProjectQ). Check out Docker's [website](https://www.docker.com/what-container) that describes what a container image is and why it can be so useful. 

## What is included?
- Conda Python 3 (but you can also use Python 2 with one minor change in Dockerfile. See Dockerfile for instructions.)
- [ProjectQ](https://github.com/ProjectQ-Framework/ProjectQ) (git repo) 
- [FermiLib](https://github.com/ProjectQ-Framework/FermiLib.git) (git repo)

## Usage

To use this image, you first need to install [Docker](https://www.docker.com/).

After installing Docker, there are two options: (1) pulling the Docker image from Docker Hub or (2) building the image.

(1) To pull the Docker image, execute:

```
docker pull hsim13372/fermiq_docker
```
 
(2) To build the Docker image, move the [Dockerfile](https://github.com/hsim13372/fermiq_docker/blob/master/Dockerfile) to your working directory. Then execute:

```
docker build -t "hsim13372/fermiq_docker" .
```

Finally, to run the image (assuming you're still inside your working directory), execute with `YOUR_WORK_DIR` as the path to your working directory:

```
docker run -it -v $(pwd):YOUR_WORK_DIR -w YOUR_WORK_DIR hsim13372/fermiq_docker
```

When you're done using the Docker image, you can use `docker stop YOUR_CONTAINER_ID` or `docker kill YOUR_CONTAINER_ID` to stop your container (you can get your container ID by using the command `docker ps`). Finally, feel free to use this as a parent image to build a more customized image layer, perhaps containing the available plugins ([PySCF](https://github.com/ProjectQ-Framework/FermiLib-Plugin-PySCF) or [Psi4](https://github.com/ProjectQ-Framework/FermiLib-Plugin-Psi4)) for FermiLib.
