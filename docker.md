# Docker 🐳

- **Container** is a running environment for **image**
- Container is a process on your machine that has been isolated from all other processes on the host machine 
- Container image contain everything needed to run an application (dependencies, config, scripts, etc)


## Commands

- `docker pull <image:tag>`: download and image (`docker pull redis:5.0`)
- `docker ps`: show a list of running containers
- `docker ps -a`: show a list of all containers 
- `docker images`: list images
- `docker run <image>`: start a new container from an image
- `docker run -d <image>`: running in detached mode/background
- `docker run -p <host_port>:<container_port> <image>`: bind our port to container port (`docker run -p 8080:80 nginx`)
- `docker stop <container_id>`: stop the container
- `docker start <container_id>`: start the container

## Resources

- [Docker Docs: Get started](https://docs.docker.com/get-started/)
- [Docker Labs](https://github.com/collabnix/dockerlabs)
- [TechWorld with Nana - YouTube](https://www.youtube.com/c/TechWorldwithNana)
