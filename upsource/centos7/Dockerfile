FROM saeedmasoumi/centos7-openjdk8
MAINTAINER Saeed Masoumi <s-masoumi@live.com>

# Forked from https://github.com/esycat/docker-upsource/ to make it run with centos

ENV APP_VERSION 3.0
ENV APP_BUILD ${APP_VERSION}.4364
ENV APP_PORT 8080
ENV APP_FOLDER upsource

ENV APP_DISTFILE upsource-${APP_BUILD}.zip
ENV APP_DIR /opt/$APP_FOLDER
ENV APP_HOME /var/lib/$APP_FOLDER

# Install needed packages
RUN yum update -y
RUN yum install -y unzip wget

# Set limits for upsource
RUN echo '* - memlock unlimited' >> /etc/security/limits.conf
RUN echo '* - nofile 100000' >> /etc/security/limits.conf
RUN echo '* - nproc 32768' >> /etc/security/limits.conf
RUN echo '* - as unlimited' >> /etc/security/limits.conf

# preparing home (data) directory and user+group
RUN mkdir -p $APP_HOME
RUN mkdir -p $APP_DIR

# downloading and unpacking the distribution, removing bundled JVMs
WORKDIR $APP_DIR
RUN wget -q https://download.jetbrains.com/upsource/$APP_DISTFILE && \
    unzip -q $APP_DISTFILE && \
    rm $APP_DISTFILE && \
    chown -R $APP_USER:$APP_USER $APP_DIR

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