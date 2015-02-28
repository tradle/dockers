FROM afdudley/base-ethereum:pbi
MAINTAINER Rick Dudley <a.frederick.dudley+docker@gmail.com>
ENV DEBIAN_FRONTEND noninteractive
RUN apt-get update && apt-get install -qy libcryptopp-dev libmicrohttpd-dev \
  libethereum ethereum 

ENTRYPOINT ["/usr/bin/eth"]
