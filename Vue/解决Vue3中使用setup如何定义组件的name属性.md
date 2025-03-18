# 解决Vue3中使用setup如何定义组件的name属性

第一种：新增加一个script标签，在这个标签中写入name属性

第二种：安装：unplugin-vue-define-options ， Element Plus中都是使用这个插件来对组件名进行注册的
cnpm install unplugin-vue-define-options -D

第三种：安装“cnpm install vite-plugin-vue-setup-extend -D”，集成插件 在vite.config.ts文件引入vite-plugin-vue-setup-extend



参考数据来源

https://www.jb51.net/article/250641.htm

http://www.syrr.cn/news/11703.html