https://docs.phalconphp.com/zh/latest/
http://phalcon.ipanta.com/
https://github.com/netstu/phalcondocs/blob/master/zh/index.rst
http://www.iphalcon.cn/

http://phalconphp.org/


下载:
https://phalconphp.com/zh/download/windows
*3.0.4 - PHP5.5（+x64），5.6，7.0

安装:
php.ini
extension=php_phalcon.dll

创建：
目录结构
test/
  app/
    controllers/
    models/
    views/
  public/
    css/
    img/
    js/
    index.php

Aphace Httpd
.htaccess
# test/.htaccess

<IfModule mod_rewrite.c>
    RewriteEngine on
    RewriteRule  ^$ public/    [L]
    RewriteRule  ((?s).*) public/$1 [L]
</IfModule>
# test/public/.htaccess

<IfModule mod_rewrite.c>
    RewriteEngine On
    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^((?s).*)$ index.php?_url=/$1 [QSA,L]
</IfModule>

或httpd.conf
<IfModule mod_rewrite.c>

    <Directory "/var/www/test">
        RewriteEngine on
        RewriteRule  ^$ public/    [L]
        RewriteRule  ((?s).*) public/$1 [L]
    </Directory>

    <Directory "/var/www/test/public">
        RewriteEngine On
        RewriteCond %{REQUEST_FILENAME} !-d
        RewriteCond %{REQUEST_FILENAME} !-f
        RewriteRule ^((?s).*)$ index.php?_url=/$1 [QSA,L]
    </Directory>

</IfModule>

使用PHP内置的web服务器:
php -S localhost:8000 -t /public .htrouter.php

Phalcon 开发工具:
https://github.com/phalcon/phalcon-devtools
http://www.iphalcon.cn/reference/tools.html

例子：
https://github.com/phalcon/tutorial
https://github.com/phalcon/invo
https://github.com/phalcon/vokuro