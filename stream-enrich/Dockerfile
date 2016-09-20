FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/

ENV SNOWPLOW_ZIP snowplow_stream_enrich_0.8.1.zip
ENV SNOWPLOW_JAR snowplow-stream-enrich-0.8.1

WORKDIR /opt/snowplow/
RUN wget http://dl.bintray.com/snowplow/snowplow-generic/${SNOWPLOW_ZIP} && \
    unzip ${SNOWPLOW_ZIP} && \
    rm ${SNOWPLOW_ZIP} && \
    mv ${SNOWPLOW_JAR} snowplow-stream-enrich.jar

RUN mkdir -p /etc/snowplow/enrichments/

COPY config/enrich.conf /etc/snowplow/enrich.conf
COPY config/resolver.json /etc/snowplow/resolver.json

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-stream-enrich.jar", "--config", "/etc/snowplow/enrich.conf", \
            "--resolver", "file:/etc/snowplow/resolver.json", "--enrichments", "file:/etc/snowplow/enrichments/"]
