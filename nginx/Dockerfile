FROM nginx:1.13
LABEL maintainer "andresgarcia.kaox@gmail.com"

RUN rm /etc/nginx/conf.d/default.conf && \
	rm /etc/nginx/nginx.conf

COPY conf/jenkins.conf /etc/nginx/conf.d/jenkins.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf