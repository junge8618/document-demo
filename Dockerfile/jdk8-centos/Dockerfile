#jdk8-centos
#1.指定基础镜像，并且必须是第一条指令
FROM centos:latest

#2.指明该镜像的作者和其电子邮件
MAINTAINER junge8618 "513851613@qq.com"

#3.在构建镜像时，指定镜像的工作目录，之后的命令都是基于此工作目录，如果不存在，则会创建目录
WORKDIR /usr/local/java

RUN mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup

#4.将一些安装包复制到镜像中，语法：ADD/COPY <src>... <dest>
## ADD与COPY的区别：ADD复制并解压，COPY仅复制
ADD jdk-8u131-linux-x64.tar.gz /usr/local/java

#5.更新CentOS的软件源为阿里云
COPY Centos-8.repo /etc/yum.repos.d/CentOS-Base.repo

#6.运行指定的命令
RUN yum install -y wget

#7.配置环境变量
ENV JAVA_HOME=/usr/local/java/jdk1.8.0_131
ENV CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH=$JAVA_HOME/bin:$PATH

#容器启动时需要执行的命令
#CMD ["java","-version"]