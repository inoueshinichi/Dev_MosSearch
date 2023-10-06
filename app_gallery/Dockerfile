# Ruby on Rails

# Base Image
FROM ruby:3.2.2

# Author
LABEL author="inoue.shinichi.1800@gmail.com"

# Update repositry
RUN apt-get update && \
    apt-get upgrade -y

# Locale & timezone (only CentOS)
# RUN localectl set-locale LANG=ja_JP.UTF-8 && \
#     timedatectl set-timezone Asia/Tokyo
# RUN localedef -f UTF-8 -i ja_JP ja_JP.UTF-8
ENV LANG="ja_JP.UTF-8" \
    LANGUAGE="ja_JP:ja" \
    LC_ALL="ja_JP.UTF-8" \
    TZ="Asia/Tokyo"

# Change to source directory
RUN mkdir /moss_app_gallery
WORKDIR /moss_app_gallery

# Ruby configuration with Rails 6
RUN bundle config set --local path '/moss_app_gallery/ruby_module'
# RUN touch Gemfile.lock && \
#     touch Gemfile && \
#     echo "source 'https://rubygems.org'" && \
#     echo "gem 'rails', '~> 6'"

# Install ruby package with bundle install
COPY ./Gemfile /moss_app_gallery/Gemfile
COPY ./Gemfile.lock /moss_app_gallery/Gemfile.lock
RUN bundle install

COPY ./src/ /moss_app_gallery/

# Env
ENV APP_PORT 80

# Start up command
CMD ["ruby", "/moss_app_gallery/gallery_server.rb"]