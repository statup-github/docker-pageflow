FROM ruby:2.4

ENV RAILS_VERSION 4.2.6

ENV MYSQL_HOST=mysql
ENV MYSQL_DATABASE=my_pageflow
ENV MYSQL_USER=mysql
ENV MYSQL_PASSWORD=mysql

# Install a lot of things :)

RUN apt-get update && \ 
  apt-get install -y imagemagick && \
  apt-get install -y nano && \
  apt-get install -y nodejs --no-install-recommends && \
  rm -rf /var/lib/apt/lists/* && \
  apt-get update && \ 
  DEBIAN_FRONTEND=noninteractive apt-get install -y default-mysql-server && \
  apt-get install -y redis-server && \
  apt-get install -y default-mysql-client --no-install-recommends && \
  rm -rf /var/lib/apt/lists/* && \
  gem install sprockets -v 3.7.2 && \
  gem install rails --version "$RAILS_VERSION" 


WORKDIR /var/www

RUN rails new app --database=mysql

WORKDIR /var/www/app

COPY ./src/Gemfile /var/www/app
COPY ./src/database.yml /var/www/app/config
COPY ./docker-cmd.sh /var/www/app/docker-cmd.sh
COPY ./docker-entry-point.sh /var/www/app/docker-entry-point.sh

RUN chmod +x /var/www/app/docker-cmd.sh && \
    chmod +x /var/www/app/docker-entry-point.sh

EXPOSE 3000

CMD ["/var/www/app/docker-cmd.sh"]





