#Simple web server container
FROM ubuntu:14.04

RUN apt-get update && apt-get install -y \
	apache2 \
	apache2-utils
	
#&& rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

#RUN apt-get clean

EXPOSE 80

ENTRYPOINT ["apache2ctl"]

CMD ["-D","FOREGROUND"]
