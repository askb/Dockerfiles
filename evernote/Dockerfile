# refer: https://hub.docker.com/r/thshaw/evernote/~/dockerfile/
# Here I am using a diff version of evernote, and combined the wine and evernote dockerfiles.
# Run evernote windows app in a container with wine
# First time run to create a evernote image
# $ docker run -d -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=unix$DISPLAY --name evernote askb/evernote
# to start evernote:
# $ xhost +
# $ docker start evernote
# stop evernote:
# $ docker stop evernote

FROM ubuntu:14.04

MAINTAINER askb <askb23@gmail.com>

RUN dpkg --add-architecture i386

RUN apt-get update -y && \
	apt-get install -y \
	software-properties-common && \
	add-apt-repository -y \
	ppa:ubuntu-wine/ppa && \
	apt-get update -y

RUN apt-get install -y wine1.7 winetricks

RUN apt-get purge -y software-properties-common
RUN apt-get autoclean -y


COPY Evernote_5.9.6.9494.exe /usr/src/evernote.exe
COPY start.sh /start.sh

ENTRYPOINT ["bash", "/start.sh"]
