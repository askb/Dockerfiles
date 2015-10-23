# Development box setup for testing and running .go or .py code
# build
# cd ~/build/
# docker build -t askb/devbox:1.1 .
#
# Start the container:
# docker run -it --name devbox --privileged --rm -v /var/run/docker.sock:/var/run/docker.sock -v /home/abelur/git/docker-fork:/go/src/github.com/docker/docker -e BOX_NAME=devbox askb/devbox:1.1

from ubuntu:14.04

run apt-get update -y && apt-get install -y \
		mercurial \
		git \
		golang \
		python \
		curl \
		vim \
		strace \
		diffstat \
		pkg-config \
		cmake \
		build-essential \
		tcpdump \
		screen \
		cgdb \
		gdb \
		ipython \
		psmisc

# set goroot and GOPATH
env GOROOT /usr/local/go
env PATH /usr/local/go/bin:$PATH

# Setup home environment
run useradd dev
run mkdir /home/dev && chown -R dev: /home/dev
run mkdir -p /home/dev/go /home/dev/bin /home/dev/lib /home/dev/include
env PATH /home/dev/bin:$PATH
env PKG_CONFIG_PATH /home/dev/lib/pkgconfig
env LD_LIBRARY_PATH /home/dev/lib
env GOPATH /home/dev/go:$GOPATH

#run go get github.com/askb/docker/pulls

# Create a shared data volume
# We need to create an empty file, otherwise the volume will
# belong to root.
# This is probably a Docker bug.
run mkdir /var/shared/
run touch /var/shared/placeholder
run chown -R dev:dev /var/shared
volume /var/shared

workdir /home/dev
env HOME /home/dev
add vimrc /home/dev/.vimrc
add vim /home/dev/.vim
add bash_profile /home/dev/.bash_profile
add gitconfig /home/dev/.gitconfig

# Link in shared parts of the home directory
run ln -s /var/shared/.ssh
run ln -s /var/shared/.bash_history
run ln -s /var/shared/.maintainercfg

run chown -R dev: /home/dev
user dev
