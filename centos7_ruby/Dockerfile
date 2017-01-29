FROM centos:7
MAINTAINER paul@kyanmedia.com
ENV REFRESHED_AT 2016-12-29

# Allow us to get the latest node version
RUN curl --silent --location https://rpm.nodesource.com/setup_7.x | bash -

RUN yum -y update && yum install -y \
  which \
  make \
  wget \
  readline-devel \
  libyaml-devel \
  nodejs \
  bzip2 \
  mysql-devel \
  gcc-c++ \
  file \
  fontconfig \
  libpng \
  libjpeg \
  openssl \
  icu \
  libX11 \
  libXext \
  libXrender \
  xorg-x11-fonts-Type1 \
  xorg-x11-fonts-75dpi

RUN wget http://download.gna.org/wkhtmltopdf/0.12/0.12.4/wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
RUN unxz wkhtmltox-0.12.4_linux-generic-amd64.tar.xz
RUN tar -xvf wkhtmltox-0.12.4_linux-generic-amd64.tar
RUN mv wkhtmltox/bin/* /usr/local/bin/
RUN rm -rf wkhtmltox
RUN rm -f wkhtmltox-0.12.4_linux-generic-amd64.tar

RUN yum clean all

ENV RUBY_VERSION 'ruby 2.4.0'

RUN wget -O ruby-install-0.6.0.tar.gz https://github.com/postmodern/ruby-install/archive/v0.6.0.tar.gz \
  && tar -xzvf ruby-install-0.6.0.tar.gz \
  && cd ruby-install-0.6.0/ \
  && make install \
  && rm -rf /usr/local/src/*
RUN ruby-install --system $RUBY_VERSION

# Setup app location
RUN mkdir -p /app
WORKDIR /app

RUN gem install bundler

# Install forego
RUN rpm -i https://bin.equinox.io/c/ekMN3bCZFUn/forego-stable-linux-386.rpm
