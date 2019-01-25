FROM       ubuntu:18.04
MAINTAINER Chia-Wei Chang "https://github.com/rgly"

# To fix delaying package problems, since apt-utils is not installed
# https://github.com/phusion/baseimage-docker/issues/319
RUN apt-get update \
    && apt-get install -y --no-install-recommends apt-utils

RUN apt-get install -y \
    vim cmake git lftp screen wget curl p7zip \
    g++-8 gdb valgrind gperf \
    fish tcsh \
    python3 python3-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Python related tools
RUN curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py \
    && python3 get-pip.py \
    && rm -f get-pip.py \
    && python3 -m pip --no-cache-dir install scipy numpy matplotlib \
    && rm -rf $HOME/.cache/pip

RUN echo 'root:root' | chpasswd \
    && mkdir /root/.ssh
