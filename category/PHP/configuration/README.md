# php.ini 中文版



## [PHP]

主要设置



### About php.ini

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



### About this file



### Quick Reference



### php.ini Options

配置文件选项



#### 用户配置 - 文件名

```ini
; 用户定义的 php.ini (.htaccess) 文件名称。默认是 ".user.ini"
; 设置此项为空值来禁用此功能
user_ini.filename = ".user.ini"
```



#### 用户配置 - 缓存时间

```ini
; 用户定义的 php.ini 文件存活时间 (time-to-live) 秒数。
; 默认是 300 秒（5 分钟）
user_ini.cache_ttl = 300
```



### Language Options

语言选项



engine=On



#### 短开始标签

```ini
; 此指令决定 PHP 是否辨认 <? 和 ?> 之间的代码，作为 PHP 源处理。
; 通常推荐 <?php 和 ?> 并禁用此功能，启用它可能导致生成 XML 文档时出现问题，向后兼容的原因仍然支持此功能。
; 注意此指令不控制 <?= 速记标记，无论该指令如何均可使用。
; 默认值：On
; 开发环境值：Off
; 生产环境值：Off
short_open_tag = Off
```



#### 精确

```ini
; 浮点数中显示的有效位数。
; -1 表示将使用舍入此类数字的增强算法。
precision = 14
```



#### 输出缓冲

```ini
; 输出缓冲是一种机制，在推送数据到客户端之前，PHP 在内部将保留多少输出数据（不包括消息头和 Cookies）。
; 如果你的应用输出超过这个设置，PHP 将以大约你指定大小的块发送数据。
; 开启此设置并管理它的最大缓冲大小可能会产生一些有趣的副作用，取决于你的应用和网页服务器。
; 你也许可以发送消息头和 Cookies 在你通过 print 或 echo 已经发送输出之后。
; 如果你的服务器由于缓冲输出而发送的数据包少于 PHP 在获得输出流式传输的结果，那么你可能还会看到性能优势。
; 在产品服务器上，出于性能原因，4069 字节是一个很好的设置。
; 注意：输出缓冲也可以通过输出缓冲控制函数进行控制。
; 可能的值：
;   On = 启用且缓冲不受限制。（谨慎使用）
;   Off = 禁用
;   整数 = 启用缓冲并设置最大值（以字节为单位）。
; 注意：在命令行 SAPI 此指令硬编码为 Off
; 默认值：Off
; 开发环境值：4096
; 生产环境值：4096
output_buffering = 4096
```



#### 输出处理

```ini
; 你可以把脚本的所有输出转到一个函数。
; 例如，你设置 output_handler 为 “mb_output_handler”，字符编码将透明地转换为指定的编码。
; 设置任何输出处理程序将自动开启输出缓冲。
; 注意：编写可移植脚本的人不应该依赖于此 ini 指令。而是使用 ob_start() 显式设置输出处理程序。
;   除非你知道脚本在做什么，否则使用此 ini 指令可能会导致问题。
; 注意：你不能同时使用 “mb_output_handler” 和 “ob_iconv_handler”，
;   也不能同时使用 “ob_gzhandler” 和 “zlib.output_compression”。
output_handler =
```



zlib.output_compression=Off



#### 隐式刷新

```ini
; 隐式刷新让 PHP 告诉输出层在每个输出块之后自动刷新自身。
; 这样等同于每次调用 print() 或 echo() 及 HTML 块之后调用 PHP 函数 flush()。
; 开启这个选项严重影响性能所以通常建议仅仅为了调试目的。
; 注意：这个指令在命令行 SAPI 硬编码为 On。
implicit_flush = Off
```

> ob_implicit_flush()



#### 反序列化回调函数

```ini
; 反序列化回调函数将被调用（用未定义类名作为参数），如果反序列化器找到未定义类将被实例化。
; 如果规定函数未定义，或此函数不能包含实现缺少的类，将出现一个警告。
; 如果确实要实现这样的回调函数，请仅设置此条目。
unserialize_callback_func =
```

> unserialize()



#### 反序列化最大深度

```ini
; 此选项规定反序列化结构默认深度限制。
; 深度限制设置太高可能导致反序列化过程中堆栈溢出。
; 单个 unserialize() 调用的最大深度选项将覆盖此项设置。
; 值为 0 将禁用深度限制。
unserialize_max_depth = 4096
```



#### 序列化精度

```ini
; 序列化单精度和双精度浮点数时，在浮点数之后存储 serialize_precision 有效数字。
; 缺省值确保 unserialize 解码浮点数时，数据保持不变。编码双精度值时，该值还用于 json_encode。
; 如果使用 -1，则使用 dtoa 模式 0，自动选择最佳精度。
serialize_precision = -1
```



#### 打开基本目录

```ini
; 如果设置了 open_basedir 限制所有文件操作在定义的目录及以下。
; 如果在每个目录或每个虚拟主机的网页服务器配置文件中使用此指令，则最有意义。
; 注意：禁用 realpath 缓存
open_basedir =
```



#### 禁用函数

```ini
; 这个指令允许你去禁用某些函数。
; 它接受一个逗号分隔的函数名列表。
disable_functions =
```



#### 禁用类

```ini
; 这个指令允许你去禁用某些类。
; 它接受一个逗号分隔的类名列表。
disable_classes =
```



#### 语法高亮

```ini
; 语法高亮模式的颜色
; 设置为 <span style="color: ???????"> 中任何可接受的代码将可用。
highlight.string  = #DD0000
highlight.comment = #FF9900
highlight.keyword = #007700
highlight.default = #0000BB
highlight.html    = #000000
```

> highlight_file()
>
> highlight_string()



#### 忽略用户中止

```ini
; 如果启用，请求将允许被完成即使用户取消这个请求。
; 如果执行长请求可以考虑启用它，最终可能会被用户中断或浏览器超时。
; PHP 的默认行为是禁用此功能。
ignore_user_abort = On
```

> ignore_user_abort()



#### 真实路径缓存大小

```ini
; 决定 PHP 将使用的 realpath 缓存大小。
; 在 PHP 打开许多文件以反映已执行文件操作的数量的系统上，应增加该值。
; 注意：如果设置了 open_basedir 此缓存将被禁用
realpath_cache_size = 4096k
```



#### 真实路径缓存时长

```ini
; 持续时间（单位秒），用于缓存 realpath 给定文件或目录的信息。
; 对于很少更改文件的系统，考虑增加此值。
realpath_cache_ttl = 120
```



zend.enable_gc=On



### Miscellaneous

其它杂项



#### 公开 PHP 签名

```ini
; 决定 PHP 是否可以公开它已安装在服务器上的事实
; （例如通过添加其签名到网页服务器头信息）。
; 这样没有任何安全威胁，但这样可使它能够确定你是否在自己的服务器上使用 PHP。
expose_php = On
```





### Resource Limits

资源限制



#### 最大执行时间

```ini
; 每个脚本的最大执行时间，单位秒
; 注意：对于命令行 SAPI，此指令硬编码为 0
max_execution_time = 30
```



#### 最大输入时间

```ini
; 每个脚本可用于分析请求数据的最长时间。
; 最好在生产服务器上限制此时间，以消除运行时间过长的脚本。
; 注意：在命令行 SAPI 此指令硬编码为 -1
; 默认值：-1（无限制）
; 开发环境值：60（60秒）
; 生产环境值：60（60秒）
max_input_time = 60
```



#### 最大输入嵌套级别

```ini
; 最大输入变量嵌套级别
max_input_nesting_level = 64
```



#### 最大输入变量

```ini
; 可以接受多少个 GET/POST/COOKIE 输入变量
max_input_vars = 1000
```



#### 内存限制

```ini
; 一个脚本可以消耗的最大内存数
memory_limit = 128M
```



### Error handling and logging

错误处理和记录



#### 错误报告

```ini
; 该指令通知 PHP 您希望采取哪些错误、警告和注意。
error_reporting = E_ALL
```



#### 显示错误

```ini
; 该指令控制是否以及 PHP 将在哪里输出错误、通知和警告。
; 错误输出是非常有用的在开发中，
; 但它可能非常危险在生产环境。
; 取决于代码哪一个触发错误，敏感信息可能从你的应用中潜在泄露，
; 例如数据库用户名和密码，或更糟糕。
; 对于生产环境，我们建议记录错误而不是发送它们到标准输出 。
; 可用的值：
;   Off = 不显示任何错误
;   stderr = 显示错误到标准错误（仅影响 CGI/CLI 二进制文件！）
;   On 或 stdout = 显示错误到标准输出
; 默认值：On
; 开发环境值：On
; 生产环境值：Off
display_errors = On
```



#### 显示启动错误

```ini
; 显示错误哪一个发生在 PHP 的启动过程分别处理和 display_errors 。
; PHP 的默认行为抑制从客户端导致的那些错误。
; 打开启动错误显示在调试配置问题中很有用。
; 我们强烈建议你设置为 “off” 对于生产服务器。
; 默认值：Off
; 开发环境值：On
; 生产环境值：Off
display_starup_errors = On
```



#### 记录错误

```ini
; 除了显示错误之外，PHP 还可以记录错误到位置，例如服务器特定的日志、STDERR，
; 或者由下面的 error_log 指令设定的位置。
; 尽管错误不应在生产服务器上显示，但仍应对其进行监控，并且日志记录是实现此目的的一种好方法。
; 默认值：Off
; 开发环境值：On
; 生产环境值：On
log_errors = On
```



#### 记录错误最大长度

```ini
; 设定 log_errors 的最大长度。在 error_log 中添加了有关源的信息。
; 默认是 1024，0 允许不做最大长度限制。
log_errors_max_len = 1024
```



#### 忽略重复错误

```ini
; 不记录重复消息。
; 重复的错误必须出现在同一个文件中的同一行代码上，除非 ignore_repeated_errors 设为真。
ignore_repeated_errors = Off
```



#### 忽略重复源

```ini
; 忽略重复消息时也忽略消息的来源。
; 如果设置为 On 将不记录重复的错误消息从不同的文件或源码行产生。
ignore_repeated_source = Off
```



#### 报告内存泄露

```ini
; 如果此参数设置为 Off，则不会显示内存泄露（在 stdout 或日志中）。
; 这仅在调试编译中有效，或者如果错误报告在允许的列表中包含 E_WARNING
report_memleaks = On
```



#### 报告 Zend 调试

```ini
; 此设置默认开启
report_zend_debug = 0
```



#### 跟踪错误

```ini
; 存储最后的错误或警告在 $php_errormsg 里。
; 此指令已经废弃（PHP 7.2.0）。
; 默认值：Off
; 开发环境值：Off
; 生产环境值：Off
track_errors = Off
```



#### 以 HTML 显示错误

```ini
; 当 PHP 显示或记录错误时，它可以格式化错误消息为 HTML 便于易读。
; 此指令控制是否将错误消息格式化为 HTML。
; 注意：命令行 SAPI 中此指令硬编码为 Off
html_errors = On
```



#### 参考文档根

```ini
; 如果 html_errors 设置为 On 并且 docref_root 不为空，
; PHP 产生可点击错误消息直接到页面描述的错误或函数引起的错误详情。
; 你可以从 http://php.net/docs 下载 PHP 手册的拷贝
; 并且改变 docref_root 到你的本地拷贝包括开头 “/”  的基本网址。
; 你必须同时指定文件扩展名包括点。
; PHP 的默认行为是让这些设置为空，每个案例中不产生链接到文档。
; 注意：切勿使用此特征用于生产环境。
docref_root = "/phpmanual/"
```



#### 参考文档扩展名

```ini
docref_ext = ".html"
```



#### 错误信息前置字符串

```ini
; 输出到错误信息前面的字符串。
; PHP 默认设置为空白。
error_prepend_string = "<span style='color: #ff0000'>"
```



#### 错误信息追加字符串

```ini
; 输出到错误信息后面的字符串。
; PHP 默认设置为空白。
error_append_string = "</span>"
```



#### 错误日志

```ini
; 记录错误到指定的文件。
; PHP 默认为空值。
; 示例：
; 记录错误到 syslog（Windows 事件日志）
;error_log = syslog
error_log = php_errors.log
```



#### 系统日志 - 前缀

```ini
; 记录到 syslog 的每条消息的前置字符串。
; 仅在 error_log 设置为 syslog 时使用。
syslog.ident = php
```



#### 系统日志 - 类型

```ini
; 指定记录消息的程序类型。
; 仅在 error_log 设置为 syslog 时使用。
syslog.facility = user
```



#### 系统日志 - 过滤

```ini
; 设置此选项禁用过滤控制字符（默认）。
; 一些记录器仅接受 NVT-ASCII，而另一些接受任何非控制字符。
; 如果你的记录器接受所有，则根本无需过滤。
; 允许的值：
;   ascii 所有可打印 ASCII 字符和 NL
;   no-ctrl 控制字符以外所有字符
;   all 所有字符
;   raw 像 all 一样，但是消息在换行符之间不会分割
syslog.filter = ascii
```



#### WINDOWS - 显示 CRT 警告

```ini
; 默认值：0
; 开发环境值：0
; 生产环境值：0
windows.show_crt_warning = 0
```



### Data Handling

数据处理



#### 参数分隔符 - 输出

```ini
; 使用这个分隔符去分开在 PHP 里面生成的网址参数。
; PHP 的默认设置是 “&”。
arg_separator.output = "\&amp;"
```



#### 参数分隔符 - 输入

```ini
; 分隔符列表用于  PHP 去解析输入的网址到变量。
; PHP 的默认设置是 “&”。
; 注意：每个字符在这个指令是考虑过作为分隔符。
arg_separator.input = ";&"
```



#### 全局变量顺序

```ini
; 此指令决定 PHP 启动时注册哪些超全局数组。
; G,P,C,E 和 S 是超全局变量 GET, POST, COOKIE, ENV 和 SERVER 对应的缩写。
; 注册这些数组会损失性能，并且因为 ENV 不像其他那样常用，不推荐在生产服务器上使用。
; 你仍然可以通过 getenv() 访问你需要的环境变量。
; 默认值："EGPCS"
; 开发环境值："GPCS"
; 生产环境值："GPCS"
variables_order = "GPCS"
```



#### 请求变量顺序

```ini
; 此指令决定哪些超全局数据（G,P & C）将被注册到超全局数组 REQUEST。同时决定注册数据的顺序。
; 该指令的值以与 variables_order 指令相同的方式指定，除非仅一个。
; 此值为空 PHP 将使用 variables_order 指令中设置的值。这不意味着超全局数组 REQUEST 为空。
; 默认值：无
; 开发环境值："GP"
; 生产环境值："GP"
request_order = "GP"
```



#### 注册参数变量

```ini
; 此指令决定 PHP 运行时是否注册 $argv 和 $argc。
; $argv 包含调用脚本时传递到 PHP 所有参数的数组。
; $argc 包含调用脚本时传递的参数数量表示的整数。
; 从命令行运行脚本时这些数组极其有用。
; 此指令启用时，每当脚本执行时注册这些变量消耗 CPU 和内存。性能原因，产品服务器上应禁用此功能。
; 注意：CLI SAPI 此指令硬编码为 On
; 默认值：On
; 开发环境值：Off
; 生产环境值：Off
register_argc_argv = Off
```



#### 自动全局变量使用即时化技术

```ini
; 启用后，ENV, REQUEST 和 SERVER 变量被创建当他们在第一次使用（即时化技术），而不是当这个脚本运行时。
; 如果这些变量在一个脚本里不使用，这个指令将获得性能效果。
; PHP 指令 register_argc_argv 必须被禁用，此指令才能生效。
auto_globals_jit = On
```



#### 启用 POST 数据读取

```ini
; PHP 是否读取 POST 数据。
; 此选项默认启用。
; 想必，你不想全局禁用此选项。
; 它导致 $_POST 和 $_FILES 总是为空；你想要读取 POST 数据只能通过 php://input 流封装的方式。
; 在内存效率上代理请求或处理 POST 数据这样的方式很有用。
enable_post_data_reading = Off
```



#### 表单最大大小

```ini
; PHP 将接受的表单数据最大大小。
; 它的值可以是 0 以禁用限制。如果通过 enable_post_data_reading 禁用了 POST 数据读取，则将忽略它。
post_max_size = 8M
```



#### 自动前置文件

```ini
; 自动添加文件在 PHP 文档之前
auto_prepend_file =
```



#### 自动追加文件

```ini
; 自动添加文件在 PHP 文档之后
auto_append_file =
```



#### 默认媒体类型

```ini
; 通过默认，PHP 将输出一个媒体类型使用这个内容类型头。
; 去禁用这个，只需设置它为空。
; PHP 的内置默认媒体类型是设置为 text/html 。
default_mimetype = "text/html"
```



#### 默认字符集

```ini
; PHP 的默认字符集是设置为 UTF-8 。
default_charset = "UTF-8"
```



#### 内部编码

```ini
; PHP 内部编码设置为空。
; 如果空，使用 default_charset。
; 从 PHP 5.6.0 起可用。此设置用于 mbstring 和 iconv 等多字节模块。
internal_encoding =
```



#### 输入编码

```ini
; PHP 输入编码设置为空。
; 如果空，使用 default_charset。
inpput_encoding =
```



#### 输出编码

```ini
; PHP 输出编码设置为空。
; 如果空，使用 default_charset。
output_encoding =
```



### Path and Directories

路径和目录



#### 包含路径

```ini
; UNIX: "/path1:/path2"
;include_path = ".:/php/includes"
;include_path = ".:${USER}/pear/php"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\php\includes"
;
; PHP 默认设置是 ".;/path/to/php/pear"
include_path = ".;C:\php\pear"
```

> set_include_path()
>
> require()
>
> include()
>
> fopen()
>
> file()
>
> readfile()
>
> file_get_contents()



#### 文档根

```ini
; PHP 页的根目录，仅在非空时使用。
; 如果 PHP 编译时没有用 FORCE_REDIRECT，
; 如果你运行 PHP 作为 CGI 运行于任何网页服务器（除 IIS）你应该设置 doc_root
; 参见文档中安全问题。下面的 cgi.force_redirect 配置作为备用
doc_root =
```



#### 用户目录

```ini
; 非空情况下，PHP 使用 /~username 打开此目录下的脚本。
user_dir = public_php
```



#### 扩展目录

```ini
; 可加载扩展（模块）存放在哪一个目录。
; 在 Windows：
;extension_dir = "ext"
extension_dir = "./"
```



#### 系统临时目录

```ini
; 临时文件将存放的目录位置。
; 默认为系统默认
sys_temp_dir = "/tmp"
```

> sys_get_temp_dir()



#### 启用 dl 函数

```ini
; 是否让 dl() 函数可用。
; dl() 函数不能很好运行于多线程服务器，比如 IIS 或 Zeus，并且使用它们时是自动禁用的。
enable_dl = Off
```



### File Uploads

文件上传



#### 开启文件上传

```ini
; 是否允许 HTTP 文件上传。
file_uploads = On
```



#### 上传临时目录

```ini
; HTTP 上传文件的临时目录（如未指定，将使用系统默认值）。
upload_tmp_dir =
```



#### 上传最大文件大小

```ini
; 上传文件的最大允许大小。
upload_max_filesize = 2M
```



#### 最大文件上传数

```ini
; 单个请求可以上传文件的最大数量
max_file_uploads = 20
```



### Fopen wrappers

文件打开封装



#### 允许打开远程文件

```ini
; 是否允许处理网址（例如 http:// 或 ftp://）作为文件。
allow_url_fopen = On
```



#### 允许包含远程文件

```ini
; 是否允许包含或要求打开网址（像 http:// 或 ftp://）作为文件。
allow_url_include = Off
```



#### 默认 Socket 超时

```ini
; 默认超时对于插口基于流（秒）
default_socket_timeout = 60
```



### INI 文件中未列出



#### [hard_timeout](https://www.php.net/manual/zh/ini.core.php#ini.hard-timeout)

```ini
hard_timeout = 2
```



### Dynamic Extensions

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



## Module Settings

扩展模块设置



### [CLI Server]

#### 命令行服务器 - 颜色

```ini
; 命令行网页服务器是否使用 ANSI 颜色编码在终端输出。
cli_server.color = On
```

> 试过貌似没效果



### [Date]

### [filter]



### [iconv]

字符转换



#### 字符转换 - 输入编码

```ini
; 此 INI 条目已经从 PHP 5.6.0 起弃用。使用全局 input_encoding 替代。
; 如为空，则使用 default_charset 或 input_encoding 或 iconv.input_encoding。
; 优先权：default_charset < input_encoding < iconv.input_encoding
iconv.input_encoding =
```

> iconv_set_encoding()



#### 字符转换 - 内部编码

```ini
; 此 INI 条目已经弃用。使用全局 internal_encoding 替代。
; 如为空，则使用 default_charset 或 internal_encoding 或 iconv.internal_encoding。
; 优先权：default_charset < internal_encoding < iconv.internal_encoding
iconv.internal_encoding =
```



#### 字符转换 - 输出编码

```ini
; 此 INI 条目已经弃用。使用全局 output_encoding 替代。
; 如为空，则使用 default_charset 或 output_encoding 或 iconv.output_encoding。
; 优先权：default_charset < output_encoding < iconv.output_encoding
; 要使用输出编码转换，iconv 的输出处理程序必须设置，否则无法执行输出编码转换。
iconv.output_encoding =
```



### [intl]

### [sqlite3]

### [Pcre]

### [Pdo]

### [Pdo_mysql]



### [Phar]

PHP 存档



```ini
phar.readonly = On
```



```ini
; 强制归档文件包含签名
phar.require_hash = On
```



```ini
; 网页服务器启动时预先解析映射的归档文件
phar.cache_list = C:\path\to\phar1.phar;C:\path\to\phar2.phar
```



### [mail function]

邮件函数



#### SMTP 服务器地址

```ini
; 仅用于 Windows。
SMTP = localhost
```



#### SMTP 服务器端口

```ini
smtp_port = 25
```



#### 邮件发送人地址

```ini
; 仅用于 Windows。
sendmail_from = me@example.com
```



#### 邮件发送路径

```ini
; 仅用于 UNIX。你也可以提供参数（默认：“sendmail -t -i”）。
sendmail_path =
```



#### 邮件 - 强制额外参数

```ini
; 强制将指定参数的添加作为额外参数传递给 sendmail 二进制文件。
; 即使在安全模式下，这些参数也始终替换 mail() 的第五个参数的值。
mail.force_extra_parameters =
```



#### 邮件 - 添加自定义消息头

```ini
; 添加 X-PHP-Originating-Script：包含脚本的 UID 和文件名
mail.add_x_header = Off
```



#### 邮件 - 日志

```ini
; 将记录所有 mail() 调用的日志文件路径。
; 日志条目包括脚本的完整路径、行号、收件人地址和标题。
; 记录邮件日志到 syslog（Windows 事件日志）。
;mail.log = syslog
mail.log =
```



### [ODBC]

odbc.allow_persistent=On

odbc.check_persistent=On

odbc.max_persistent=-1

odbc.max_links=-1

odbc.defaultlrl=4096

odbc.defaultbinmode=1

### [Interbase]

ibase.allow_persistent=1

ibase.max_persistent=-1

ibase.max_links=-1

ibase.timestatmpformat="%Y-%m-%d %H:$M:%S"

ibase.dateformat="%Y-%m-%d"

ibase.timeformat="%H:%M:%S"

### [MySQLi]

mysqli.max_persistent=-1

mysqli.allow_persistent=On

mysqli.max_links=-1

mysqli.default_port=3306

mysqli.default_socket=

mysqli.default_host=

mysqli.default_user=

mysqli.default_pw=

mysqli.reconnect=Off

### [mysqlnd]

mysqlnd.collect_statistics=On

mysqlnd.collect_memory_statistics=On

### [OCI8]

### [PostgreSQL]

pgsql.allow_persistent=On

pgsql.auto_reset_persistent=Off

pgsql.max_persistent=-1

pgsql.max_links=-1

pgsql.ignore_notice=0

pgsql.log_notice=0

### [bcmath]

bcmath.scale=0



### [browscap]

浏览器功能

> http://browscap.org/
>
> get_browser()
>
> 要使用绝对路径

browscap = extra/browscap.ini



### [Session]

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

### [Assertion]

zend.assertions=1

### [COM]

### [mbstring]

### [gd]

### [exif]

### [Tidy]

tidy.clean_output=Off

### [soap]

soap.wsdl_cache_enabled=1

soap.wsdl_cache_dir="/tmp"

soap.wsdl_cache_ttl=86400

soap.wsdl_cache_limit=5

### [sysvshm]

### [ldap]

ldap.max_links=-1

### [dba]

### [opcache]

zend_extension="D:/env/win/ProgramFiles/php-7.3.0/ext/php_opcache.dll"

opcache.enable=1

opcache.enable_cli=1

### [curl]

curl.cainfo=

### [openssl]

openssl.cafile=D:/env/www/legend/dist/https/curl.haxx.se/ca/cacert.pem

openssl.capath=

### [Xdebug]

zend_extension=E:\env\win\ProgramData\php\ext\x64\ts\7.3\php_xdebug-2.8.0alpha1-7.3-vc15-x86_64.dll
xdebug.profiler_enable=On
xdebug.profiler_output_dir=E:\env\tmp\php\xdebug
xdebug.trace_output_dir=E:\env\tmp\php\xdebug