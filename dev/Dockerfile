FROM ubuntu

RUN set -ex && \
    apt-get update && \
    apt-get --no-install-recommends --yes install \
    gcc \
    make \
    nasm \
    mtools

COPY ./scripts/* /bin/
