Docker Learning
===============

Here, I will try to  different commands to use Docker.

# Useful commands for Docker

1. Usually docker requires to run in `superuser` or `root` mode. Also possible without `root` mode. Will write later regarding this.
1. To build a docker image at first create a account in [docker hub](https://docs.docker.com/docker-hub/#step-1-sign-up-for-a-docker-account) and create a [repository](https://docs.docker.com/docker-hub/#step-2-create-your-first-repository)
1. To build a docker `docker build -t <your_username>/repository_name .`. Don't miss the last argument `a dot (.)`
1. To avoid intermediate and None images try this while building `sudo docker build -rm <your_username>/repository_name .` [Source](https://forums.docker.com/t/how-to-remove-none-images-after-building/7050/7).
1. To run a docker image `docker run <your_username>/repository_name`
1. To push docker image to dicker hub: `docker push <your_username>/repository_name`. This command is also available in the docker hub repository.
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


# Resources
1. [A github Repo](https://github.com/prakhar1989/docker-curriculum) where I have found organized information on Docker
1. [This](https://docker-curriculum.com/) one contains all information related to Docker
1.
