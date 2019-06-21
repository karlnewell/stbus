FROM docker.elastic.co/logstash/logstash-oss:6.8.0
MAINTAINER Karl Newell <karlnewell@gmail.com>

WORKDIR /usr/share/logstash/logstash-plugin-udp-native-sensors
USER root
RUN yum -y install rubygems
COPY ./logstash-plugin-udp-native-sensors ./
RUN gem build logstash-codec-juniper-udp-native-sensors.gemspec
RUN logstash-plugin install logstash-codec-juniper-udp-native-sensors-0.1.0.gem

USER 1000

WORKDIR /usr/share/logstash/config

RUN rm -f /usr/share/logstash/pipeline/logstash.conf
ADD pipeline/ /usr/share/logstash/pipeline/

ENTRYPOINT ["/usr/local/bin/docker-entrypoint"]
