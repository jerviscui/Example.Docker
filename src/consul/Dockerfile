FROM consul
LABEL maintainer="jervis"
ENV REFRESHED_AT=2020-11-19

ADD consul.json /config/

EXPOSE 53/udp 8300 8301 8301/udp 8302 8302/udp 8400 8500

VOLUME ["/data"]

ENTRYPOINT [ "/bin/consul", "agent", "-ui", "-config-dir=/config" ]
CMD []
