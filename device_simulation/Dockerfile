FROM ubuntu:20.04

LABEL description="Device simulation module" 

# Install all necessary software
RUN apt update \
    && apt install -y git make gcc g++ libsctp-dev libsctp-dev lksctp-tools iproute2 wget \
    && wget https://github.com/Kitware/CMake/releases/download/v3.24.1/cmake-3.24.1-linux-x86_64.sh -O cmake_installer.sh \
    && chmod +x cmake_installer.sh \
    && ./cmake_installer.sh --skip-license \
    && git clone -b master -j `nproc` https://github.com/aligungr/UERANSIM \
    && cd ./UERANSIM \
    && ln -s /usr/bin/bash /bin/bash \
    && ln -s /usr/bin/bash /bin/sh \
    && make -j4 \
    && cd / \
    && git clone https://github.com/Pa-Paolo/Thesis_code \
    && export DEBIAN_FRONTEND=noninteractive \
    && ln -fs /usr/share/zoneinfo/Europe/Rome /etc/localtime \
    && apt-get install -y tzdata \
    && dpkg-reconfigure --frontend noninteractive tzdata \
    && apt -y install python3.9 python3-pip \
    && cd Thesis_code/device_simulation \
    && pip install -r requirements.txt \
    && python3 config_duplicator.py -d \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && python3 config_duplicator.py -d

# Set working dir
WORKDIR /Thesis_code/device_simulation
