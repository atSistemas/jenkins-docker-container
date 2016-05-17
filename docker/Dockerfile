FROM debian:jessie

RUN apt-get update
# Hay formas de generar una imagen más pequeña, esto es académico :P
RUN apt-get -y install wget
RUN apt-get -y install openjdk-7-jdk
RUN apt-get -y install groovy2
RUN apt-get -y install git
RUN apt-get -y install maven2

RUN mkdir /jenkins

RUN mkdir -p /opt/sw/swarm
RUN cd /opt/sw/swarm
RUN wget -O /opt/sw/swarm/swarm-client-2.0-jar-with-dependencies.jar http://repo.jenkins-ci.org/releases/org/jenkins-ci/plugins/swarm-client/2.0/swarm-client-2.0-jar-with-dependencies.jar

ENV JAVA_HOME /usr/lib/jvm/java-7-openjdk-amd64
ENV GROOVY_HOME /usr/share/groovy2
ENV GIT_PATH /usr/bin/git
# Arrancar el esclavo swarm
CMD java -jar /opt/sw/swarm/swarm-client-2.0-jar-with-dependencies.jar -name ${NODE_NAME} -master http://192.168.1.33:1337 -labels esclavo_swarm -t Groovy-1.8.7=$GROOVY_HOME -t default-git=$GIT_PATH
