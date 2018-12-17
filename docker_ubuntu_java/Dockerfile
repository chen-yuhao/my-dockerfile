# 引入基础镜像
FROM ubuntu:16.04

# 运行shell脚本，更换安装源
COPY run.sh /
RUN apt-get install bash -y \
&& /bin/sh run.sh \
# 安装必要软件
&& apt-get update && apt-get install vim -y \
&& apt-get install dos2unix

# 安装jdk
RUN mkdir /home/java
ADD jdk1.8.0_151/ /home/java/jdk1.8.0_151

# 安装maven
RUN mkdir /var/tmp/maven
ADD apache-maven-3.5.2/ /var/tmp/maven 

# mvn启动文件转unix格式
RUN dos2unix /var/tmp/maven/bin/*

# 配置环境变量
ENV MAVEN_HOME=/var/tmp/maven
ENV PATH=${PATH}:${MAVEN_HOME}/bin
ENV JAVA_HOME=/home/java/jdk1.8.0_151
ENV JRE_HOME=/home/java/jdk1.8.0_151/jre
ENV PATH=$JAVA_HOME/bin/:$JAVA_HOME=/jre/bin:$PATH:$HOME/bin


