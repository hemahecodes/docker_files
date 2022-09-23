
# Copyright 2022 Nostrum Biodiscovery

# modified Helena Martin
# 14-09-2022

FROM centos:7
MAINTAINER Helena Martín

RUN yum -y install epel-release && yum -y update &&\
 yum -y install gcc gcc-c++ make git  cppunit cppunit-devel wget popt popt-devel curl zip unzip\
 numpy python-configparser openbabel openbabel-devel python-openbabel python-pip &&\
 yum clean all

RUN git clone https://github.com/CBDD/rDock.git rDock

ENV RBT_FILE rDock
ENV RBT_ROOT /rDock
ENV LD_LIBRARY_PATH $LD_LIBRARY_PATH:/rDock/lib
ENV PATH $PATH:/rDock/bin


WORKDIR /rDock/build

RUN make linux-g++-64 && make clean

RUN useradd -m -s /bin/bash -G 0 rdock
USER rdock
WORKDIR /home/rdock

LABEL maintainer=helena.martin@nostrumbiodiscovery.com \
      description="rDock Docker container" \
      gpu=false \
      moduleclass=bio
