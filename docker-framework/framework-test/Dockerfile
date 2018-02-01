FROM docker.artifactory/docker-framework:latest

MAINTAINER Jainish Shah jainishs@jfrog.com

ADD war/*.war /home/exec/tomcat/webapps/swampup.war

CMD /bin/bash -c cd /home/exec; /home/exec/tomcat/bin/catalina.sh run
