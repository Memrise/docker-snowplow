FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/

ENV SNOWPLOW_ZIP snowplow_kinesis_elasticsearch_sink_0.8.0_rc1_2x.zip
ENV SNOWPLOW_JAR snowplow-elasticsearch-sink-0.8.0-rc1-2x

WORKDIR /opt/snowplow/
RUN wget http://dl.bintray.com/snowplow/snowplow-generic/${SNOWPLOW_ZIP} && \
    unzip ${SNOWPLOW_ZIP} && \
    rm ${SNOWPLOW_ZIP} && \
    mv ${SNOWPLOW_JAR} snowplow-elasticsearch-sink.jar

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-elasticsearch-sink.jar", "--config", "/etc/snowplow/elasticsearch-sink.conf"]
