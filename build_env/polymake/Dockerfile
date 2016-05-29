# docker run -it \
#     -v polymake_SRC:/home/user/polymake \
#     --name m2build \
#     build_env/m2 /bin/bash

FROM fedora:23
MAINTAINER Lars Kastner <lars.kastner@yahoo.dk>

# polymake build context
RUN dnf -y install autoconf bison boost-devel cddlib-devel emacs factory-devel \
   fakeroot flex gc-devel gcc-c++ gdbm-devel git glpk-devel gmp-devel \
   kernel-devel lapack-devel libatomic_ops-devel libfac-devel \
   libgfortran-static libtool libxml2-devel mpfr-devel mpir-devel ncurses-devel \
   ntl-devel pari-devel patch readline-devel rpm-build rpm-sign rpmdevtools \
   subversion strace

# Some standard tools, that are provided by Fedora, but not in the docker version:
RUN dnf -y install make

RUN useradd -m user
RUN mkdir /home/user/polymake; \
    chown -R user:user /home/user/polymake


