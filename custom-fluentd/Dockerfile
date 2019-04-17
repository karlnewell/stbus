FROM fluent/fluentd:v0.12-onbuild
MAINTAINER Karl Newell <karlnewell@gmail.com>

USER root

RUN apk add --no-cache --update --virtual .build-deps \
        sudo build-base ruby-dev \
 && sudo gem install \
        fluent-plugin-kafka fluent-plugin-juniper-telemetry \
 && sudo gem sources --clear-all \
 && apk del .build-deps \
 && rm -rf /home/fluent/.gem/ruby/2.3.0/cache/*.gem

EXPOSE 24284
EXPOSE 50000/udp
