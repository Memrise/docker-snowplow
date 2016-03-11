FROM memrise/snowplow:base-r78_rc3

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mv snowplow-elasticsearch-sink-0.5.0 /opt/snowplow/snowplow-elasticsearch-sink.jar

WORKDIR /opt/snowplow/
RUN rm -rf /snowplow_jars/

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-elasticsearch-sink.jar", "--config", "/etc/snowplow/elasticsearch-sink.conf"]
