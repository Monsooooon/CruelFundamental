# 讲讲HTTP状态码

HTTP响应码分为五类, 分别为1-5开头.

## 1开头

**信息**. 服务器收到请求, 请求者继续执行操作.

## 2开头

**成功**. 操作被成功接收并处理.

- 200: 请求成功. 一般用于GET和POST.
- 201: Created. 已创建. 成功请求并创建了新的资源.
- 202: Accepted. 已接受. 已经接受请求, 但未完成处理.

## 3开头

**重定向**. 需要进一步的操作以完成请求.

- 301: **永久重定向**. 请求的资源永久移动到新的URL上, 返回的响应中包含新的URL, 之后任何新的请求都应该使用新的URL替代.z
- 302: **暂时重定向**. 资源只是被暂时移动, 客户端应继续使用原URL.

## 4开头

**客户端错误**. 请求错误或者无法完成请求.

- 403: Forbidden. 权限不足, 拒绝执行.
- 404: Not Found. 无法找到资源.

## 5开头

**服务器错误**. 服务器在处理请求中发生了错误.

- 500: 服务器内部错误.
- 502: Bad Gateway. 网关执行请求时, 从远处服务器收到了无效的响应.
- 504: Gateway time-out. 网关从远程服务器获取超时.