# docker run -it \
#     -v M2_SRC:/home/user/M2 \
#     --name m2build \
#     m2env /bin/bash

FROM ubuntu:16.04
MAINTAINER Lars Kastner <lars.kastner@yahoo.dk>

RUN apt-get update
RUN apt-get install -yq keyboard-configuration
RUN mkdir /build



# M2 stuff
RUN apt-get install -yq autoconf bison emacs flex g++ gcc gfortran libc6-dev libcdd-dev libatomic-ops-dev libgc-dev libgdbm-dev libglpk-dev liblapack-dev libmpfr-dev libncurses-dev libncurses5-dev libntl-dev libpari-dev libreadline-dev libxml2-dev liblzma-dev libz-dev make openssh-server patch subversion time unzip xbase-clients zlib1g-dev libtool pkg-config libmpc-dev

# Pass the UID and GID of your user, otherwise you will have permission issues.
WORKDIR /
ENV NUMPROC 3

RUN ln -s /bin/sed /usr/bin/sed


# Installing topcom
WORKDIR /build
ENV TOPCOM_VERSION 0.17.8
RUN wget http://www.rambau.wm.uni-bayreuth.de/Software/TOPCOM-$TOPCOM_VERSION.tar.gz;\
   tar xzf TOPCOM-$TOPCOM_VERSION.tar.gz
WORKDIR /build/topcom-$TOPCOM_VERSION
RUN ./configure;\
   make -j$NUMPROC;\
   make install;\
   make clean


# Installing cohomcalg
WORKDIR /build
ENV COHOMCALG_VERSION 031b
RUN wget http://wwwth.mppmu.mpg.de/members/bjurke/cohomcalg/content/cohomCalg-031b.zip;\
   mkdir cohomcalg;\
   unzip cohomCalg-$COHOMCALG_VERSION.zip -d cohomcalg
WORKDIR /build/cohomcalg
RUN make -j$NUMPROC;\
   ln -s /build/cohomcalg/bin/cohomcalg /usr/local/bin/cohomcalg


# Installing lrslib
WORKDIR /build
ENV LRS_VERSION 062
RUN wget http://cgm.cs.mcgill.ca/~avis/C/lrslib/archive/lrslib-$LRS_VERSION.tar.gz;\
   tar xzf lrslib-$LRS_VERSION.tar.gz
WORKDIR /build/lrslib-$LRS_VERSION
RUN make -j$NUMPROC;\
   make install;\
   make clean


# Installing cddlib
WORKDIR /build
ENV CDD_VERSION 094h
RUN wget ftp://ftp.math.ethz.ch/users/fukudak/cdd/cddlib-$CDD_VERSION.tar.gz;\
   tar xzf cddlib-$CDD_VERSION.tar.gz
WORKDIR /build/cddlib-$CDD_VERSION
RUN ./configure;\
   make -j$NUMPROC;\
   make install;\
   make clean


