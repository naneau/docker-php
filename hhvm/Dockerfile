FROM ubuntu:14.04
MAINTAINER Maurice Fonk <maurice@naneau.net>

# Update apt
RUN apt-get update

# Install wget
RUN apt-get install -y wget

# Add hhvm apt repo
RUN wget -O - http://dl.hhvm.com/conf/hhvm.gpg.key | apt-key add -
RUN echo deb http://dl.hhvm.com/ubuntu trusty main | tee /etc/apt/sources.list.d/hhvm.list

# Update apt
RUN apt-get update

# Install
RUN apt-get install -y hhvm

# Somehow not installed with hhvm, see https://github.com/facebook/hhvm/issues/3849
RUN apt-get install -y libgmp10

# Set as php binary
RUN /usr/bin/update-alternatives --install /usr/bin/php php /usr/bin/hhvm 60

# Install Composer
RUN php -r "readfile('https://getcomposer.org/installer');" | php
RUN mv composer.phar /usr/local/bin/composer
