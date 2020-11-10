FROM jervis/redis
LABEL maintainer="jervis"
ENV REFRESHED_AT=2020-11-09

ENTRYPOINT [ "redis-server", "--protected-mode no", "--logfile /var/log/redis/redis-replica.log", "--slaveof redis_primary 6379" ]