FROM logstash:7.9.3
LABEL maintainer="jervis"
ENV REFRESHED_AT=2020-11-12

WORKDIR /usr/share/logstash
ADD ./logstash.conf /usr/share/logstash/

ENTRYPOINT [ "bin/logstash" ]
CMD [ "-f", "logstash.conf", "--config.reload.automatic" ]