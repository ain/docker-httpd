FROM httpd:2.4

ENV PHP_VERSION 5.1.6
#ENV HTTPD_VERSION 2.4

RUN apt-get update && apt-get install -y libxml2 libxml2-dev libxpm4 libxpm-dev libxslt1.1 libxslt1-dev build-essential wget vim msmtp default-mysql-client default-libmysqlclient-dev m4 librecode-dev libreadline6-dev libcurl4-openssl-dev flex libpng16-16 libpng-dev pkg-config libgdbm-dev libsqlite3-dev libssl-dev libfreetype6 libfreetype6-dev libjpeg-dev

RUN ln -s /usr/lib/x86_64-linux-gnu/libXpm.so /usr/lib/libXpm.so \
  && ln -s /usr/lib/x86_64-linux-gnu/libmysqlclient.so /usr/lib/libmysqlclient.so \
  && ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so /usr/lib/libjpeg.so \
  && ln -s /usr/lib/x86_64-linux-gnu/libpng.so /usr/lib/libpng.so

#RUN apt-get install -y build-essential libssl-dev \
#  libsqlite3-dev
#  librecode-dev \
#  libreadline6-dev \
#  libcurl4-openssl-dev \
#  pkg-config \
#  libgdbm-dev \
#  m4 \
#  flex \
#  wget \
#  vim \
#  libpng12-0 \
#  libpng12-dev \
#  libxpm4 \
#  libxpm-dev \
#  libmysqlclient-dev \
#  mysql-client \
#  ssmtp

#RUN cd /tmp && wget "https://www.apache.org/dist/httpd/httpd-$HTTPD_VERSION.tar.gz" \
#  && tar xzvf "httpd-$HTTPD_VERSION.tar.gz" \
#  && /usr/local/apache2/bin/apxs -c -i "/tmp/httpd-$HTTPD_VERSION/modules/mappers/mod_rewrite.c"

RUN cd /tmp && wget http://ftp.gnu.org/gnu/bison/bison-2.3.tar.gz \
  && tar xzvf bison-2.3.tar.gz \
  && cd bison-2.3 \
  && ./configure \
  && make \
  && make install \
  && make clean

# RUN apt-get install -y libfreetype6-dev
# RUN cd /tmp && wget http://download.savannah.gnu.org/releases/freetype/freetype-2.6.tar.gz \
#   && tar xzvf freetype-2.6.tar.gz \
#   && cd freetype-2.6 \
#   && ./configure \
#   && make \
#   && make install \
#   && make clean

# RUN mkdir -p /usr/include/freetype2/freetype
# RUN ln -s /usr/include/freetype2/freetype.h /usr/include/freetype2/freetype/freetype.h
#
RUN cd /tmp && wget http://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.16.tar.gz \
  && tar xzvf libiconv-1.16.tar.gz \
  && cd libiconv-1.16 \
  && ./configure \
  && make \
  && make install \
  && make clean

#RUN cd /tmp && wget http://www.ijg.org/files/jpegsrc.v9a.tar.gz \
  #&& tar xzvf jpegsrc.v9a.tar.gz \
  #&& cd jpeg-9a \
  #&& ./configure \
  #&& make \
  #&& make install \
  #&& make clean

RUN cd /tmp && wget "http://museum.php.net/php5/php-$PHP_VERSION.tar.gz" \
  && tar xzvf "php-$PHP_VERSION.tar.gz" \
  && cd "php-$PHP_VERSION" \
  && ./configure --enable-bcmath --with-xsl --enable-fastcgi --enable-force-cgi-redirect --with-gd --enable-sockets --with-mysql=/usr/ --with-gettext --enable-mbstring --with-xpm-dir=/usr/lib --with-jpeg-dir=/usr/lib --with-gdbm=/usr/lib --with-zlib-dir=/usr/lib --with-freetype-dir=/usr/lib --with-iconv=/usr/local/lib --with-xml --with-dom --with-config-file=/etc/php5.ini --with-openssl-dir=/usr/include/openssl --enable-memory-limit --with-pdo-mysql=/usr/ --with-apxs2 --enable-so --without-pear --with-png-dir=/usr/lib \
  && make \
  && make install \
  && make clean

COPY ./httpd.conf /usr/local/apache2/conf/httpd.conf

COPY ./php.ini /usr/local/lib/php.ini

RUN echo "FromLineOverride=YES" >> /etc/ssmtp/ssmtp.conf

RUN ln -s /usr/local/apache2/htdocs /var/www
