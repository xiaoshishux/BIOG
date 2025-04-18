# router与route区别

简单理解为：router是用来操作路由的，route是用来获取路由信息的

## router

```md
router是VueRouter的实例，通过Vue.use(VueRouter)和VueRouter构造函数得到一个router的实例对象，这个对象中是一个全局的对象，它包含了所有的路由包含了许多关键的对象和属性
```

$router对象是全局路由的实例，是router构造方法的实例

**1.$router.go()**

​    $router.back 后退   

​    页面路由跳转 $router.go(-1)为后退，$router.go(-1)为前进  $router.forward()为前进

**2.$router.push()**

字符串this.$router.push('home')

 对象this.$router.push({path:'home'})

命名的路由this.$router.push({name:'user',params:{userId:123}})

带查询参数，变成 /register?plan=123this.$router.push({path:'register',query:{plan:'123'}})

push方法其实和<router-link :to="...">是等同的。

​    *注意：push方法的跳转会向 history 栈添加一个新的记录，当我们点击浏览器的返回按钮时可以看到之前的页面。

**3.$router.replace()**  常用来做404页面

​    push方法会向 history 栈添加一个新的记录，而replace方法是替换当前的页面，

​    不会向 history 栈添加一个新的记录

​    this.$router.replace('/') 跳转到首页

## route

```md
route是路由信息对象，每一个路由都会有一个route对象，是一个局部的对象,里面主要包含路由的一些基本信息，比如name、meta、path、hash、query、params、fullPath、matched、redirectedFrom...
```

1. **$route.name**        当前路径名字

2. **$route.meta**        路由元信息

3. **$route.path**        字符串，对应当前路由的路径，总是解析为绝对路径，如"/foo/bar"。

4. **$route.hash**        当前路由的hash值 (不带#) ，如果没有 hash 值，则为空字符串。锚点*

5. **$route.query**        一个 key/value 对象，表示 URL 查询参数。例如，对于路径 /foo?user=1，则有$route.query.user == 1，如果没有查询参数，则是个空对象。

6. **$route.params**        一个 key/value 对象，包含了 动态片段 和 全匹配片段，如果没有路由参数，就是一个空对象。

7. **$route.fullPath**        完成解析后的 URL，包含查询参数和hash的完整路径。

8. **$route.matched**        数组，包含当前匹配的路径中所包含的所有片段所对应的配置参数对象。



this.$router它是VueRouter的实例、一个全局路由对象，是是用来来操作路由，项目中用来路由跳转（this.$router.push（xxx））

this.$route

this.$route是当前激活的路由对象，通过它我们可以获取当前路由的一些信息，比如path、quey，meta等属性

（this.$route.quey.xxxx）