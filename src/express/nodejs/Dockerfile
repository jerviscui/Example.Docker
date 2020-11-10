FROM jerviscui/node-aliyun:15.1.0
LABEL maintainer="jervis"
ENV REFRESHED_AT=2020-11-09

RUN mkdir -p /var/log/nodeapp

ADD ./nodeapp /opt/nodeapp/
WORKDIR /opt/nodeapp
RUN npm install

VOLUME [ "/var/log/nodeapp" ]

EXPOSE 3000

ENTRYPOINT [ "nodejs", "server.js" ]