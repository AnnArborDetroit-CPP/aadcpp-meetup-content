FROM ubuntu:artful

LABEL maintainer="Jerry Wiltse <jwiltse@carsim.com>"

RUN dpkg --add-architecture i386 \
    && apt-get -qq update \
    && apt-get -qq install -y --no-install-recommends \
       python-dev=2.7.* \
       sudo=1.8.* \
       binutils=2.29.* \
       wget=1.19.* \
       git=1:2.14.* \
       vim=2:8.0.* \
       libc6-dev-i386=2.26-* \
       linux-libc-dev:i386=4.13.* \
       g++-7-multilib=7.2.* \
       libgmp-dev=2:6.1.* \
       libmpfr-dev=3.1.* \
       libmpc-dev=1.0.* \
       libc6-dev=2.26* \
       nasm=2.13.* \
       dh-autoreconf=14 \
       valgrind=1:3.13.* \
       ninja-build=1.7.* \
       libffi-dev=3.2.* \
       libssl-dev=1.0.2* \
       pkg-config=0.29.1-0ubuntu2 \
       ca-certificates \
    && update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-7 100 \
    && update-alternatives --install /usr/bin/c++ c++ /usr/bin/g++-7 100 \
    && rm -rf /var/lib/apt/lists/* \
    && wget --no-check-certificate --quiet https://cmake.org/files/v3.10/cmake-3.10.3-Linux-x86_64.tar.gz \
    && tar -xzf cmake-3.10.3-Linux-x86_64.tar.gz \
    && cp -fR cmake-3.10.3-Linux-x86_64/* /usr \
    && rm -rf cmake-3.10.3-Linux-x86_64 \
    && rm cmake-3.10.3-Linux-x86_64.tar.gz \