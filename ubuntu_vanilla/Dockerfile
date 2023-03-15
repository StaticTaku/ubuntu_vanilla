FROM ubuntu:20.04
#for auto-install
ENV DEBIAN_FRONTEND=noninteractive
#change repository server to the server in Japan
RUN sed -i 's@archive.ubuntu.com@ftp.jaist.ac.jp/pub/Linux@g' /etc/apt/sources.list
#update & upgrade
RUN apt-get -y update && apt-get -y upgrade

#install something useful
RUN apt-get install -y \
        sudo \
        tzdata

#set environmental variable used in container
ARG DOCKER_USER
ARG DOCKER_UID
ARG DOCKER_GID
ARG DOCKER_PASS
ARG DOCKER_GROUPNAME
ARG HOME=/home/$DOCKER_USER
ENV TZ Asia/Tokyo
#set argments used exclusively in this file

# set user
RUN groupadd -g $DOCKER_GID $DOCKER_GROUPNAME && \
    useradd -d $HOME -m -s /bin/bash -u $DOCKER_UID -g $DOCKER_GID $DOCKER_USER && \
    echo "$DOCKER_USER:$DOCKER_PASS" | chpasswd && \
    echo "$DOCKER_USER ALL=(ALL) ALL" >> /etc/sudoers.d/$DOCKER_USER
USER $DOCKER_USER

WORKDIR $HOME

#after making docker container, do passwd to change your password