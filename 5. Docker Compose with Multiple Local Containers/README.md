# Docker Compose with Multiple Local Container

## App Overview
- App that displays number of times the user visited the server
- We need web server and Redis server to store number of visits
- When there is a lot of traffic, there will be more instances of docker container but if container has both, Redis will have different values so we don't want multiple of them.

## Introducing Docker Compose
- Separate CLI that gets installed with Docker
- Used to start up multiple Docker containers at the same time
- Automates some of the long-winded arguments we were passing to `docker run`

## Networking with Docker Compose
- By putting docker containers in the same docker-compose, it will automatically configure network between one another
- service name (`redis-server`) is enough host name for Docker to redirect it to the redis container

## Docker Compose Commands
- `docker-compose up` is to run the containers
- `docker-compose up --build` is to rebuild image of a container inside it

## Stopping Docker Compose Containers
- `docker-compose down` will stop all the running containers

## Automatic Container Restarts
- 0 exit code represents we exited and everything is OK but other numbers indicate error
- Restart Policies
    - `"no"`: Never attempt to restart (make sure to have "" because no by default is false)
    - `always`: always attempt to restart
    - `on-failure`: only start if container stops with error code
    - `unless-stopped`: always restart unless we forcefully stop it
- When restarting not stopping the existing container but reusing them and attaching to it

## Container Status with Docker Compose
- `docker-compose ps` will show status of containers under docker-compose
- Will not work on other working directories because it looks for docker-compose.yml