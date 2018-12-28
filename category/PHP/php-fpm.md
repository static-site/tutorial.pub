# 命令行

**帮助**

Benny@Taurus /usr/sbin
$ ./php-fpm -h
```
Usage: php-fpm [-n] [-e] [-h] [-i] [-m] [-v] [-t] [-p <prefix>] [-g <pid>] [-c <file>]
  -c <path>|<file> Look for php.ini file in this directory
  -n               No php.ini file will be used
  -d foo[=bar]     Define INI entry foo with value 'bar'
  -e               Generate extended information for debugger/profiler
  -h               This help
  -i               PHP information
  -m               Show compiled in modules
  -v               Version number
  -p, --prefix <dir>
                   Specify alternative prefix path to FastCGI process manager (default
  -g, --pid <file>
                   Specify the PID file location.
  -y, --fpm-config <file>
                   Specify alternative path to FastCGI process manager config file.
  -t, --test       Test FPM configuration and exit
  -D, --daemonize  force to run in background, and ignore daemonize option from config
  -F, --nodaemonize
                   force to stay in foreground, and ignore daemonize option from confi
  -O, --force-stderr
                   force output to stderr in nodaemonize even if stderr is not a TTY
  -R, --allow-to-run-as-root
                   Allow pool to run as root (disabled by default)
```



# 配置

/etc/php-fpm.conf
```
[global]
pid = /var/run/php-fpm.pid
```

/etc/php-fpm.d/www.conf
```
[www]
listen = 0.0.0.0:9004
chdir = /srv/www/htdocs
access.log = /var/log/$pool.access.log
pm.status_path = /status
```

**参考**：

- [配置 - FastCGI 进程管理器（FPM）](http://php.net/manual/zh/install.fpm.configuration.php)



# 启动和关闭

**测试**
Benny@Taurus /usr/sbin
$ ./php-fpm -t -R
```
[21-Sep-2018 21:22:57] NOTICE: configuration file /etc/php-fpm.conf test is successful
```

**运行**
Benny@Taurus /usr/sbin
$ ./php-fpm -R


**查找映像**

Benny@Taurus ~
$ ps aux | grep php-fpm
```
     6324    5032    5032       6324  ?         197608 21:18:18 /usr/sbin/php-fp      m
     7156    5032    5032       7156  ?         197608 21:18:08 /usr/sbin/php-fp      m
     5032       1    5032       5032  ?         197608 21:09:22 /usr/sbin/php-fp      m
```

**结束进程**

Benny@Taurus ~
$ kill 5032


**关闭**

Benny@Taurus ~
> $ kill -INT `cat /var/run/php-fpm.pid`

**重启**
在未关闭的前提下有效
Benny@Taurus ~
> $ kill -USR2 `cat /var/run/php-fpm.pid`


