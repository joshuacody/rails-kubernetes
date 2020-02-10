FROM ruby:2.4.2

RUN apk --update add nodejs netcat-openbsd postgresql-dev
RUN apk --update add --virtual build-dependencies make g++

RUN mkdir /Users/jsmith/repos/rails-kubernetes/rails-kube-demo

WORKDIR /Users/jsmith/repos/rails-kubernetes/rails-kube-demo

ADD Gemfile /Users/jsmith/repos/rails-kubernetes/rails-kube-demo/Gemfile
ADD Gemfile.lock /Users/jsmith/repos/rails-kubernetes/rails-kube-demo/Gemfile.lock

RUN bundle install
RUN apk del build-dependencies && rm -rf /var/cache/apk/*

ADD . /Users/jsmith/repos/rails-kubernetes/rails-kube-demo

COPY docker-entrypoint.sh /usr/local/bin

ENTRYPOINT ["docker-entrypoint.sh"]