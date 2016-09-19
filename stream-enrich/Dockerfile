FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/

ENV SNOWPLOW_JAR snowplow_stream_enrich_0.8.1.zip
RUN wget http://dl.bintray.com/snowplow/snowplow-generic/${SNOWPLOW_SOURCE_ZIP} -O /opt/snowplow/snowplow-stream-enrich.jar

WORKDIR /opt/snowplow/
RUN rm -rf /snowplow_jars/

RUN mkdir -p /etc/snowplow/enrichments/

COPY config/enrich.conf /etc/snowplow/enrich.conf
COPY config/resolver.json /etc/snowplow/resolver.json

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-stream-enrich.jar", "--config", "/etc/snowplow/enrich.conf", \
            "--resolver", "file:/etc/snowplow/resolver.json", "--enrichments", "file:/etc/snowplow/enrichments/"]
