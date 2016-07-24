# docker run -it \
#     -v M2_SRC:/home/user/M2 \
#     --name m2build \
#     m2env /bin/bash

FROM ubuntu:16.04
MAINTAINER Lars Kastner <lars.kastner@yahoo.dk>

RUN apt-get update
RUN apt-get install -yq keyboard-configuration
RUN apt-get install -yq polymake

# M2 stuff
RUN apt-get install -yq autoconf bison emacs flex g++ gcc gfortran libc6-dev libcdd-dev libatomic-ops-dev libgc-dev libgdbm-dev libglpk-dev liblapack-dev libmpfr-dev libncurses-dev libncurses5-dev libntl-dev libpari-dev libreadline-dev libxml2-dev liblzma-dev libz-dev make openssh-server patch subversion time unzip xbase-clients zlib1g-dev libtool pkg-config libmpc-dev

# Pass the UID and GID of your user, otherwise you will have permission issues.
ENV UID 1000
ENV GID 1000

RUN useradd -m user -u $UID
RUN mkdir /home/user/M2; \
    chown -R user:user /home/user/M2

RUN ln -s /bin/sed /usr/bin/sed

# Set working directory and login user.
WORKDIR /home/user/M2
USER user
