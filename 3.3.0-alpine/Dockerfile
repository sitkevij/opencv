FROM alpine:3.5

######## changelog
# 01 [x] test new apk adds: docker run --rm -it alpine sh, docker run --rm -it sitkevij/opencv python3 -c 'print("Hello World")'
# 02 [x] linux/auxvec.h: No such file or directory - https://github.com/mirage/mirage-block-unix/issues/45
# 03 [x] alpine-sdk -> build-base
# 04 [ ] migrate @testing to @community
# 05 [x] alpine:3.5 -> alpine:3.6
# 06 [x] python3-dev -> python   
# 07 [x] libjasper -> libjasper-dev 
########

MAINTAINER Julian Sitkevich <sitkevij@gmail.com>

RUN echo -e '@edge http://nl.alpinelinux.org/alpine/edge/main\n@testing http://nl.alpinelinux.org/alpine/edge/testing' >> /etc/apk/repositories \
  && apk update && apk add ca-certificates && update-ca-certificates \
  && apk upgrade \
  && apk add --virtual build-dependencies --no-cache \ 
    openssl \
    build-base \
    linux-headers \ 
    unzip \ 
    wget \ 
    cmake \ 
    git \ 
    gnutls \
    python \
    # python3-dev \
    libtbb@testing \
    libtbb-dev@testing \
    libjpeg \
    libjpeg-turbo-dev \
    libpng-dev \ 
    tiff-dev \
    libjasper \
  && cd \
    && wget https://github.com/Itseez/opencv/archive/3.3.0.zip \
    && unzip 3.3.0.zip \
    && cd opencv-3.3.0 \
    && mkdir build \
    && cd build \
    && cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D WITH_FFMPEG=NO -D WITH_IPP=NO -D WITH_OPENEXR=NO ..  \
    && make -j3 \
    && make install \
    && cd \
    && rm 3.3.0.zip \
    && rm -rf /var/cache/apk/*
    && apk del build-dependencies
