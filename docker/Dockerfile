FROM ubuntu:latest

ARG BASE_PATH=/var/spool/apt-mirror

RUN set -ex &&\
    \ 
    apt-get -qq update &&\
    apt-get -y --no-install-recommends -qq install wget curl git ca-certificates &&\
    rm -rf /var/lib/apt/lists

ADD apt-mirror /usr/local/bin/apt-mirror
ADD mirror.list /etc/apt/mirror.list

RUN set -ex &&\
    \
    chmod 755 /usr/local/bin/apt-mirror &&\
    chmod 644 /etc/apt/mirror.list &&\
    mkdir -p ${BASE_PATH}/mirror &&\
    mkdir -p ${BASE_PATH}/skel &&\
    mkdir -p ${BASE_PATH}/var

ENTRYPOINT apt-mirror