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

### [docker container](https://docs.docker.com/engine/reference/commandline/container/): manage containers

- `docker container ls`: show running containers
- `docker container ls -a`: show all container

- `docker container run <image>`:
  - `--publish <host_port>:<container_port>` or `-p <host_port>:<container_port>`: exposes the port on your machine
  - `--rm`: remove the container when it exits
  - `--interactive` or `-i`: keep stdin open even if not attached
  - `--tty`, `-t`
  - `--network <network_name>`: connect the container to a network
  - `--network-alias <network alias>`: add network-scoped alias to a network
  - `--name <name>`: name the container
  - `--detach` or `-d`: run detached
  - examples:
    - `docker container run --publish 80:80 --detach --name webhost nginx`
    - `docker container run -d --name mysql -e MYSQL_RANDOM_ROOT_PASSWORD=true mysql`
    - `docker container run -it alpine sh`
    - `docker container run -d --net mynetwork --net-alias search elasticsearch:2`
- `docker container rm <container_name_or_id>`
- `docker container rm -f <container_name_or_id>`: force removal - can remove running containers
  - `docker container rm 63f 690 ode`
  
## Resources

- [Docker Docs: Get started](https://docs.docker.com/get-started/)
- [Docker Labs](https://github.com/collabnix/dockerlabs)
- [TechWorld with Nana - YouTube](https://www.youtube.com/c/TechWorldwithNana)
