FROM ruby:2.5.3-slim

ENV NOKOGIRI_USE_SYSTEM_LIBRARIES=true

RUN apt-get update \
    && BUILD_DEPS=' \
      build-essential \
      patch \
      ruby-dev \
      zlib1g-dev \
      liblzma-dev \
      libxml2-dev \
      libxslt-dev \
    ' \
    && apt-get install -y --no-install-recommends $BUILD_DEPS
      

ADD Gemfile /Gemfile

# Quite a bit of trial and error to get nokogiri to install
RUN gem update --system \
    && gem install pkg-config \
    && bundle install \
    && rm /Gemfile

RUN echo Build Deps were $BUILD_DEPS
