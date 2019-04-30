# php.ini

> Module Settings

#### [CLI Server]

cli_server.color=On

#### [Date]

#### [filter]

#### [iconv]

#### [intl]

#### [sqlite3]

#### [Pcre]

#### [Pdo]

#### [Pdo_mysql]

#### [Phar]

#### [mail function]

SMTP=localhost

smtp_port=25

mail.add_x_header=Off

#### [ODBC]

odbc.allow_persistent=On

odbc.check_persistent=On

odbc.max_persistent=-1

odbc.max_links=-1

odbc.defaultlrl=4096

odbc.defaultbinmode=1

#### [Interbase]

ibase.allow_persistent=1

ibase.max_persistent=-1

ibase.max_links=-1

ibase.timestatmpformat="%Y-%m-%d %H:$M:%S"

ibase.dateformat="%Y-%m-%d"

ibase.timeformat="%H:%M:%S"

#### [MySQLi]

mysqli.max_persistent=-1

mysqli.allow_persistent=On

mysqli.max_links=-1

mysqli.default_port=3306

mysqli.default_socket=

mysqli.default_host=

mysqli.default_user=

mysqli.default_pw=

mysqli.reconnect=Off

#### [mysqlnd]

mysqlnd.collect_statistics=On

mysqlnd.collect_memory_statistics=On

#### [OCI8]

#### [PostgreSQL]

pgsql.allow_persistent=On

pgsql.auto_reset_persistent=Off

pgsql.max_persistent=-1

pgsql.max_links=-1

pgsql.ignore_notice=0

pgsql.log_notice=0

#### [bcmath]

bcmath.scale=0

#### [browscap]

#### [Session]

session.save_handler=files

session.use_strict_mode=0

session.use_cookies=1

session.use_only_cookies=1

session.name=PHPSESSID

session.auto_start=0

session.cookie_lifetime=0

session.cookie_path=/

session.cookie_domain=

session.cookie_httponly=

session.cookie_samesite=

session.serialize_handler=php

session.gc_probability=1

session.gc_divisor=1000

session.gc_maxlifetime=1440

session.referer_check=

session.cache_limiter=mocache

session.cache_expire=180

session.use_trans_sid=0

session.sid_length=26

session.trans_sid_tags="a=href,area=href,frame=src,form="

session.sid_bits_per_character=5

#### [Assertion]

zend.assertions=1

#### [COM]

#### [mbstring]

#### [gd]

#### [exif]

#### [Tidy]

tidy.clean_output=Off

#### [soap]

soap.wsdl_cache_enabled=1

soap.wsdl_cache_dir="/tmp"

soap.wsdl_cache_ttl=86400

soap.wsdl_cache_limit=5

#### [sysvshm]

#### [ldap]

ldap.max_links=-1

#### [dba]

#### [opcache]

zend_extension="D:/env/win/ProgramFiles/php-7.3.0/ext/php_opcache.dll"

opcache.enable=1

opcache.enable_cli=1

#### [curl]

curl.cainfo=

#### [openssl]

openssl.cafile=D:/env/www/legend/dist/https/curl.haxx.se/ca/cacert.pem

openssl.capath=
