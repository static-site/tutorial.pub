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
    - ���һ���µ� Web ������չ����չ�� php��Ҫ����ļ� x:\php5\php5isapi.dll ������չ״̬Ϊ����
    - Ĭ����վ > ���� > ��Ŀ¼ > ���� > ���Ӧ�ó�����չ����չ�� php����ִ���ļ� x:\php5\php5isapi.dll


6. test
http://localhost/phpinfo.php

```php
<?php
phpinfo();
```

