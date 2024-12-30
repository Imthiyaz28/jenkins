FROM ubuntu:24.04
ARG PASSWORD
RUN apt install -y openssh-server #install openssh server

RUN useradd -m remote_user #creaing a user with default home directory 
RUN echo "remote_user:$PASSWORD" | chpasswd #updating the password
RUN mkdir -p /home/remote_user/.ssh
RUN chmod 700 /home/remote_user/.ssh
RUN mkdir -p -m0755 /var/run/sshd

