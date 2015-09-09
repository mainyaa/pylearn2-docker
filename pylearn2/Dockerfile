FROM ubuntu:14.04

MAINTAINER Traun Leyden <traun.leyden@gmail.com>
MAINTAINER Kazuyuki Mori <mainya@gmail.com>

# Get latest ubuntu packages
RUN apt-get update

# Dependencies
RUN apt-get install -y build-essential gfortran g++ libopenblas-dev git curl

# Python
RUN apt-get install -y python python-numpy python-scipy python-dev python-pip python-nose python-yaml python-imaging python-matplotlib

# install Theano (development version)
RUN cd /opt && git clone git://github.com/Theano/Theano.git
RUN cd /opt/Theano && python setup.py develop

# install Pylearn2 (development version)
RUN cd /opt && git clone git://github.com/lisa-lab/pylearn2.git
RUN cd /opt/pylearn2 && python setup.py develop

# set Data path
ENV PYLEARN2_DATA_PATH /opt/data

# set Scripts path
ENV PATH /opt/pylearn2/pylearn2/scripts:$PATH
ENV PATH /usr/local/cuda/bin:$PATH
VOLUME /usr/local/cuda
WORKDIR /opt/pylearn2/pylearn2/scripts

CMD [ "/bin/bash" ]
# docker run -it mainyaa/pylearn2 bash
# docker run -it --privileged -v /usr/lib64/libcuda.so:/usr/lib64/libcuda.so -v /usr/lib64/libcuda.so.1:/usr/lib64/libcuda.so.1 -v /usr/local/cuda:/usr/local/cuda mainyaa/pylearn2 bash
# python datasets/download_mnist.py


