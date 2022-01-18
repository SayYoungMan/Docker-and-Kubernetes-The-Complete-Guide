# Why use Docker?
- Docker makes it really easy to install and run software without worrying about setup or dependencies.

# What is Docker?
- `Docker` is a platform or ecosystem around creating and running containers.
- `Image` is a signle file with all the dependencies and config required to run a program.
- `Container` is an instance of an image that runs a program.

# Docker for Windows/Mac
- There are two tools inside the program
    - `Docker Client (Docker CLI)`: we are going to issue commands to this tool
    - `Docker Server (Docker Daemon)`: tool that is responsible for creating images, running containers, etc.

# Using Docker Client
- When `docker run hello-world` is typed, following steps occur:
    1. Docker Client contacts Docker Daemon.
    1. Docker Daemon checks image cache for the image and if it's not there pull the image from Docker Hub.
    1. Docker daemon created new container from that image
    1. Docker Daemon streamed the output to Docker Client

# What is Container?
- In operating system, there is `kernel` which governs access between the software and hardware, via `System call`.
- Since, there cannot be same installation in the same hardware, namespacing can help segment the hardware for different system calls.
- `Namespacing` is isolating resources per process (or group of processes).
- `Control Groups` is used to limit amount of resources used per process.
- `Container` is a process that has grouping of resources specifically assigned.

# How's Docker Running?
- Namespacing and Control Groups belong to Linux OS only.
- Within docker there exists Linux Virtual Machine which has Linux Kernel.