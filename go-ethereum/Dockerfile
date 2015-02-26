FROM afdudley/base-ethereum:0.1
MAINTAINER Rick Dudley <a.frederick.dudley+docker@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
RUN add-apt-repository ppa:beineri/opt-qt541-trusty -y \
  && apt-get -y update && apt-get install -y go-ethereum

ENTRYPOINT ["/usr/bin/ethereum"]
