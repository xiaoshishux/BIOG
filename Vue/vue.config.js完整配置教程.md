## 1.介绍

Vue3.0不在有`webpack.config.js`的配置；但是不可避免,在项目开发中我们肯定会存在一些特殊的需求需要调整`webpack`, 这个时候，在Vue3.0的项目当中，我们就需要在根目录创建`vue.config.js`去完成`webpack`的一些特殊配置,默认它会被 `@vue/cli-service` 自动加载。此刻，你需要创建`vue.config.js`文件。

### 查看默认的webpack配置

Vue CLI 官方文档：`vue-cli-service` 暴露了 `inspect` 命令用于审查解析好的 `webpack` 配置。

那个全局的 vue 可执行程序同样提供了 `inspect` 命令，这个命令只是简单的把 `vue-cli-service``inspect` 代理到了你的项目中。

被抽象化的`webpack`，我们要想去理解它默认的一些配置的话是比较困难的，所以我们可以通过指令去查看。

该指令会将`webpack`的配置输出到`output.js`文件，这样方便去查看。

#### **vue.config.js文件**

这个文件导出了一个包含了选项的对象：

```js
module.exports = {//选项
}
```

接下来，详细介绍一些选项及配置：

## 2.基本配置：

```js
module.exports = {
    productionSourceMap: false,
    publicPath: './',
    outputDir: 'dist',
    assetsDir: 'assets',
    devServer: {
        port: 8090,
        host: '0.0.0.0',
        https: false,
        open: true
    },
    // 其他配置
    ...
```

productionSourceMap：生产环境是否要生成 `sourceMap`。

publicPath：部署应用包时的基本 URL，用法和 `webpack` 本身的 `output.publicPath` 一致

可以通过三元运算去配置`dev`和`prod`环境, 

```js
publicPath: process.env.NODE_ENV === 'production' ? '/prod/' : './'
```

outputDir: `build` 时输出的文件目录。

assetsDir: 放置静态文件夹目录。

devServer: dev环境下，`webpack-dev-server` 相关配置

- port: 开发运行时的端口
- host: 开发运行时域名，设置成`'0.0.0.0'`,在同一个局域网下，如果你的项目在运行，同时可以通过你的http://ip:port/...访问你的项目
- https: 是否启用 `https`
- open: `npm run serve` 时是否直接打开浏览器

## 3.插件及规则的配置

在`vue.config.js`如果要新增/修改 `webpack` 的 `plugins` 或者 `rules` , 有2种方式。

`configureWebpack` 方式

configureWebpack 是相对比较简单的一种方式

- 它可以是一个对象：和 `webpack` 本身配置方式是一致，该对象将会被 `webpack-merge` 合并入最终的 `webpack` 配置

- 它也可以是一个函数：直接在函数内部进行修改配置

  ```js
  configureWebpack: {
      rules:[],
      plugins: []
    }
  configureWebpack: (config) => {
      // 例如，通过判断运行环境，设置mode
      config.mode = 'production'
  } 
  ```

`chainWebpack` 方式

chainWebpack 链式操作 (高级)，接下来所有的配置我都会在该选项中进行配置

## 4.规则rules的配置

关于`rules` 的配置，我会分别从新增/修改进行介绍。

4.1rules的新增

在`webpack`中 `rules` 是 `module` 的配置项，而所有的配置的都是挂载到 `config` 下的，所以新增一个rule方式：

```js
config.module
  .rule(name)
    .use(name)
      .loader(loader)
      .options(options)
```

案例：`style-resources-loader` 来添加`less`全局变量

案例：`svg-sprite-loader` 将svg图片以雪碧图的方式在项目中加载

```js
module.exports = {
    chainWebpack: (config) => {
        // 通过 style-resources-loader 来添加less全局变量
        const types = ['vue-modules', 'vue', 'normal-modules', 'normal'];
        types.forEach(type => {
            let rule = config.module.rule('less').oneOf(type)
            rule.use('style-resource')
                .loader('style-resources-loader')
                .options({
                    patterns: [path.resolve(__dirname, './lessVariates.less')]
                });
        });
        // `svg-sprite-loader`: 将svg图片以雪碧图的方式在项目中加载
        config.module
            .rule('svg')
            .test(/.svg$/) // 匹配svg文件
            .include.add(resolve('src/svg')) // 主要匹配src/svg
            .end() 
            .use('svg-sprite-loader')
            .loader('svg-sprite-loader') // 使用的loader，主要要npm该插件
            .options({symbolId: 'svg-[name]'}) // 参数配置
    }
}
```

4.2rules的修改

针对已经存在的 `rule` , 如果需要修改它的参数, 可以使用 `tap` 方法：

```js
config.module
  .rule(name)
    .use(name)
      .tap(options => newOptions)
```

案例：修改`url-loader`的参数

```js
module.exports = {
    chainWebpack: (config) => {
        // `url-loader`是webpack默认已经配置的，现在我们来修改它的参数
        config.module.rule('images')
            .use('url-loader')
            .tap(options => ({
                name: './assets/images/[name].[ext]',
                quality: 85,
                limit: 0,
                esModule: false,
            }))
    }
}
```

## 5.插件plugins的配置

关于 `plugins` 的配置，我会分别从`新增/修改/删除`进行介绍。