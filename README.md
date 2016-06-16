# docker-httpd

Docker HTTPD extension for legacy PHP versions.

## Software

Image is based on Apache's [httpd:2.2](https://github.com/docker-library/httpd), extended with:

- PHP 5.1.3
- SSMTP

## Configuration

- For email delivery with `mail()`, `/etc/ssmtp/ssmtp.conf` needs to be configured with appropriate credentials.

## Licence

Copyright © 2016 Ain Tohvri, [contributors](https://github.com/ain/docker-httpd/graphs/contributors). Licenced under [GPL-3](https://github.com/ain/docker-httpd/blob/master/LICENSE).
