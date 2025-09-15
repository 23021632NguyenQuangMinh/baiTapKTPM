FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y openssh-server sudo nano \
    && rm -rf /var/lib/apt/lists/*

RUN useradd -m -s /bin/bash user \
    && echo "user:password" | chpasswd \
    && adduser user sudo

RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

RUN mkdir /var/run/sshd

EXPOSE 22 5901

CMD ["/usr/sbin/sshd", "-D"]