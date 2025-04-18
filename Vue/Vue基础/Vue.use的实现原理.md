### Vue.use的实现原理

先贴源码

```js
// src/core/global-api/use.js
import { toArray } from '../util/index'

export function initUse (Vue: GlobalAPI) {
  Vue.use = function (plugin: Function | Object) {
    const installedPlugins = (this._installedPlugins || (this._installedPlugins = []))
    if (installedPlugins.indexOf(plugin) > -1) {
      return this
    }

    // additional parameters
    const args = toArray(arguments, 1)
    args.unshift(this)
    if (typeof plugin.install === 'function') {
      plugin.install.apply(plugin, args)
    } else if (typeof plugin === 'function') {
      plugin.apply(null, args)
    }
    installedPlugins.push(plugin)
    return this
  }
}
```

可以看到，use源码部分其实不长

Vue.use()，传入一个function或object，首先会检查这个插件是否已经存在，如果存在则直接返回

toArray方法，将类数组转化成数组，1是指从第一个参数开始，比如

```js
Vue.use(globalPlugin, 1, 2, 3)
// args = [1,2,3]
```

检查入参plugin的install属性是否为function，如果是，则通过apply调用plugin.install，此时plugin为object

如果不是，则检查入参plugin是否为function，如果是，则通过apply调用plugin

最后把入参plugin存到数组installedPlugins，用于检查插件是否存在

**举个栗子**

```js
// globalPlugin.js
// 以下为我随手写的假代码，不一定能运行，但思路是对的
import ElementUI from 'element-ui'

export default (app) => {
    useElement(app)
    useConfig(app)
    useToast(app)
}

/** 对象写法
export default {
	install(app): {
        useElement(app)
        useConfig(app)
        useToast(app)
	}
}
*/

// 注册ElementUI
const useElement = (app) => {
    app.use(ElementUI)
}

// 注册全局配置
const useConfig = (app) => {
    app.config.name = 'xxx'
    app.config.age = 18
}

// 注册自己写的toast方法
const useToast = (app) => {
    app.$toast = () => {
        // 自己写的toast方法
    }
}
```

```js
// main.js
import Vue from 'vue'
import globalPlugin from './globalPlugin'	// 就是上面这个js

const vm = new Vue()
vm.use(globalPlugin)	// 执行自定义插件
```

根据以上demo，可以得出，通过use

- 注册全局配置属性
- 注册全局引用方法