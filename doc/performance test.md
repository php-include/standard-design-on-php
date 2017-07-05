# 性能分析，提高你的代码质量

对你的代码进行性能分析，是我们需要建立的一个共识。
一般作为一个phper,你需要掌握Apache的ab压力测试工具，和使用XHProf等PHP扩展来实现非入侵式性能监控。你需要对你的代码性能非常了解。
下面介绍我们需要了解得性能测试要点.
---- 
ab压力测试：Apache服务器自带了ab压力测试工具，可以用来测试网站性能，使用简单方便。
 
 1、打开Apache服务器的安装路径，在bin目录中有一个ab.exe的可执行程序，该程序就是ab压力测试工具，需要在终端执行，直接双击无法运行。
例如 D：documentsapachebinab
 
2、ab 的用法是：ab [options](#) [http://](#)hostname[:port](#)/path
-n ：总共的请求执行数；
-c： 并发数；
-t：测试所进行的总时间，秒为单位
-p：POST时的数据文件
-w: 以HTML表的格式输出结果
例如：D：documentsapachebinab -n10 -c10 http://www.mall.com/index.php
相当于并发为10的情况下请求www.mall.com站点10次
 
3、测试结果分析：  
  Concurrency Level      并发数
  Complete requests      完成请求的数量
  Failed requests         失败的请求数量
  Requests per second    每秒事务数
  Time per request       平均事务响应时间 （上）
  Time per request       每个请求实际运行时间的平均值（下）
![](DraggedImage.tiff)
---- 
使用php扩展，监控性能。

xhgui升级php7
- 目前XHProf版本不支持，需要找其他扩展
- The XHProf PHP extension is not compatible with PHP7.0+. Instead you'll need to use the tideways extension. 
- ideways extension url:[https://github.com/tideways/php-profiler-extension](https://github.com/tideways/php-profiler-extension)
- 编译：
	 /usr/local/webserver/php7/bin/phpize
	 ./configure --with-php-config=/usr/local/webserver/php7/bin/php-config 
	make
	make install
- 配置：
 tideways
extension="/path/to/tideways/tideways.so"
tideways.connection=unix:///usr/local/var/run/tidewaysd.sock
tideways.loadlibrary=0
tideways.autoprependlibrary=0
tideways.autostart=0
tideways.samplerate=100
重启fpm
安装 [[xhgui]https://github.com/perftools/xhgui](#)
在你的项目入口加入下面一段：
@include '/data/web/xhgui.eelly.dev/external/header.php';
![](DraggedImage.png)

---- 
通过这两项，基本上，你对你的项目性能有一定的了解。