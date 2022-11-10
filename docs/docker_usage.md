Docker Learning
===============

Here, I will try to  different commands to use Docker.

# Useful commands for Docker
1. Usually docker requires to run in `superuser` or `root` mode. Also possible without `root` mode. Will write later regarding this.
1. To build a docker image at first create a account in [docker hub](https://docs.docker.com/docker-hub/#step-1-sign-up-for-a-docker-account) and create a [repository](https://docs.docker.com/docker-hub/#step-2-create-your-first-repository)
1. To build a docker `docker build -t <your_username>/repository_name .`. Don't miss the last argument `a dot (.)`
1. To get all info related to docker: `docker system df -v`
1. All docker image list : `docker images` or `docker images -a`
1. All container list: `docker container ls -a`
1. To delete a docker image: `docker rmi IMAGE_TAG`. If need to force: `docker rm -f IMAGE_TAG`
1. To delete a docker container: `docker rm IMAGE_TAG`


# Resources
1. [A github Repo](https://github.com/prakhar1989/docker-curriculum) where I have found organized information on Docker
1. [This](https://docker-curriculum.com/) one contains all information related to Docker
1.
