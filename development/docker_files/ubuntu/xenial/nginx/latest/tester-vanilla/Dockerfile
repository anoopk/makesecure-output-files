 
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
 

 
 
RUN printf 'deb-src https://nginx.org/packages/ubuntu/ xenial nginx' >> /etc/apt/sources.list
RUN sed -i 's/# deb-src/deb-src/g' /etc/apt/sources.list
 

 

 
RUN apt-get -qq -y update 
 
RUN sudo apt-get -y upgrade  \
		binutils
 

 
RUN sudo apt-get -y build-dep nginx
 
RUN apt-get source --compile nginx
 
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