FROM ubuntu:bionic

MAINTAINER Monaparty Developers <webmaster@monaparty.me>

# Install common dependencies
RUN apt-get update && apt-get install -y gnupg2 && \
    apt-key adv --keyserver keyserver.ubuntu.com --recv f23c5a6cf475977595c89f51ba6932366a755776 && \
    echo "deb http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic main" > /etc/apt/sources.list.d/python.list && \
    echo "deb-src http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic main" >> /etc/apt/sources.list.d/python.list && \
    apt-get update && apt-get install -y apt-utils ca-certificates wget curl git mercurial \
    python3.5 python3.5-dev python3-distutils \
    build-essential vim unzip software-properties-common sudo gettext-base \
    net-tools iputils-ping telnet lynx locales && \
    curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python3.5 get-pip.py && rm get-pip.py && \
    mv /usr/local/bin/pip /usr/bin/pip3 && \
    ln -sf /usr/bin/python3.5 /usr/bin/python3 && ln -sf /usr/bin/python3.5m /usr/bin/python3m


# Upgrade pip3 to newest
RUN pip3 install --upgrade pip appdirs

# Set locale
RUN dpkg-reconfigure -f noninteractive locales && \
    locale-gen en_US.UTF-8 && \
    /usr/sbin/update-locale LANG=en_US.UTF-8
ENV LC_ALL en_US.UTF-8

# Set home dir env variable
ENV HOME /root
