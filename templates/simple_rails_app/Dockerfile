FROM ruby:2.3.3-slim
MAINTAINER <your name>

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    build-essential \
    curl \
    fontconfig \
    sudo \
    ssh \
    libpq-dev \
    tzdata \
    git \
  && curl -sLO https://deb.nodesource.com/setup_6.x \
  && bash setup_6.x \
  && rm -f setup_6.x \
  && apt-get install -y nodejs \
  && apt-get clean all \
  && rm -rf /var/lib/apt/lists/*

ENV PHANTOMJS_VERSION=2.1.1
RUN \
  cd /usr/local/share && \
  curl -sLO https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-${PHANTOMJS_VERSION}-linux-x86_64.tar.bz2 && \
  tar xvf phantomjs-${PHANTOMJS_VERSION}-linux-x86_64.tar.bz2 && \
  rm phantomjs-${PHANTOMJS_VERSION}-linux-x86_64.tar.bz2 && \
  ln -s /usr/local/share/phantomjs-${PHANTOMJS_VERSION}-linux-x86_64/bin/phantomjs /usr/local/bin/phantomjs

RUN mkdir -p /root/.ssh/

RUN ssh-keyscan -H github.com >> ~/.ssh/known_hosts
RUN ssh-keyscan -H bitbucket.org >> ~/.ssh/known_hosts

ENV GEM_HOME /app/vendor/bundle
ENV PATH $GEM_HOME/bin:$PATH
ENV BUNDLE_PATH $GEM_HOME
ENV BUNDLE_BIN $BUNDLE_PATH/bin

WORKDIR /app
