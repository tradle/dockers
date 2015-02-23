FROM ubuntu:14.04
MAINTAINER Rick Dudley <a.frederick.dudley+docker@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get upgrade -qy software-properties-common \
  # Ethereum PPA
  && add-apt-repository ppa:ethereum/ethereum \
  && add-apt-repository ppa:ethereum/ethereum-dev
RUN apt-get update && apt-get install -qy libcryptopp-dev libmicrohttpd-dev \
  libethereum ethereum 

ENTRYPOINT ["/usr/bin/eth"]
