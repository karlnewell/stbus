#FROM fluent/fluentd:v0.12-onbuild
FROM fluent/fluentd:v1.3-onbuild
MAINTAINER Karl Newell <karlnewell@gmail.com>

USER root

RUN apk add --no-cache --update --virtual .build-deps \
        sudo build-base ruby-dev \
 && sudo gem install \
        fluent-plugin-kafka fluent-plugin-juniper-telemetry \
 && sudo gem sources --clear-all \
 && apk del .build-deps \
 && rm -rf /home/fluent/.gem/ruby/2.3.0/cache/*.gem

RUN sed -i "1 i\require 'fluent/parser'" /usr/lib/ruby/gems/2.5.0/gems/fluent-plugin-juniper-telemetry-0.3.0/lib/fluent/plugin/parser_juniper_jti.rb

EXPOSE 24284
EXPOSE 50000/udp
