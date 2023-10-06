# Ruby on Rails

# Base Image
FROM ruby:3.2.2

# Author
LABEL author="inoue.shinichi.1800@gmail.com"

# Update repositry
RUN apt-get update && \
    apt-get upgrade -y

# Locale & timezone
RUN localectl set-locale LANG=ja_JP.UTF-8 && \
    timedatectl set-timezone Asia/Tokyo

# Change to source directory
RUN mkdir /moss_app_gallery
WORKDIR /moss_app_gallery

# Ruby configuration with Rails 6
RUN bundle install --path '/moss_app_gallery/ruby_module'
COPY ./GemFile /moss_app_gallery/GemFile
COPY ./GemFile.lock /moss_app_gallery/GemFile.lock
# RUN touch Gemfile.lock && \
#     touch Gemfile && \
#     echo "source 'https://rubygems.org'" && \
#     echo "gem 'rails', '~> 6'"

COPY ./src/ /moss_app_gallery/

# Env
ENV APP_PORT 80

# Start up command
CMD ["ruby", "/moss_app_gallery/gallery_server.rb"]