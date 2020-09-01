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



> 这个指令允许你去禁用某些函数。
>
> 它接受一个逗号分隔的函数名列表。
>
> 禁用函数

disable_functions=



> 这个指令允许你去禁用某些类。
>
> 它接受一个逗号分隔的类名列表。
>
> 禁用类

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



##### Error handling and logging 错误处理和记录



error_reporting=E_ALL



> 该指令控制是否以及 PHP 将在哪里输出错误、通知和警告。
>
> 错误输出是非常有用的在开发中，
>
> 但它可能非常危险在生产环境。
>
> 取决于代码哪一个触发错误，敏感信息可能从你的应用中潜在泄露，
>
> 例如数据库用户名和密码，或更糟糕。
>
> 对于生产环境，我们建议记录错误而不是发送它们到标准输出 。
>
> 可用的值：
>
> ​    Off = 不显示任何错误
>
> ​    stderr = 显示错误到标准错误（仅影响 CGI/CLI 二进制文件！）
>
> ​    On 或 stdout = 显示错误到标准输出
>
> 默认值：On
>
> 开发环境值：On
>
> 生产环境值：Off
>
> 显示错误

display_errors=On



> 显示错误哪一个发生在 PHP 的启动过程分别处理和 display_errors 。
>
> PHP 的默认行为抑制从客户端导致的那些错误。
>
> 打开启动错误显示在调试配置问题中很有用。
>
> 我们强烈建议你设置为 “off” 对于生产服务器。
>
> 默认值：Off
>
> 开发环境值：On
>
> 生产环境值：Off
>
> 显示启动错误

display_starup_errors=On



log_errors=On

log_errors_max_len=1024

ignore_repeated_errors=Off

ignore_repeated_source=Off

report_memleaks=On

html_errors=On



##### Data Handling 数据处理



> 使用这个分隔符去分开在 PHP 里面生成的网址参数。
>
> PHP 的默认设置是 “&”。
>
> 例子：
>
> 参数分隔符 - 输出

arg_separator.output = "\&amp;"



> 分隔符列表用于  PHP 去解析输入的网址到变量。
>
> PHP 的默认设置是 “&”。
>
> 注意：每个字符在这个指令是考虑过作为分隔符。
>
> 例子：
>
> 参数分隔符 - 输入

arg_separator.input = ";&"



variables_order="GPCS"

request_order="GP"

register_argc_argv=Off



> 启用后，ENV, REQUEST 和 SERVER 变量被创建当他们在
>
> 第一次使用（即时化技术），而不是当这个脚本运行时。如果这些
>
> 变量在一个脚本里不使用，这个指令将获得性能效果。
>
> PHP 指令 register_argc_argv 必须被禁用，此指令才能生效。
>
> 自动全局变量使用即时化技术

auto_globals_jit=On



post_max_size=8M



> 自动添加文件在 PHP 文档之前
>
> 自动前置文件

auto_prepend_file=



> 自动添加文件在 PHP 文档之后
>
> 自动追加文件

auto_append_file=



> 通过默认，PHP 将输出一个媒体类型使用这个内容类型头。
>
> 去禁用这个，只需设置它为空。
>
>
>
> PHP 的内置默认媒体类型是设置为 text/html 。
>
> 默认媒体类型

default_mimetype="text/html"



> PHP 的默认字符集是设置为 UTF-8 。
>
> 默认字符集

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



##### Fopen wrappers 文件打开封装

> 是否允许处理网址（例如 http:// 或 ftp://）作为文件。
>
> 允许打开远程文件

allow_url_fopen=On



> 是否允许包含或要求打开网址（像 http:// 或 ftp://）作为文件。
>
> 允许包含远程文件

allow_url_include=Off



> 默认超时对于插口基于流（秒）
>
> 默认插口超时

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



#### [browscap] 浏览器功能

> http://browscap.org/
>
> get_browser()
>
> 要使用绝对路径

browscap = extra/browscap.ini



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