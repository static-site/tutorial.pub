D:\ProgramFiles\MongoDB\Server\3.4\bin

mongod --logpath "D:\Program_Data\MongoDB-x64\log\MongoDB.log" --logappend --dbpath "D:\Program_Data\MongoDB-x64\db" --directoryperdb --serviceName "MongoDB" --serviceDisplayName "MongoDB3.4.2" --install

G:\Program_Files\mongodb-win32-i386-2.6.6\bin\mongod.exe --dbpath=G:\Program_Data\MongoDB\db --logpath=G:\Program_Data\MongoDB\log\MongoDB.log --journal --service

mongod --config D:\Program_Data\MongoDB-x64\MongoDB.ini --install


安装:
mongod -h
http://www.cnblogs.com/liuzhiying/p/5915741.html
http://blog.csdn.net/u010874036/article/details/51921206

命令：
https://docs.mongodb.com/manual/reference/command/

PHP 扩展:

http://pecl.php.net/package/mongodb 

https://docs.mongodb.com/php-library/master/tutorial/crud/
https://docs.mongodb.com/ecosystem/drivers/php/


http://soft.urlnk.com/php
http://soft.urlnk.com/php/ext
http://soft.urlnk.com/php/ext/mongodb

工具：
http://mongodb-tools.com/
https://docs.mongodb.com/ecosystem/tools/administration-interfaces/
https://mongodb-documentation.readthedocs.io/en/latest/ecosystem/tools/administration-interfaces.html

php_mongo:
http://www.phpmoadmin.com/
 => https://github.com/MongoDB-Rox/phpMoAdmin-MongoDB-Admin-Tool-for-PHP
https://github.com/bobthecow/genghis
https://github.com/iwind/rockmongo
https://github.com/jwage/php-mongodb-admin
https://github.com/argon/Opricot-MongoConsole
https://github.com/lovetheidea/MoaDB
http://www.mongoadmin.org/


配置文件:
https://my.oschina.net/pwd/blog/399374


权限验证:
https://docs.mongodb.com/manual/reference/method/db.createUser/

db.createUser(
   {
     user: "root",
     pwd: "root",
     roles:
       [
         { role: "readWrite", db: "config" },
         "clusterAdmin"
       ]
   }
)

http://www.cnblogs.com/zengen/archive/2011/04/23/2025722.html

文档参考：
https://mongodb-documentation.readthedocs.io
http://www.cnblogs.com/xinghebuluo/category/338660.html
http://lovelace.blog.51cto.com/1028430/1440988