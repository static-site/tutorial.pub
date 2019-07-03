# php.ini

#### [PHP]

##### About php.ini

PHP 的初始化文件，通常命名为 php.ini，主管 PHP 行为的大多数方面。



PHP 尝试去查找并加载这个配置从许多地方。

下面是它的搜索顺序的概括：

1. SAPI 模块明确规定的地方。

2. 这 PHPRC 环境变量。（截至 PHP 5.2.0）

3. Windows 上的许多预定义注册表项（截至 PHP 5.2.0）

4. 当前工作目录（除了 CLI）

5. 网络网页服务器的目录（用于 SAPI 模块），或者 PHP 的目录（除非在 Windows 里）

6. 编译时选项 `--with-config-file-path` 目录，或者 Windows 目录（通常 C:\Windows）

   参阅 PHP 文档，获取更多具体信息。

   http://php.net/configuration.file



##### About this file



##### Quick Reference



##### php.ini Options



##### Language Options

engine=On

short_open_tag=Off

precision=14

output_buffering=4096

zlib.output_compression=Off

implicit_flush=Off

unserilize_callback_func=

serialize_precision=-1

disable_functions=

disable_classes=

zend.enable_gc=On



##### Miscellaneous

expose_php=On



##### Resource Limits

max_execution_time=30

max_input_time=60

max_input_nesting_level = 64

;max_input_vars = 1000

memory_limit=128M



##### Error handling and logging

error_reporting=E_ALL

display_errors=On

display_starup_errors=On

log_errors=On

log_errors_max_len=1024

ignore_repeated_errors=Off

ignore_repeated_source=Off

report_memleaks=On

html_errors=On



##### Data Handling

variables_order="GPCS"

request_order="GP"

register_argc_argv=Off

auto_globals_jit=On

post_max_size=8M

auto_prepend_file=

auto_append_file=

default_mimetype="text/html"

default_charset="UTF-8"



##### Path and Directories

doc_root=

user_dir=

extension_dir="ext"

enable_dl=Off



##### File Uploads

file_uploads=On

upload_max_filesize=2M

max_file_uploads=20



##### Fopen wrappers

allow_url_fopen=On

allow_url_include=Off

default_socket_timeout=60



##### Dynamic Extensions

extension=bz2

extension=curl

extension=fileinfo

extension=gd2

extension=gettext

extension=gmp

extension=intl

extension=imap

extension=interbase

extension=ldap

extension=mbstring

extension=exif

extension=mysqli

extension=oci8_12c

extension=odbc

extension=openssl

extension=pdo_firebird

extension=pdo_mysql

extension=pdo_oci

extension=pdo_odbc

extension=pdo_pgsql

extension=pdo_sqlite

extension=pgsql

extension=shmop

extension=snmp

extension=soap

extension=sockets

extension=sodium

extension=sqlite3

extension=tidy

extension=xmlrpc

extension=xsl

extension=php_amqp.dll



### Module Settings

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

#### [Xdebug]

zend_extension=E:\env\win\ProgramData\php\ext\x64\ts\7.3\php_xdebug-2.8.0alpha1-7.3-vc15-x86_64.dll
xdebug.profiler_enable=On
xdebug.profiler_output_dir=E:\env\tmp\php\xdebug
xdebug.trace_output_dir=E:\env\tmp\php\xdebug