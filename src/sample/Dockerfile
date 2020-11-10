FROM nginx
LABEL maintainer="jervis"
ENV REFRESHED_AT=2020-11-03

RUN mkdir -p /var/www/html
ADD nginx/global.conf /etc/nginx/conf.d/

CMD [  "-g", "daemon off;" ]
ENTRYPOINT [ "nginx" ]

EXPOSE 80