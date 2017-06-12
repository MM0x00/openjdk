# openjdk 在线实验环境

## 软件简介

OpenJDK（开放Java开发工具包）是Java Platform，Standard Edition（Java SE）的免费开源实现。OpenJDK是Java SE自第7版以来的官方参考实现。

所属类别是编程语言

特点:

OpenJDK可以运行在其他系统上，特别是那些基于PowerPC的机器上

## 软件官网

http://openjdk.java.net/

## Dockerfile 使用方法

使用此映像的最简单的方法是将Java容器用作构建和运行时环境。在你的Dockerfile写作中，按照以下的方式编写和运行你的项目：
```
FROM openjdk:7
COPY . /usr/src/myapp
WORKDIR /usr/src/myapp
RUN javac Main.java
CMD ["java", "Main"]
```
然后，您可以运行并构建Docker映像：
```
$ docker build -t my-java-app .
$ docker run -it --rm --name my-running-app my-java-app
```
在Docker容器中编译你的应用程序

有可能在容器内运行应用程序是不合适的。要编译，而不是在Docker实例中运行您的应用程序，您可以编写以下内容：
```
$ docker run --rm -v "$PWD":/usr/src/myapp -w /usr/src/myapp openjdk:7 javac Main.java
```
这会将当前目录作为卷添加到容器中，将工作目录设置为卷，并运行该命令javac Main.java，该命令将使Java编译代码Main.java并输出Java类文件Main.class。

## 资源链接

- http://openjdk.java.net/
