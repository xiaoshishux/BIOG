```
关于link与@import的区别:
区别1：link是XHTML标签，除了加载CSS外，还可以定义RSS等其他事务；@import属于CSS范畴，只能加载CSS。
区别2：link引用CSS时，在页面载入时同时加载；@import需要页面网页完全载入以后加载。
区别3：link是XHTML标签，无兼容问题；@import是在CSS2.1提出的，低版本的浏览器不支持。
区别4：link支持使用Javascript控制DOM去改变样式；而@import不支持。
```