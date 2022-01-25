# Making Real Projects with Docker

## Project Outline
- Aim to create Node JS server and run inside the container
- Steps:
    - Create Node JS web app
    - Create a Dockerfile
    - Build image
    - Run image as container
    - Connect web app from browser

## Copying Build Files
- `COPY` copies the files from the machine relative to build context to inside the container

## Container Port Mapping
- Containers have separated set of ports
- We have to set up explicit `port mapping` such that any request to certain port of localhost is automatically forwarded to the container port
- This is strictly limited to the incoming traffic
- It can be done at runtime by the `docker run -p 8080(localhost) : 8080(container)` command

## Specifying a Working Directory
- Should have work directory because having same file name as default file can overwrite files in root directory
- `WORKDIR` command will execute commands relative to the specified path