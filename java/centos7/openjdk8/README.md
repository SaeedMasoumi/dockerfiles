dockerfile-centos-openjdk
======================

A Dockerfile that Produces a centos7-based docker image that will run the latest openjdk8.

To build from source:

```
# sudo docker build -t <username>/centos7-openjdk:8 .
```

To run image from docker hub:
```
# sudo docker run --name openjdk8 saeedmasoumi/centos7-openjdk8
```