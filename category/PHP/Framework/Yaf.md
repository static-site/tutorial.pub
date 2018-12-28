Yet Another Framework(Yaf) 

http://www.laruence.com/manual/
http://php.net/manual/zh/yaf.appconfig.php

https://github.com/laruence/yaf-examples

http://pecl.php.net/package/yaf

2.2.9 PHP5.3，5.4，5.5（+x64）
2.3.2 +5.6
3.0.0 7.0
3.0.4 +7.1
3.0.5 +7.2

下载 和php对应版本
安装和 php 配置（主要是命名空间）
服务器配置重写
框架配置 conf.ini 模块 bootstrap composer


Yaf 类
目录结构
例子

控制器
请求

响应
视图、模板引擎

数据库适配
模型

命令行
COOKIE session
API RESTful GraphQL RPC

******************************
加载机制
默认
/controller/action/param_name/param_value



******************************
常量
[YAF\VERSION] => 3.0.7
[YAF\ENVIRON] => product yaf.environ php.ini 设置
[YAF\ERR\STARTUP_FAILED] => 512
[YAF\ERR\ROUTE_FAILED] => 513
[YAF\ERR\DISPATCH_FAILED] => 514
[YAF\ERR\AUTOLOAD_FAILED] => 520
[YAF\ERR\NOTFOUND\MODULE] => 515
[YAF\ERR\NOTFOUND\CONTROLLER] => 516
[YAF\ERR\NOTFOUND\ACTION] => 517
[YAF\ERR\NOTFOUND\VIEW] => 518
[YAF\ERR\CALL_FAILED] => 519
[YAF\ERR\TYPE_ERROR] => 521

*************************
php.ini 配置选项
;; PHP_INI_SYSTEM

[yaf]
; 默认控制器或动作优先 PATH_INFO
yaf.action_prefer = On

;; 缓存配置文件 3.0.7 无
yaf.cache_config = 1

; 环境名称
yaf.environ = test

; 最大嵌套深度
yaf.forward_limit = 5

; 全局类库的目录路径
yaf.library = K:\dev\php\library

; 类名目录路径小写
yaf.lowcase_path = On

; 类名分隔符
yaf.name_separator = '_'

; 类名后缀式
yaf.name_suffix = Off

; actions 额外的自动查找逻辑
yaf.st_compatible = Off

;; 开启命名空间
yaf.use_namespace = 1

; 开启自动加载
yaf.use_spl_autoload = 1

*******************************
application.ini 配置文件
必须
application.directory	String	应用的绝对目录路径

提倡
application.dispatcher.throwException	Bool	True	在出错的时候, 是否抛出异常
application.dispatcher.catchException	Bool	False	是否使用默认的异常捕获Controller, 如果开启, 在有未捕获的异常的时候, 控制权会交给ErrorController的errorAction方法, 可以通过$request->getException()获得此异常对象

application.modules	String	Index	声明存在的模块名, 请注意, 如果你要定义这个值, 一定要定义Index Module
application.dispatcher.defaultRoute string
默认路由，如果未指定，静态路由会被当做是默认路由，参见： Yaf_Router::addRoute()。


可选
application.view.ext	String	phtml	视图模板扩展名

application.library	String	application.directory + "/library"	本地(自身)类库的绝对目录地址
Yaf2.1.6以后，该配置项也可以是一个数组
application.library.directory string Alias of application.library. Introduced in Yaf 2.1.6

application.library.namespace string  逗号分隔的本地类库命名空间前缀。


application.bootstrap	String	Bootstrapplication.php	Bootstrap路径(绝对路径)

application.system.*	String	*	通过这个属性, 可以修改yaf的runtime configure, 比如application.system.lowcase_path, 但是请注意只有PHP_INI_ALL的配置项才可以在这里被修改, 此选项从2.2.0开始引入

多劳不多得
application.dispatcher.defaultModule	String	index	默认的模块
application.dispatcher.defaultController	String	index	默认的控制器
application.dispatcher.defaultAction	String	index	默认的动作

多余
application.baseUri	String	NULL	在路由中, 需要忽略的路径前缀, 一般不需要设置, Yaf会自动判断.

; 完全没必要
application.ext	String	php	PHP脚本的扩展名


**************************
final Yaf\Application {
	protected $config
	$_environ
	$_modules
	$dispatcher
	::$_app
	
	$_running
	
	$_err_no
	$_err_msg
	
	
	public __constrcut($config, $environ)
	getAppDirectory()
	setAppDirectory()
	
	
	getConfig()
	environ()
	getModules()
	getDispatcher()
	::app()
	
	
	bootstrap(Yaf\Bootstrap_Abstract)
	run()
	execute(callback $entry, $...)
	
	getLastErrorNo()
	getLastErrorMsg()
	clearLastError()
	
	__destruct()
	private __clone()
	private __sleep()
	private __wakeup()
}

abstract class Yaf_Bootstrap_Abstract { 
	/* constants */
	/* properties */
	/* methods */
}

final Yaf\Dispatcher {
	protected $plugins
	$_router
	$_request
	$_view
	
	$_auto_render = 1
	$_return_response
	$_instantly_flush
	
	$_default_module
	$_default_contrller
	$_default_action
	
	::$_instance
	
	private __construct()
	private __clone()
	private __sleep()
	private __wakeup()
	
	public getApplication()
	
	registerPlugin($plugin)
	getRouter()
	getRequest()
	setRequest($request)
	dispatch($request)
	
	setView(Yaf_View_Interface $view)
	initView($template_dir, $options)
	enableView()
	disableView()
	
	autoRender($flag)
	returnResponse($flag)
	flushInstantly($flag)
	
	setDefaultModule($module)
	setDefaultController($controller)
	setDefaultAction($action)
	
	::getInstance()
	
	setErrorHandler($callback, $error_types)
	throwException($flag = NULL)
	catchException($flag = NULL) 
}

*****************************
代码生成工具
https://github.com/laruence/php-yaf/tree/master/tools/cg

---------------
目录结构
public
	index.php
conf
	application.ini
application
	controllers
		Error.php
	actions
		路径只有1个时生效
		
**************************
Rewrite rules

Apache

#.htaccess
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule .* index.php

Nginx

server {
  listen ****;
  server_name  domain.com;
  root   document_root;
  index  index.php index.html index.htm;
 
  if (!-e $request_filename) {
    rewrite ^/(.*)  /index.php/$1 last;
  }
}

Lighttpd

$HTTP["host"] =~ "(www.)?domain.com$" {
  url.rewrite = (
     "^/(.+)/?$"  => "/index.php/$1",
  )
}
		
****************************
命令行中使用
$ php request.php  "request_uir=/index/hello"
 
$app = new Yaf_Application("conf.ini");
$app->getDispatcher()->dispatch(new Yaf_Request_Simple());

$request = new Yaf_Request_Simple("CLI", "Index", "Controller", "Hello", array("para" => 2));
		
*******************************
视图渲染

Yaf\Dispatcher::getInstance()->disableView();

----------------------------------
控制器中给视图模板变量赋值

$this->getView()->assign("content", "Hello World");
$this->_view->test = 'hi';

**********
参考文档
http://www.laruence.com/manual/
https://www.kancloud.cn/chunice/yaf-php7/428436
https://www.kancloud.cn/liustone/yaf-note/84332

2015-1    http://www.01happy.com/php-yaf-ext-preface/

*****************
例子
==========

基本
https://github.com/laruence/yaf-examples
https://github.com/jsyzchen/chen-yaf
https://github.com/melonwool/YafUse
2016-10   https://github.com/xwmhmily/YOF
2015-8    https://github.com/zxcvdavid/yaf-light-frame


功能
4-2       https://github.com/yumufeng/thinkyaf
2-8       https://github.com/molaifeng/yaf_eloquent
2017-10   https://github.com/cdoco/yaf-ext
2017-8    https://github.com/ifintech/phplib
2017-6    https://github.com/codejm/yaf_base
2016-10   https://github.com/zfeig/yafapi
2016-8    https://gitee.com/iceup/yaf-ext
2016-5    https://github.com/jimmydong/Yaf
2015-6    https://github.com/xudianyang/Yaf.Global.Library
2014-6    https://github.com/rhyzx/php-yaf-extras
https://github.com/sillydong/CZD_Yaf_Extension
https://github.com/Neeke/Yaf.Scaffold
https://github.com/akDeveloper/yaf_base_application

完整
2018-3    https://github.com/chuanhaisoft/ChuanHaiShop-php-yaf
2016-5    https://github.com/loncool/yaf-admin
https://github.com/xudianyang/yaf.app
https://github.com/yantze/yaf
https://github.com/suliang/Yaf-Blog
https://github.com/LucasRosa90/Yaf-CMS

增强
2017-10   https://github.com/gnpok/yafApi
2016-4    https://github.com/rryqszq4/yaf-lib
https://github.com/wenjun1055/swoole-yaf
https://github.com/LinkedDestiny/swoole-yaf

开发
https://github.com/elad-yosifon/php-yaf-doc
https://github.com/xudianyang/yaf.auto.complete

测试
2017-3    https://github.com/lancerhe/yaf-phpunit
2014-2    https://github.com/chenjiebin/yaf-phpunit-test
https://github.com/mzsolti/yaf-phpport
https://github.com/warmans/Yaf-PHP-Example
