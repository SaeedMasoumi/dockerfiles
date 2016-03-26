dockerfile-centos-openjdk
======================

[![](https://badge.imagelayers.io/saeedmasoumi/centos7-openjdk8:latest.svg)](https://imagelayers.io/?images=saeedmasoumi/centos7-openjdk8:latest 'Get your own badge on imagelayers.io')

A Dockerfile that Produces a centos7-based docker image that will run the latest openjdk8(jre).

To build from source:

```
# sudo docker build -t <username>/centos7-openjdk:8 .
```

To run image from docker hub:
```
# sudo docker run --it --rm --name openjdk8 saeedmasoumi/centos7-openjdk8 java -version
```
