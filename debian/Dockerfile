FROM debian:10

ARG DEBIAN_FRONTEND=noninteractive

# install required dependencies
RUN apt-get update && apt-get install -y apt-utils \
&& apt-get install -y iproute2 iptables net-tools \
&& apt-get install nano \
&& apt-get install -y openssh-server openssh-client

# Add root pass
RUN echo 'root:root' | chpasswd

# Modify `sshd_config`
# From: #PermitRootLogin prohibit-password
# TO  : PermitRootLogin yes
# Check: nano /etc/ssh/sshd_config
RUN sed -ri 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Start sshd
RUN /etc/init.d/ssh start

# restart sshd
# check: sudo service ssh status
ENTRYPOINT service ssh restart && bash
