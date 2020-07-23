 
FROM ubuntu:xenial

USER root
WORKDIR /root
 
SHELL [ "/bin/bash", "-c"]
 
ENV DEBIAN_FRONTEND noninteractive
 
RUN apt-get -qq -y update && \
	apt-get -qq -y install  \
		wget \
 		apt-transport-https
 

 
RUN printf 'deb [trusted=yes] https://runsafesecurity.jfrog.io/artifactory/debian  stretch main' >> /etc/apt/sources.list.d/nginx.list
 

 
RUN wget -qO - https://runsafesecurity.jfrog.io/artifactory/api/gpg/key/public | apt-key add -
 
RUN apt-get -qq -y update && \
	apt-get -qq -y install  \
		 nginx
 

 

 

 

 

 

 

 

 

 

 

 

 

 
EXPOSE 8081

ENV DEBIAN_FRONTEND newt
 
CMD [ ""nginx", "-g", "daemon off;"" ]