Docker Learning
===============

Here, I will try to  different commands to use Docker.

# Useful commands for Docker

1. Usually docker requires to run in `superuser` or `root` mode. Also possible without `root` mode. Will write later regarding this.
1. To build a docker image at first create a account in [docker hub](https://docs.docker.com/docker-hub/#step-1-sign-up-for-a-docker-account) and create a [repository](https://docs.docker.com/docker-hub/#step-2-create-your-first-repository)
1. To build a docker `docker build -t <your_username>/repository_name .`. Don't miss the last argument `a dot (.)`
1. To avoid intermediate and None images try this while building `sudo docker build -rm <your_username>/repository_name .` [Source](https://forums.docker.com/t/how-to-remove-none-images-after-building/7050/7).
1. To run a docker image `docker run <your_username>/repository_name`
1. To push docker image to docker hub: `docker push <your_username>/repository_name`. This command is also available in the docker hub repository.
1. To get all info related to docker: `docker system df -v`
1. All docker image list : `docker images` or `docker images -a`
1. All container list: `docker container ls -a`
1. To delete a docker image: `docker rmi IMAGE_TAG`. If need to force: `docker rmi -f IMAGE_TAG`
1. To delete a docker container: `docker rm IMAGE_TAG`
1. Delete all container with single command:

    ```sh
    sudo docker rm -vf $(sudo docker ps -aq)
    ```

    Delete all images with single command:

    ```sh
    sudo docker rmi -f $(sudo docker images -aq)
    ```

    All of the containers should be removed before removing all the images from which those containers were created.

# Useful docker Commands from [Docker tutorial - TechWorld with Nana](https://www.youtube.com/watch?v=3c-iBn73dDE&ab_channel=TechWorldwithNana)

Lets assume this works related to `redis` docker image , see [here](https://hub.docker.com/_/redis)

1. Pull image: `docker pull redis`
1. Check images in host machine: `docker images`
1. Run docker image: `docker run redis`. This will run image in attached mode that means you cannot do anything on that terminal.
1. Docker image can run as detached mode: `docker run -d redis`. On the terminal you can do other work. After running this command you will see a string which refers to container ID.
1. List of all running containers: `docker ps`. That will return a table where important parameters of containers will be available (container ID, port, container and image name ...)
1. List of all containers whether running or not: `docker ps -a`
1. running and stopping container with ID: `docker start CONTAINER_ID`, `docker stop CONTAINER_ID`. This ID will be seen from `docker ps`
1. Till now the installed redis image's version is `latest`. But if user want to use another version, eg `x.y.z`, do simply `docker run redis:x.y.z`. This will not again pull all layers but only the required layer for the specific version as already some layers are installed for `latest` version.
1. Now if `docker ps` run then user can see two image, container id.
1. Now a concept will come about binding ports as we will see that both redis container will listen through ports `6379/tcp`. It is configured by redis image (information is taken from video). That is related to `Container port and Host port`
    
    1. Now host machine cannot connect with both redis image if user don't bind these images explicitly to different port of host machine
    1. Multiple container can listen on same port but host machine can only communicate with a container through a single port
    1. Consider two images, `redis` and `redis:x.y.z`
    1. Run `docker run -p6000:6379 redis` and `docker run -p6001:6379 redis:x.y.z`
    1. Here, 6000 and 6001 are ports of host machine. Now, `docker ps` command will show `PORTS` parameter in table with the information of binding
    1. User can also run as detached mode : `docker run -p6000:6379 -d redis` and `docker run -p6001:6379 -d redis:x.y.z`
    1. If user does, ``docker run -p6001:6379 redis` it will throw error as 6001 port is already allocated

1. Debugging docker containers: `docker logs CONTAINER_ID` or `docker logs NAMES`. All parameters `CONTAINER_ID`, `NAMES` will be found in return table of `docker ps` command.
1. Naming of container by user's wish: `docker run -d -p6000:6379 --name redis-older redis:x.y.z`
1. To get a terminal on the container to do further process using Linux command `docker exec -it CONTAINER_ID /bin/bash` or `docker exec -it NAMES /bin/bash`. That will take user inside of the container. That means virtual file system inside the container. 
1. `-it` stands for `interactive terminal`.
1. By typing `exit` user can close the session.
1. `docker run` and `docker start` confusion

    1. `docker run` - tells to create container with different attribute (eg: names, port binding, attach/detach) from image
    1.  Then `docker ps` will show the available containers.
    1. And `docker start CONTAINER_ID` will start a container with the provided attributes



# Resources
1. [A github Repo](https://github.com/prakhar1989/docker-curriculum) where I have found organized information on Docker
1. [This](https://docker-curriculum.com/) one contains all information related to Docker
1.
