Ubuntu Server安装图形界面全过程
https://blog.csdn.net/sunbaigui/article/details/6624110

为Ubuntu Server安装gnome图形桌面环境
http://blog.creke.net/696.html

1.进入图形界面
startx

2.安装提示
apt install xinit

3.安装桌面环境
apt install ubuntu-desktop

==================================
ubuntu 安装 php7.2
https://blog.csdn.net/qq_16885135/article/details/79747045

在 Ubuntu/Debian 下安装 PHP7.2
https://www.centos.bz/2017/12/%E5%9C%A8-ubuntu-debian-%E4%B8%8B%E5%AE%89%E8%A3%85-php7-2/

记Ubuntu 16.04 下配置 Nginx、PHP7、MySQL环境，以及多域名配置
https://juejin.im/post/5aab298ef265da23994e44dc

ubuntu上安装php7.0+nginx+mysql
https://my.oschina.net/hjchhx/blog/876335

Ubuntu 16.04 LTS 安装 Nginx/PHP 7/MySQL 5.7 (LEMP)
https://www.linuxidc.com/Linux/2016-05/131154.htm

1.安装并运行 nginx
apt install nginx
service nginx start

2.安装 php7.1
sudo apt-add-repository ppa:ondrej/php
apt install php7.1 php7.1-fpm

3.集成
location ~ \.php$ {
    fastcgi_pass unix:/run/php/php7.1-fpm.sock
}
