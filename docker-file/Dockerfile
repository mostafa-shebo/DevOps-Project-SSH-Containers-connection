FROM ubuntu
RUN apt-get update && \
    apt-get install -y openssh-server vim && \
    service ssh start
WORKDIR /etc/ssh
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]
