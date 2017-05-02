# $ docker build -t jenkins-slave-halcon .
# $ docker run -d -P --name jenkins-slave jenkins-slave-halcon
# $ docker exec -it 226c088802b8 bash

FROM openjdk:7u121-jdk

ENV DEBIAN_FRONTEND noninteractive

# Instalando SSH
RUN apt-get update && apt-get install -y openssh-server && mkdir /var/run/sshd

# Creando usuario
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

WORKDIR /home/jenkins

EXPOSE 22

CMD  ["/usr/sbin/sshd", "-D"]