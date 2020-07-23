 
FROM ubuntu:xenial

USER root
WORKDIR /root
 

SHELL [ "/bin/bash", "-c"]
 
ENV DEBIAN_FRONTEND noninteractive
 
RUN apt-get -qq -y update && \
	apt-get -qq -y install  \
		sudo \
		wget \
		build-essential \
		apt-transport-https \
		git
 

 
 
RUN printf 'deb-src https://nginx.org/packages/ubuntu/ xenial nginx' >> /etc/apt/sources.list
RUN sed -i 's/# deb-src/deb-src/g' /etc/apt/sources.list
 

 

 
RUN apt-get -qq -y update 
 
RUN sudo apt-get -y upgrade  \
		binutils
 

 

 

 

 

 

 

 

 

 

 

 
ENV DEBIAN_FRONTEND newt
 
CMD [ "/bin/bash" ]