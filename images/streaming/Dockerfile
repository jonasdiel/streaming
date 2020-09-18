FROM ubuntu:18.04

RUN apt-get update; \
	apt-get install git build-essential libpcre3 libpcre3-dev libssl-dev wget zlibc zlib1g zlib1g-dev -y

RUN git clone https://github.com/sergey-dryabzhinsky/nginx-rtmp-module.git; \
	wget http://nginx.org/download/nginx-1.18.0.tar.gz; \
	tar -xf nginx-1.18.0.tar.gz; \
	cd nginx-1.18.0; \
	./configure --with-http_ssl_module --add-module=../nginx-rtmp-module; \
	make -j 1; \
	make install;

COPY ./nginx.conf /usr/local/nginx/conf/nginx.conf

RUN mkdir -p /nginx/hls; \
    chown -R www-data:www-data /nginx

EXPOSE 8080
EXPOSE 1935

VOLUME /nginx/hls

CMD /usr/local/nginx/sbin/nginx -g 'daemon off;'
