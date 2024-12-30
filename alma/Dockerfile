FROM almalinux/8-base
ARG PASSWORD=12345
#RUN dnf update -y
RUN dnf install -y openssh-server unzip mysql #install openssh server
#RUN dnf install -y mysql
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && \
    unzip awscliv2.zip && \
    ./aws/install
RUN useradd -m remote_user #creaing a user with default home directory 
RUN echo "remote_user:$PASSWORD" | chpasswd #updating the password
RUN mkdir -p /home/remote_user/.ssh
RUN chmod 700 /home/remote_user/.ssh
RUN mkdir -p -m0755 /var/run/sshd
COPY remote_key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user   -R /home/remote_user && \
    chmod 600 /home/remote_user/.ssh/authorized_keys

RUN ssh-keygen -A && rm -rf /run/nologin
CMD /usr/sbin/sshd -D