 
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
 

 
RUN printf 'deb [trusted=yes] https://runsafesecurity.jfrog.io/artifactory/debian  xenial main' >> /etc/apt/sources.list.d/alkemist-lfr.list
 
RUN printf 'deb-src https://nginx.org/packages/ubuntu/ xenial nginx' >> /etc/apt/sources.list
RUN sed -i 's/# deb-src/deb-src/g' /etc/apt/sources.list
 

 
RUN wget -qO - https://runsafesecurity.jfrog.io/artifactory/api/gpg/key/public | sudo apt-key add -
RUN wget -qO - https://nginx.org/keys/nginx_signing.key | sudo apt-key add -
 
RUN apt-get -qq -y update && \
	apt-get -qq -y install  \
		alkemist-lfr
 
RUN sudo apt-get -y upgrade  \
		binutils
 

 

 

 

 

 

 

 

 

 

 

 
ENV DEBIAN_FRONTEND newt
 
CMD [ "/bin/bash" ]