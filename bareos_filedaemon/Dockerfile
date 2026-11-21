# Dockerfile generated using karavomarangos - https://git.windmaker.net/a-castellano/karavomarangos
ARG BASE_IMAGE=ubuntu:resolute
FROM $BASE_IMAGE

MAINTAINER Álvaro Castellano Vela <alvaro@windmaker.net>


RUN \
  apt-get update -qq && \
  apt-get install -qq -o=Dpkg::Use-Pty=0 -y gnupg ca-certificates wget --no-install-recommends && \
  wget -qO- https://download.bareos.org/current/xUbuntu_26.04/bareos-keyring.gpg >> /etc/apt/keyrings/bareos.gpg && \
  echo "Types: deb deb-src " > /etc/apt/sources.list.d/bareos.sources && \
  echo "URIs: https://download.bareos.org/current/xUbuntu_26.04 " >> /etc/apt/sources.list.d/bareos.sources && \
  echo "Suites: / " >> /etc/apt/sources.list.d/bareos.sources && \
  echo "Architectures: amd64 " >> /etc/apt/sources.list.d/bareos.sources && \
  echo "Signed-By: /etc/apt/keyrings/bareos.gpg" >> /etc/apt/sources.list.d/bareos.sources && \
  apt-get update -qq && \
  apt-get install -qq -o=Dpkg::Use-Pty=0 -y \
    bareos-filedaemon=25.1.3~pre24.0e7742c39-128 \
    --no-install-recommends && \
  apt-get purge -qq -o=Dpkg::Use-Pty=0 -y gnupg wget ca-certificates && \
  apt-get autoremove -qq -o=Dpkg::Use-Pty=0 -y && \
  apt-get autoclean -qq -o=Dpkg::Use-Pty=0 -y && \
  rm -rf /var/lib/apt/lists/* 

EXPOSE 9102 
CMD ["/usr/sbin/bareos-fd", "-f"]