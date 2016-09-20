FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/

ENV SNOWPLOW_ZIP snowplow_stream_collector_0.7.0.zip
ENV SNOWPLOW_JAR snowplow-stream-collector-0.7.0

WORKDIR /opt/snowplow/
RUN wget http://dl.bintray.com/snowplow/snowplow-generic/${SNOWPLOW_ZIP} && \
    unzip ${SNOWPLOW_ZIP} && \
    rm ${SNOWPLOW_ZIP} && \
    mv ${SNOWPLOW_JAR} snowplow-stream-collector.jar

COPY config/collector.conf /etc/snowplow/collector.conf

EXPOSE 80

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-stream-collector.jar", "--config", "/etc/snowplow/collector.conf"]
