FROM saeedmasoumi/centos7-openjdk8
MAINTAINER Saeed Masoumi <s-masoumi@live.com>

# Forked from https://github.com/esycat/docker-upsource/ to make it run with centos

ENV APP_VERSION 2.5
ENV APP_BUILD ${APP_VERSION}.5074
ENV APP_PORT 8080
ENV APP_SUFFIX upsource

ENV APP_DISTFILE upsource-${APP_BUILD}.zip
ENV APP_PREFIX /opt
ENV APP_DIR $APP_PREFIX/$APP_SUFFIX
ENV APP_HOME /var/lib/$APP_SUFFIX

# Install needed packages
RUN yum update -y
RUN yum install -y unzip wget

# preparing home (data) directory and user+group
RUN mkdir -p $APP_HOME
 

# downloading and unpacking the distribution, removing bundled JVMs
WORKDIR $APP_PREFIX
RUN wget -q https://download.jetbrains.com/upsource/$APP_DISTFILE && \
    unzip -q $APP_DISTFILE && \
    rm $APP_DISTFILE && \
    rm -rf $APP_DIR/internal/java && \
    mv Upsource $APP_SUFFIX && \
    chown -R $APP_USER:$APP_USER $APP_DIR

WORKDIR $APP_DIR

RUN bin/upsource.sh configure \
    --backups-dir $APP_HOME/backups \
    --data-dir    $APP_HOME/data \
    --logs-dir    $APP_HOME/log \
    --temp-dir    $APP_HOME/tmp \
    --listen-port $APP_PORT \
    --base-url    http://localhost/

ENTRYPOINT ["bin/upsource.sh"]
CMD ["run"]
EXPOSE $APP_PORT
VOLUME ["$APP_HOME"]