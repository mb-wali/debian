FROM debian:10

RUN TZ=Europe/Vienna \
apt-get update \
&& apt-get install -y iproute2 iptables net-tools

# add static ip address
# https://stackoverflow.com/questions/27937185/assign-static-ip-to-docker-container
