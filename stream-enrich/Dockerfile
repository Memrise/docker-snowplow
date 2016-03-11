FROM memrise/snowplow:base-r78_rc2

MAINTAINER Daniel Zohar <daniel@memrise.com>

RUN mv snowplow-stream-enrich-0.7.0 /opt/snowplow/snowplow-stream-enrich.jar

WORKDIR /opt/snowplow/
RUN rm -rf /snowplow_jars/

RUN mkdir -p /etc/snowplow/enrichments/

COPY config/enrich.conf /etc/snowplow/enrich.conf
COPY config/resolver.json /etc/snowplow/resolver.json

ENTRYPOINT ["/usr/bin/java", "-jar", "snowplow-stream-enrich.jar", "--config", "/etc/snowplow/enrich.conf", \
            "--resolver", "file:/etc/snowplow/resolver.json", "--enrichments", "file:/etc/snowplow/enrichments/"]


