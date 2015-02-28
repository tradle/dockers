FROM afdudley/baseimage
MAINTAINER Rick Dudley <a.frederick.dudley+docker@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get upgrade -qy software-properties-common \
  # Ethereum PPA
  && add-apt-repository ppa:ethereum/ethereum -y \
  && add-apt-repository ppa:ethereum/ethereum-dev -y
