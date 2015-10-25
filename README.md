### Development box setup for testing and running .go or .py app code built using Dockerfiles.

Build Instructions:
  1. 
  2. 
  3. cd ~/mydevbox/
  4. docker build -t askb/devbox:1.0 .
  
Start the container:
  docker run -it --name devbox --privileged --rm -v /var/run/docker.sock:/var/run/docker.sock -v /home/abelur/git/docker-fork:/go/src/github.com/docker/docker -e BOX_NAME=devbox askb/devbox:1.0

