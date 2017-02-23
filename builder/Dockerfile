FROM debian:stretch-slim

MAINTAINER Infra <infrastructure@concreteplatform.com>

# Base package updates & installations
RUN apt-get update
RUN apt install -y systemd \
	systemd-sysv \
	apt-transport-https \
	apt-utils \
	curl \
	procps \
	telnet \
	vim \
	gnupg2 \
	locales \
	man-db \
	lsof \
	iotop \
	man-db \
	manpages

# Set locales - Docker way (will change in future commit)
RUN echo "en_GB.UTF-8 UTF-8" >> /etc/locale.gen
RUN locale-gen
ENV LANGUAGE en_GB.UTF-8
ENV LANG en_GB.UTF-8
ENV LC_ALL en_GB.UTF-8
ENV LC_CTYPE en_GB.UTF-8

# Set Timers: apt update; apt upgrade --yes
ADD ./system/* /etc/systemd/system/
RUN systemctl enable update.timer
RUN systemctl enable upgrade.timer

STOPSIGNAL SIGRTMIN+3

CMD ["/sbin/init"]
