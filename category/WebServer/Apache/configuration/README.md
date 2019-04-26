# Apache HTTP server configuration file

Define SRVROOT "D:/env/win/ProgramFiles/Apache24"



ServerRoot "${SRVROOT}"



Listen 127.0.0.1:80



#### Dynamic Shared Object (DSO) Support

LoadModule access_compat_module modules/mod_access_compat.so



```
<IfModule unixd_module>
User daemon
Group daemon
</IfModule>
```



ServerAdmin admin@example.com



ServerName 127.0.0.1



#### 目录和权限

```
<Directory />
AllowOverride none
Require all denied
</Directory>
```



DocumentRoot "${SRVROOT}/htdocs"

```
<Directory "${SRVROOT}/htdocs">
Options Indexes FollowSymLinks ExecCGI
AllowOverride All
Require all granted
</Directory>
```



```
<IfModule dir_module>
DirectoryIndex index.html index.php
</IfModule>
```



```
<Files ".ht*">
Require all denied
</Files>
```



#### 日志

ErrorLog "logs/error.log"

LogLevel warn

```
<IfModule log_config_module>
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b" common
  <IfModule logio_module>
  LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
  </IfModule>
CustomLog "logs/access.log" common
</IfModule>
```



#### 模块

```
<IfModule alias_module>
ScriptAlias /cgi-bin/ "${SRVROOT}/cgi-bin/"
</IfModule>
```



```
<IfModule cgid_module>
</IfModule>
```



```
<Directory "${SRVROOT}/cgi-bin">
AllowOverride None
Options None
Require all granted
</Directory>
```



```
<IfModule headers_module>
RequestHeader unset Proxy early
</IfModule>
```



```
<IfModule mime_module>
TypesConfig conf/mime.types
AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz
</IfModule>
```



#### Supplemental configuration

Include conf/extra/httpd-php.conf

Include conf/extra/httpd-vhosts.conf

```
<IfModule proxy_html_module>
Include conf/extra/proxy-html.conf
</IfModule>
```

```
<IfModule ssl_module>
SSLRandomSeed startup builtin
SSLRandomSeed connect builtin
</IfModule>
```

