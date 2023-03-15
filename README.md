# docker image for ubuntu with user/group

## Instalation
```sh
git clone https://github.com/StaticTaku/ubuntu_vanilla.git
```

## Setup
change DOCKER_USER, DOCKER_GROUPNAME, DOCKER_UID, DOCKER_GID, DOCKER_PASS in .env file. 
In .env file, ex.
```sh
    DOCKER_USER=statictaku
    DOCKER_GROUPNAME=statictaku
    DOCKER_UID=1000
    DOCKER_GID=1000
    DOCKER_PASS=DummyPass
```

```sh
    docker-compose up -d && \ #make image, create container from the image, then start container
    docker-compose exec -it vanilla bash #get into the container
```

In the container, you should do passwd to change the password in the container because of some security reasons.
```sh
    passwd
```

## Description
./ubuntu_vanilla is the home directory in the container.