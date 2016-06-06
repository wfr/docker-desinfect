FROM ubuntu:xenial
MAINTAINER Wolfgang Frisch <wfr@roembden.net>

COPY rootfs/ /
COPY kav /

RUN set -xe \
	&& rm -r /var/kl/bases_rd \
	&& mv /var/kl/bases_rd.orig /var/kl/bases_rd \
	&& apt-get update \
	&& apt-get install -y libc6-i386 lib32ncurses5 lib32stdc++6

WORKDIR /data
