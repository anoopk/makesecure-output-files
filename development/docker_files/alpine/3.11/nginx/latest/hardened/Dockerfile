 
FROM runsafesecurity-docker-alkemist-lfr.jfrog.io/alpine:3.11 AS lfr-files
FROM alpine:3.11

USER root
WORKDIR /root
 
RUN apk add --no-cache --upgrade bash
 
ENV LFR_ROOT_PATH=/lfr
COPY --from=lfr-files /usr/src/lfr/ ${LFR_ROOT_PATH} 

 

 

 

 

 

 
RUN apk update
RUN apk add git alpine-sdk
 

 
RUN adduser -D packager && addgroup packager abuild \
	&& mkdir -p /var/cache/distfiles \
	&& chmod a+w /var/cache/distfiles \
	&& mkdir /root/data \
	&& chown -R packager:packager /root \
	&& echo "packager ALL=(ALL) ALL" >> /etc/sudoers 

USER packager
RUN git config --global user.name "Test Name"
RUN git config --global user.email "test@test.com"
WORKDIR /root/data
RUN git clone git://git.alpinelinux.org/aports.git 

RUN abuild-keygen -a -i 

 

 
RUN cd aports/main/nginx \
	&& ${LFR_ROOT_PATH}/scripts/lfr-helper.sh abuild checksum && abuild -r
 

USER root 

 

 

 

 

 

