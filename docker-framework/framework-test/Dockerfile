FROM docker.artifactory/docker-framework:latest

MAINTAINER Jainish Shah jainishs@jfrog.com

RUN rm -rf /home/exec/apache-tomcat-8.0.32/webapps/*

ADD war/*.war /home/exec/apache-tomcat-8.0.32/webapps/ROOT.war
CMD /bin/bash -c cd /home/exec; /home/exec/apache-tomcat-8.0.32/bin/catalina.sh run
