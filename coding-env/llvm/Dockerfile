FROM       rgly/coding-env
MAINTAINER Chia-Wei Chang "https://github.com/rgly"

RUN apt-get update
# LLVM-based coding utils
RUN apt-get install -y clang-tools llvm-6.0 clang-tidy clang-format
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
