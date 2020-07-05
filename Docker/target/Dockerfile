FROM centos:centos8.2.2004
LABEL Name=deployerstudy Version=0.0.1

RUN dnf -y update && dnf install -y openssh openssh-server

# https://qiita.com/YumaInaura/items/1d5c18a9e55484ccad89
RUN mkdir /var/run/sshd
RUN mkdir /root/.ssh
RUN echo 'root:screencast' | chpasswd
RUN sed -i 's/PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

# https://qiita.com/kkk627/items/b7cc990f310f04a584c7
RUN ssh-keygen -t rsa -N "" -f /etc/ssh/ssh_host_rsa_key
RUN ssh-keygen -t dsa -N "" -f /etc/ssh/ssh_host_dsa_key
RUN ssh-keygen -t ecdsa -N "" -f /etc/ssh/ssh_host_ecdsa_key
RUN ssh-keygen -t ed25519 -N "" -f /etc/ssh/ssh_host_ed25519_key

# https://ja.coder.work/so/docker/2239459
RUN rm -rf /run/nologin

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]