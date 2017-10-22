# opencv
OpenCV Docker

There are two ways to run this opencv Docker images:

## 1. Pull from Docker Hub

- [opencv 3.3.0-alpine/latest](https://github.com/sitkevij/opencv/tree/master/3.3.0-alpine)
  - `docker pull sitkevij/opencv` OR `docker pull sitkevij/opencv:3.3.0-alpine`

## 2. Building from source
```
$ git clone https://github.com/sitkevij/opencv.git && \
cd opencv && \
chmod a+x build-arg.sh && \
./build-arg.sh sitkevij "opencv:3.3.0-alpine:3.5" && \
docker run --rm sitkevij/opencv:3.3.0-alpine
```

## opencv Build Options

- Reference https://github.com/opencv/opencv/blob/master/CMakeLists.txt
