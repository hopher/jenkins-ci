FROM jenkinsci/blueocean:1.14.0
LABEL maintainer="hopher <565983236@qq.com>"

USER root

#RUN echo http://dl-2.alpinelinux.org/alpine/edge/community/ >> /etc/apk/repositories
RUN apk --no-cache add shadow && usermod -a -G docker jenkins

USER jenkins