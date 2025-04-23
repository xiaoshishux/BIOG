### HTTP请求报文的是什么样的？

请求报⽂有4部分组成: 

- 请求⾏ 
- 请求头部 
- 空⾏
- 请求体 

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1500604/1615907508156-a82d09e4-00bf-4dc7-a3a3-1ae75481754e.png)

**其中：**

（1）请求⾏包括：请求⽅法字段、URL字段、HTTP协议版本字段。它们⽤空格分隔。例如，GET /index.html HTTP/1.1。 

（2）请求头部:请求头部由关键字/值对组成，每⾏⼀对，关键字和值⽤英⽂冒号“:”分隔  

- User-Agent：产⽣请求的浏览器类型。 
- Accept：客户端可识别的内容类型列表。 
- Host：请求的主机名，允许多个域名同处⼀个IP地址，即虚拟主机。 

（3）请求体: post put等请求携带的数据 

![image.png](https://cdn.nlark.com/yuque/0/2021/png/1500604/1615907573585-6651540d-9dee-4b33-a97f-dee1b31f231c.png)