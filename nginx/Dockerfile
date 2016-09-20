FROM nginx:latest

MAINTAINER Mathieu Androz <mathieu@shareyourscript.me>

ENV TZ="Europe/Paris"
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/

COPY ./conf.d/nginx.conf /etc/nginx/conf/nginx.conf
COPY ./conf.d/default.conf /etc/nginx/conf.d/default.conf
COPY ./conf.d/00-http.conf /etc/nginx/conf.d/00-http.conf
