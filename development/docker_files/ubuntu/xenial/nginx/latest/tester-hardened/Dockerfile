 
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
		apt-transport-https
 

 
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

ENV ALKEMIST_LICENSE_KEY=3e4125f015d6428dba2c83c8ee9a58c0-fbb177fdc0f320e938881dfaaaa27dd5-89a51b8e753505e62649120223e7c042-213949fc67f59b1889b8aac60f23a9v2
ENV LFR_ROOT_PATH="/opt/alkemist/lfr"
 
RUN sudo ln -s cc ${LFR_ROOT_PATH}/scripts/x86_64-linux-gnu-gcc \
	&& sudo ln -s cc ${LFR_ROOT_PATH}/scripts/x86_64-linux-gnu-g++
 
RUN sudo apt-get -y build-dep nginx
 
RUN lfr-helper apt-get source --compile nginx
 
RUN sudo dpkg -i *.deb || sudo apt-get -y install -f
 
RUN ldd /usr/sbin/nginx | grep lfr
 
RUN sudo apt-get -qq -y update  && \
	apt-get -qq -y install  \
		git
RUN sudo git clone https://github.com/nginx/nginx-tests
 
RUN mkdir /root/test-output
RUN chown -R nginx:nginx /root
USER nginx
 
ENV DEBIAN_FRONTEND newt
 
CMD [ "/bin/bash" ]