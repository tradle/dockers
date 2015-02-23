FROM ubuntu:14.04
MAINTAINER Rick Dudley <a.frederick.dudley+docker@gmail.com>
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get -qy upgrade && apt-get -qy install autoconf git \
  cabal-install libtool cmake libncurses5-dev curl libgmp10-dev zlib1g-dev \
  libxen-dev

# set the locale (fixes this https://github.com/haskell/cabal/issues/1883)
ENV LANG=en_US.UTF-8
RUN locale-gen en_US.UTF-8 && update-locale LANG=en_US.utf-8 && cabal update \
  && git clone http://github.com/galoisinc/HaLVM.git --recursive
RUN cd HaLVM && autoconf && ./configure --enable-gmp --prefix /opt/HaLVM
RUN cd HaLVM && make && make install
ENV PATH=/opt/HaLVM/bin:$PATH
# scripts in /opt/HaLVM assume /bin/sh is bash :(
RUN rm /bin/sh && ln -s /bin/bash /bin/sh \
  && git clone http://github.com/GaloisInc/HaNS \
  && git clone http://github.com/GaloisInc/network-hans \
  && git clone http://github.com/acw/HTTP \
  && halvm-cabal update && halvm-cabal install -j1 cereal fingertree \
  monadLib random mtl parsec network-uri \
  && for d in HaNS network-hans HTTP ; do cd $d ; \
  halvm-cabal configure -f HaLVM && halvm-cabal build && halvm-cabal copy \
  && halvm-cabal register ; cd .. ; done \
  && rm /bin/sh && ln -s /bin/dash /bin/sh

ENTRYPOINT ["/bin/bash"]
