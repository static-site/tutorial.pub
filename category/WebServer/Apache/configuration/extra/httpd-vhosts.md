# httpd-vhosts

#### 定义常量

Define WWWROOT "D:/env/www"



#### 本地 IP 和 8001

```
<VirtualHost *:80>
ServerAdmin webmaster@urlnk.com
DocumentRoot "${SRVROOT}/htdocs"
ServerName 127.0.0.1
ServerAlias www.dumy-host.example.com
ErrorLog "logs/127.0.0.1-error.log"
CustomLog "logs/127.0.0.1-access.log" common
</VirtualHost>
```



```
<VirtualHost *:8001>
DocumentRoot "${SRVROOT}/htdocs"
</VirtualHost>
```



#### 本地主机名和 8081

```
<VirtualHost *:80>
ServerAdmin webmaster@urlnk.com
DocumentRoot "${WWWROOT}"
ServerName localhost
ErrorLog "logs/localhost.err.log"
</VirtualHost>
```



#### 本地 IPv6 和 8801

```
<VirtualHost [${IPv6}]:80>
DocumentRoot "${SYNROOT}"
SetEnv RUNTIME_ENVIROMENT DEV
</VirtualHost>
```



#### 目录设置

```
<Directory "${WWWROOT}">
Options +Indexes +FollowSymLinks +ExecCGI
AllowOverride All
Order allow,deny
Allow from all
Require all granted
</Directory>
```

