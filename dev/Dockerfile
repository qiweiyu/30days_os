FROM ubuntu

RUN set -ex && \
    apt-get update && \
    apt-get --no-install-recommends --yes install \
    make \
    nasm \
    mtools

COPY ./scripts/* /bin/
