# Building Custom Images through Docker Server

## Creating Docker Images
- Dockerfile is a text file that has configuration for what program to contain in the container and what it should do.
- Docker Server will look into Dockerfile and build the usable image out of it.
- In side every Dockerfile:
    - Specify a base image 
    - Run some commands to install additional programs 
    - Specify a command to run on container startup.

## Dockerfile Teardown
- `FROM` tells docker server about the base image
- `RUN` will run a command
- `CMD` does also provide command the same way you would write into the shell

## What's a Base Image?
- Writing a dockerfile == Being given a computer with no OS and being told to install Chrome
- Base image is similar to installing operating system
- Downloading browser, installer is similar to running commands to install programs
- Executing chrome is writing commands on startup
- Why did we use alpine?
    - They come with a preinstalled set of programs useful to me

## The Build Process in Detail
- `docker build .` gives Dockerfile to Docker client and build image in the docker context
- `FROM alpine` will check in the local cache if alpine was downloaded before and if not it pulls from the Docker Hub
- `RUN apk add --update redis` and `CMD ["redis-server"]` will have intermediate containers that gets removed after the step
    - These will look at the previous step and take the image and make new temporary container
    - The line will run inside a container as primary running process
    - Take file system snapshot of the container and stop it

## Rebuilds with Cache
- There is file system snapshot for every container of every steps
- Fetching of alpine will not happen again because it is already downloaded
- Getting redis will not happen again either and will say `Using cache` because Docker knows its image after this step in cache
- This makes Docker very fast because it only reruns few steps

## Tagging an Image
- Tagging is done by `docker build -t <tag> .`
- Tag convention is `<Docker ID> / <Project Name> : <Version>`
    - Only version is actually tag and things in front is repo name
- Version does not need to be specified because it will use latest by default

## Manual Image Generation with Docker Commit
- Can manually create container and run a command and generate image out of it
- One can only mention first few segment of the id and Docker assumes it
- Can create container by `docker commit`