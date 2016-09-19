FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/

ENV SNOWPLOW_JAR snowplow_stream_collector_0.7.0.zip
RUN wget http://dl.bintray.com/snowplow/snowplow-generic/${SNOWPLOW_SOURCE_ZIP} -O /opt/snowplow/snowplow-stream-collector.jar

WORKDIR /opt/snowplow/
RUN rm -rf /snowplow_jars/

COPY config/collector.conf /etc/snowplow/collector.conf

EXPOSE 80

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-stream-collector.jar", "--config", "/etc/snowplow/collector.conf"]
