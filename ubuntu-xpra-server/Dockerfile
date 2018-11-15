FROM ubuntu:16.04

# To skip keyboard configuration.
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update -y
RUN apt-get install -y software-properties-common
RUN apt-get install -y apt-transport-https

USER root
RUN dpkg --configure -a
RUN apt-key adv --keyserver keys.gnupg.net --recv-keys 18ADB31CF18AD6BB
RUN add-apt-repository -y 'deb https://xpra.org/ xenial main'
RUN apt-get clean
RUN apt-get update -y
RUN apt-get upgrade -y

# for X11
RUN apt-get install -y xpra
RUN apt-get install -y xvfb
RUN apt-get install -y xserver-xephyr
RUN apt-get install -y xterm

# for SSH daemon
RUN apt-get -y install ssh

# for Win
RUN add-apt-repository -y ppa:ubuntu-wine/ppa
RUN dpkg --add-architecture i386
RUN apt-get update -y
RUN apt-get install -y wine
RUN apt-get install -y dos2unix

COPY  startup.sh  /usr/local/bin/
RUN dos2unix /usr/local/bin/startup.sh
EXPOSE 22

CMD ["/usr/local/bin/startup.sh"]