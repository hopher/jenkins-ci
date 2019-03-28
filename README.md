# Jenkins 持续集成

用 Docker 容器服务的方式搭建 `jenkinsci` 持续集成环境, 易于维护、升级。

本环境基于 `jenkinsci/blueocean:1.14.0` 镜像，Linux版本: `Alpine Linux 3.9`

## xx

phpDox 假设配置是用来生成 api 文档


PHP_CodeSniffer  代码嗅探器


## 初始化 AdminPassword

```
cat /var/jenkins_home/secrets/initialAdminPassword
```

相关概念

- Pipeline 是一套插件，支持实现和集成到Jenkins中的连续交付管道。

- Jenkinsfile  Jenkins Pipeline提供了一组可扩展的工具，用于“作为代码”对简单到复杂的交付管道进行建模。
                然后写在 Jenkinsfile 里面



Pipeline script from SCM (Source Code Master) 选项

    此选项指示Jenkins从源代码管理（SCM）仓库获取你的流水线， 这里的仓库就是你clone到本地的Git仓库


示例:
https://github.com/jenkins-docs/simple-java-maven-app
https://github.com/jenkins-docs/building-a-multibranch-pipeline-project
https://github.com/jenkins-docs/simple-node-js-react-npm-app



## 权限问题解决

> Got permission denied while trying to connect to the Docker daemon socket  
> **解决**: https://github.com/chrootLogin/docker-nextcloud/issues/3

将用户jenkins，添加到组 docker

```
sudo usermod -a -G docker jenkins
```

**dockerfile文件**
```
USER root
#RUN echo http://dl-2.alpinelinux.org/alpine/edge/community/ >> /etc/apk/repositories
RUN apk --no-cache add shadow && usermod -a -G docker jenkins
USER jenkins
```


## 参考资料

- [自动化部署之jenkins及简介](https://www.cnblogs.com/jimmy-xuli/p/9020825.html)
- [Jenkins官网](https://jenkins.io/)
- [Jenkins官网 - 中文](https://jenkins.io/zh/)
- [PHP 集成](https://jenkins.io/solutions/php/)
- [使用 Jenkins 自动化发布 PHP 项目](https://www.centos.bz/2018/05/使用-jenkins-自动化发布-php-项目/)
- [Jenkins发布PHP代码](https://www.cnblogs.com/jimmy-xuli/p/9072015.html)
- [Docker Compose Build Step Plugin](https://wiki.jenkins.io/display/JENKINS/Docker+Compose+Build+Step+Plugin)
- [Github 参考项目 istresearch/jenkins ](https://github.com/istresearch/jenkins)
- [Jenkins Mounts the docker socket 权限问题解决](https://github.com/chrootLogin/docker-nextcloud/issues/3)