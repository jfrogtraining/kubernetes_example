FROM docker.artifactory/ubuntu:14.04

MAINTAINER Jainish Shah jainishs@jfrog.com

RUN mkdir -p /home/exec/jdk8 /home/exec/tomcat

COPY jdk/jdk-8-linux-x64.tar.gz /home/exec/
RUN cd /home/exec/ && tar -xvf /home/exec/jdk-8-linux-x64.tar.gz
ENV JAVA_HOME=/home/exec/jdk1.8.0_91
#RUN sed "/securerandom.source=/{s/file:\/dev\/random/file:\/dev\/urandom/}" /home/exec/jdk8/jre/lib/security/java.security -i

COPY tomcat/apache-tomcat-8.tar.gz /home/exec/tomcat
RUN cd /home/exec/ && tar -xvf /home/exec/tomcat/apache-tomcat-8.tar.gz
ADD tomcat/server.xml /home/exec/apache-tomcat-8.0.32/conf/server.xml
ENV CATALINA_HOME=/home/exec/apache-tomcat-8.0.32
ENV TEST_ENV=2

CMD /bin/bash -c cd /home/exec; /home/exec/apache-tomcat-8.0.32/bin/catalina.sh run