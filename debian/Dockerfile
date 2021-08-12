FROM debian:10

ARG DEBIAN_FRONTEND=noninteractive

# install required dependencies
RUN apt-get update && apt-get install -y apt-utils \
&& apt-get install -y iproute2 iptables net-tools \
&& apt-get install nano
