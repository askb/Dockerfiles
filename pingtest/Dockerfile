#Simple container to ping google DNS 
FROM ubuntu:14.04

RUN apt-get update && apt-get install -y \
	iputils-ping

ENV var1=ping var2=8.8.8.8

CMD $var1 $var2

#ENTRYPOINT ["ping","-c 30", "8.8.8.8"]
