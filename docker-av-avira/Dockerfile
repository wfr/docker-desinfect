FROM ubuntu:xenial
MAINTAINER Wolfgang Frisch <wfr@roembden.net>

COPY rootfs/ /
COPY avupdate /

RUN set -xe \
	&& apt-get update \
	&& apt-get install libc6-i386

WORKDIR /data

