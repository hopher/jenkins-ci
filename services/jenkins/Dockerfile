FROM jenkinsci/blueocean:1.14.0
LABEL maintainer="hopher <565983236@qq.com>"

# 设置安装源镜像
ENV MIRROR_SOURCE=tencent
COPY ./mirrors/$MIRROR_SOURCE/alpine/v3.9 /etc/apk/repositories

USER root

#RUN echo http://dl-2.alpinelinux.org/alpine/edge/community/ >> /etc/apk/repositories
RUN apk --no-cache add shadow && usermod -a -G docker jenkins

USER jenkins