FROM ubuntu:24.04

ARG USER_ID
ARG GROUP_ID

# Install sudo first
RUN apt-get update && apt-get install -y sudo

# Modify the existing 'ubuntu' user:
# 1. Change the group ID (GID)
# 2. Change the user ID (UID) and primary group
# 3. Fix ownership of the home directory (in case IDs changed)
# 4. Add to sudoers
RUN groupmod --gid $GROUP_ID ubuntu && \
    usermod --uid $USER_ID --gid $GROUP_ID ubuntu && \
    chown -R $USER_ID:$GROUP_ID /home/ubuntu && \
    echo 'ubuntu ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# Verify
RUN id ubuntu
USER ubuntu

RUN DEBIAN_FRONTEND=noninteractive sudo apt-get install -y --no-install-recommends tzdata

RUN sudo apt-get update
RUN sudo apt-get install -y \
    gawk \ 
    xz-utils \
    net-tools \
    xterm \
    autoconf \
    libtool \
    less \
    rsync \
    texinfo \
    zlib1g-dev \
    build-essential \ 
    python3 \
    libncurses5-dev \
    git \
    bc \
    vim \
    locales \
    chrpath \
    cpio \
    diffstat \
    lz4 \
    zstd \
    liblz4-tool \
    wget \
    locales-all 

ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8

RUN sudo ln -sf /bin/bash /bin/sh
