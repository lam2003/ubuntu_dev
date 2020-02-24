FROM ubuntu:16.04

ENV LANG=en_US.UTF-8

COPY ./go1.13.8.linux-amd64.tar.gz /

RUN tar zxvf /go1.13.8.linux-amd64.tar.gz && \
	rm /go1.13.8.linux-amd64.tar.gz && \
    echo "export PATH=$PATH:/go/bin" >> /etc/environment && \
    echo "export GOROOT=/go" >> /etc/environment && \
    echo "export GOPATH=/go_path" >> /etc/environment && \
    mkdir /go_path && \
    apt-get update -y && \
    apt-get -y install gcc \
	g++ \
	gdb \
	automake \
	autoconf \
	libtool \
	make \
	cmake \
    ssh \
	ntp \
	vim \
	wget \
	curl \
	telnet \
    git \
	subversion \
	doxygen \
	lighttpd \
	net-tools \
	inetutils-ping \
    python \
    libbz2-dev \
	libdb++-dev \
	libssl-dev \
	libdb-dev \
	libssl-dev \
	openssl \
	libreadline-dev \
	libcurl4-openssl-dev \
	libncurses-dev \
	autotools-dev \
	build-essential \
	libicu-dev \
	python-dev && \
    mkdir /var/run/sshd && \
    sed -i 's/Port[ ]*22/Port 36000/' /etc/ssh/sshd_config && \
    echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config && \
    mkdir /home/linmin && \
    useradd -s /bin/bash linmin && \
    echo "linmin:123456" | chpasswd && \
    chown -R linmin:linmin /home/linmin 

# Container should expose ports.
EXPOSE 36000
EXPOSE 1935
EXPOSE 80
CMD ["/usr/sbin/sshd", "-D"]