# docker run -it \
#     -v M2_SRC:/home/user/M2 \
#     -u user \
#     -w /home/user \
#     --name m2build \
#     m2env /bin/bash

FROM fedora:23
MAINTAINER Lars Kastner <lars.kastner@yahoo.dk>

# M2 build context from M2 repo
RUN dnf -y install autoconf bison boost-devel cddlib-devel emacs factory-devel \
   fakeroot flex gc-devel gcc-c++ gdbm-devel git glpk-devel gmp-devel \
   kernel-devel lapack-devel libatomic_ops-devel libfac-devel \
   libgfortran-static libtool libxml2-devel mpfr-devel mpir-devel ncurses-devel \
   ntl-devel pari-devel patch readline-devel rpm-build rpm-sign rpmdevtools \
   subversion strace

# Some standard tools, that are provided by Fedora, but not in the docker version:
RUN dnf -y install make

# Pass the UID and GID of your user, otherwise you will have permission issues.
ENV UID 1001
ENV GID 1001

RUN useradd -m user -u $UID
RUN mkdir /home/user/M2; \
    chown -R user:user /home/user/M2
VOLUME ["/home/user/M2"]

# Set working directory and login user.
WORKDIR /home/user/M2
USER user

