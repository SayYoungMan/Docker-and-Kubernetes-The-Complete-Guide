# Manipulating Containers with the Docker Client

## Docker Run in Detail
- `docker run <image name>` to create and run a container.

## Overriding Default Commands
- `docker run <image name> <command>` to provide start up command to docker run
- `docker run busybox echo hi there` will provide echo hi there
- Busybox Image has snapshot of file system and that will be given to the hard drive segment.
- `docker run hello-world echo hi there` will not work because these commands do not exist within file system of hello-world.

## Listing Running Containers
- `docker ps` will list running containers.
- CONTAINER ID, IMAGE, COMMAND, CREATED, STATUS, PORTS, NAMES are provided headers
- `docker ps --all` shows all containers that I have ever run

## Container Lifecycle
- `docker run` = `docker create` + `docker start`
- Creating container is setting up file system snapshot to use
- Starting is executing startup command
- `docker create hello-world` will provide id of container
- `docker start -a 230a44c662ab89179354dc04cfb672bef006887bc4c73d82801976f21f578814` will run the container
- `-a` attach to the container and provide output of container to the terminal

## Restarting Stopped Containers
- We can start the exited container back up by `docker start -a <id>` of the container
- Cannot however replace the issued startup command

## Removing Stopped Containers
- Good to delete exited containers because it will save disk space
- `docker system prune` will remove all containers, images and build cache

## Retrieving Log Outputs
- `docker logs <container id>` will show all the outputs that was emitted in the container
- Useful for inspect and debug

## Stopping Containers
- `docker stop <id>` will send SIGTERM to the process inside the container and it will give some time to do some cleanup.
    - If it doesn't shutdown in 10 seconds, then it will automatically change to docker kill
- `docker kill <id>` will send SIGKILL to the process and it will not get to do any additional work further.

## Multi-command Containers
- running redis-server in docker and redis-cli outside will not work because redis-cli will not recognise the redis-server inside the container

## Executing Commands in Running Containers
- `docker exec -it <container id> <command>` will allow us to execute additional command in container
- `-it` allows us to provide input to the container

## The Purpose of -it Flag
- Every process in Linux has three communication channels:
    - STDIN will get any input
    - STDOUT will provide output to the terminal
    - STDERR will show error on the terminal if any
- `-it` is combination of `-i` (attaching terminal to STDIN) and `-t` (formatting the output)

## Getting a Command Prompt in a Container
- `docker exec -it <id> sh` will open the shell inside the container
- `Ctrl + D` to get out
- `sh` is a command processor just like bash powershell and zsh

## Starting with a Shell
- `docker run -it <image> sh` will create, start and run the shell inside the container and attach the container

## Container Isolation
- Two containers have absolutely isolated file systems so creation of file in one is not reflected in another.