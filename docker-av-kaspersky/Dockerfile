FROM osrf/ubuntu_32bit:xenial
MAINTAINER Wolfgang Frisch <wfr@roembden.net>

COPY rootfs/ /
COPY kav /

RUN set -xe \
    && rm -r /var/kl/bases_rd \
    && mv /var/kl/bases_rd.orig /var/kl/bases_rd

WORKDIR /data
