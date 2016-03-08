FROM iron/java:1.8

MAINTAINER Daniel Zohar <daniel@memrise.com>

ENV SNOWPLOW_SOURCE_ZIP snowplow_kinesis_r78_great_hornbill_rc2.zip

WORKDIR /snowplow_jars/
RUN mkdir -p /etc/snowplow/ && \
    mkdir -p /opt/snowplow/ && \
    wget https://bintray.com/artifact/download/snowplow/snowplow-generic/${SNOWPLOW_SOURCE_ZIP} && \
    unzip ${SNOWPLOW_SOURCE_ZIP}
