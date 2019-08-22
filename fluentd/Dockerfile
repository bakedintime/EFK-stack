FROM fluent/fluentd:stable
RUN addgroup -S fluent
RUN adduser -S -D -h /home/fluent fluent fluent
RUN chown -R fluent:fluent /home/fluent
RUN mkdir /home/fluent/logs
RUN chown -R fluent:fluent /home/fluent/logs/
WORKDIR /home/fluent
RUN apk add --update --virtual .build-deps \
    sudo build-base ruby-dev \
    && sudo gem install \
    fluent-plugin-elasticsearch \
    && sudo gem sources --clear-all \
    && apk del .build-deps \
    && rm -rf /var/cache/apk/* \
    /home/fluent/.gem/ruby/2.3.0/cache/*.gem
