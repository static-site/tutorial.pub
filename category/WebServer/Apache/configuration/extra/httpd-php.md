# httpd-php

LoadModule fcgid_module modules/mod_fcgid.so



```
<IfModule fcgid_module>
Include conf/extra/httpd-fcgid.conf
FcgidInitialEnv PHPRC "D:/env/win/ProgramFiles/php-7.3.0RC1-nts"
<Files ~ "\.php$">
  AddHandler fcgid-script .php
  FcgidWrapper "D:/env/win/ProgramFiles/php-7.3.0RC1-nts" .php
</Files>
</IfModule>
```
