FROM arm32v7/debian:latest
#FROM resin/rpi-raspbian:stretch

LABEL maintainer="bronogard" \
	url="https://github.com/bronogard/docker-pivpn"

RUN export DEBIAN_FRONTEND=noninteractive && apt-get update && apt-get install -y \
#        apt-utils \
        curl \
	debconf-utils \
	dhcpcd5 \
	dnsutils \
#        expect \
        git \
#        grep \
#        iptables-persistent \
#        net-tools \
	openvpn \
#        software-properties-common \
        sudo \
#        tar \
        wget \
	whiptail \
	&& rm -rf /var/cache/apt/archives /var/lib/apt/lists

RUN adduser --disabled-password --gecos '' pivpn

USER pivpn:pivpn

WORKDIR /home/pivpn

RUN curl -L https://install.pivpn.io -o install.sh && chmod +x install.sh

EXPOSE 1194

VOLUME ["/dev/random", "/home/pivpn/ovpns"]

ENTRYPOINT ["/bin/bash"]

