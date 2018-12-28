## PHP_Setup_for_IIS6


1. download zip package
http://www.php.net/downloads.php
http://cn.php.net/distributions/php-5.1.4-Win32.zip


2. unzip
x:\php5


3. copy files
```sh
copy x:\php5\php5ts.dll %SystemRoot%\system32\php5ts.dll
copy x:\php5\php.ini-recommended %SystemRoot%\php.ini
```

4. config php.ini
```ini
extension_dir = "x:\php5\ext"
```

5. setup IIS
    - 添加一个新的 Web 服务扩展，扩展名 php，要求的文件 x:\php5\php5isapi.dll 设置扩展状态为允许
    - 默认网站 > 属性 > 主目录 > 配置 > 添加应用程序扩展，扩展名 php，可执行文件 x:\php5\php5isapi.dll


6. test
http://localhost/phpinfo.php

```php
<?php
phpinfo();
```

