# $ docker build -t jenkins-slave-halcon .
# $ docker run -d -P --name jenkins-slave jenkins-slave-halcon
# $ docker exec -it 226c088802b8 bash

FROM openjdk:6b38-jdk

ENV DEBIAN_FRONTEND noninteractive

# Instala SSH
RUN apt-get update && apt-get install -y openssh-server

RUN mkdir /var/run/sshd
#RUN echo 'root:screencast' | chpasswd
#RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Set user jenkins to the image
RUN useradd -m -d /home/jenkins -s /bin/sh jenkins &&\
    echo "jenkins:jenkins" | chpasswd

# SSH login fix. Otherwise user is kicked off after login
#RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

# Instala Ant
#RUN apt-get install ant \
#    && apt-get clean

EXPOSE 22

CMD  ["/usr/sbin/sshd", "-D"]