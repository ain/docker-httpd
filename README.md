# docker-httpd

Docker HTTPD extension for legacy PHP versions.

## Software

Image is based on Apache's [httpd:2.2](https://github.com/docker-library/httpd) (2.2.31), extended with:

- PHP
  - 5.1.3. Only available from Docker Hub at `aintohvri/docker-httpd:5.1.3`. Dockerfile has been discontinued.
- SSMTP

## Configuration

- For email delivery with `mail()`, `/etc/ssmtp/ssmtp.conf` needs to be configured with appropriate credentials.

## Licence

Copyright © 2016 Ain Tohvri, [contributors](https://github.com/ain/docker-httpd/graphs/contributors). Licenced under [GPL-3](https://github.com/ain/docker-httpd/blob/master/LICENSE).
