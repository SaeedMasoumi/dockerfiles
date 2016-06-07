# Upsource for Centos7

[![](https://badge.imagelayers.io/saeedmasoumi/centos7-upsource:latest.svg)](https://imagelayers.io/?images=saeedmasoumi/centos7-upsource:latest 'Get your own badge on imagelayers.io') [![](https://img.shields.io/badge/upsource-v3.0.4364-blue.svg)](https://www.jetbrains.com/upsource/download/)

This image is based on [centos7](https://hub.docker.com/r/saeedmasoumi/centos7-openjdk8/) with latest version of openjdk8 (jre).

## Usage

To run a container:

```
# sudo docker run -d --name upsource -p 8080:8080 --restart=always saeedmasoumi/centos7-upsource
```

If you want to mount upsource **_backups/data/temp/logs_** files in your host, run this: 


```
# sudo docker run -d --name upsource -v "path/on/host:/var/lib/upsource" -p 8080:8080 --restart=always saeedmasoumi/centos7-upsource
```
