FROM debian:jessie
MAINTAINER Wolfgang Frisch <wfr@roembden.net>

RUN set -xe \
	&& dpkg --add-architecture i386 \
	&& apt-get update \
	&& apt-get install -y libc6-i386

COPY rootfs/ /
COPY avupdate /

WORKDIR /data

