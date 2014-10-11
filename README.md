# PHP Docker Images

These Docker instructions contain all current/stable official PHP versions, and
HHVM. Builds are done using [PHP-Build](https://github.com/CHH/php-build).

## Why Not Use The Official Docker/PHP Images?

The default images currently [do not support
Composer](https://github.com/docker-library/php/issues/17), and lack a
mechanism to easily change the installed extensions. While not "official",
PHP-Build fixes this problem.

## Example:

```Dockerfile
FROM naneau/php:5.5

# Add local dir to /var/php/app dir
ADD . /var/php/awesome-app

# Change workdir
WORKDIR /var/php/awesome-app

# Install composer deps
RUN composer install .

# Start development server
CMD php -S localhost:80
```

## Composer

Composer is included, and installed in `/usr/local/bin`, meaning that it can
simply be called using `composer`:

```bash
docker run naneau/php:5.5 composer require monolog/monolog
```
