ARG REPOSITORY
ARG CLANG_VERSION=9
FROM ${REPOSITORY}:clang-${CLANG_VERSION}
LABEL maintainer="Felix Thaler <thaler@cscs.ch>"

ENV CLANG_VERSION ${CLANG_VERSION}

RUN cd /tmp && \
    wget -q https://developer.nvidia.com/compute/cuda/10.1/Prod/local_installers/cuda-repo-ubuntu1804-10-1-local-10.1.168-418.67_1.0-1_amd64.deb && \
    dpkg -i cuda-repo-ubuntu1804-10-1-local-10.1.168-418.67_1.0-1_amd64.deb && \
    apt-key add /var/cuda-repo-10-1-local-10.1.168-418.67/7fa2af80.pub && \
    apt-get update -qq && \
    apt-get install -qq -y cuda-compiler-10-1 cuda-libraries-dev-10-1 && \
    rm -rf * && \
    dpkg -r $(dpkg-query -f '${Package}' -W 'cuda-repo-*') && \
    rm -rf /var/lib/apt/lists/*

ENV CUDACXX=/usr/local/cuda-10.1/bin/nvcc
