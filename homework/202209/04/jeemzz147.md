### 什么是跨域资源请求?

由于浏览器同源策略，凡是发送请求url的协议、域名、端口三者之间任意一与当前页面地址不同即为跨域。存在跨域的情况：

网络协议不同，如http协议访问https协议。

端口不同，如80端口访问8080端口。

域名不同，如qianduanblog.com访问baidu.com。

子域名不同，如abc.qianduanblog.com访问def.qianduanblog.com。

域名和域名对应ip,如www.a.com访问20.205.28.90.

2、跨域请求资源的方法：

(1)proxy代理

定义和用法：proxy代理用于将请求发送给后台服务器，通过服务器来发送请求，然后将请求的结果传递给前端。

实现方法：通过nginx代理；

注意点：1、如果你代理的是https协议的请求，那么你的proxy首先需要信任该证书（尤其是自定义证书）或者忽略证书检查，否则你的请求无法成功。

(2)CORS 

定义和用法：是现代浏览器支持跨域资源请求的一种最常用的方式。

使用方法：一般需要后端人员在处理请求数据的时候，添加允许跨域的相关操作。
