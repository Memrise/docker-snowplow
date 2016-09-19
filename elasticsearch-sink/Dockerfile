FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/

ENV SNOWPLOW_JAR snowplow_elasticsearch_sink_0.7.0.zip
RUN wget http://dl.bintray.com/snowplow/snowplow-generic/${SNOWPLOW_SOURCE_ZIP} -O /opt/snowplow/snowplow-elasticsearch-sink.jar

WORKDIR /opt/snowplow/
RUN rm -rf /snowplow_jars/

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-elasticsearch-sink.jar", "--config", "/etc/snowplow/elasticsearch-sink.conf"]
