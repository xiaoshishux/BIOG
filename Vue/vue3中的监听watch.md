# **vue3中的监听watch**

在 Vue 3 中，watch 的使用方式发生了一些变化，尤其是引入了 Composition API 之后。Vue 3 仍然支持 Options API（即传统的 Vue 组件写法），但如果你使用 Composition API，watch 和 watchEffect 将成为你观察和响应数据变化的主要工具。

 **使用 Composition API 中的 watch** 

在 Composition API 中，watch 是一个独立的函数，可以从 vue 包中导入。以下是一个简单的例子：

```javascript
import { ref, watch } from 'vue';
 
export default {
  setup() {
    const count = ref(0);
 
    watch(count, (newValue, oldValue) => {
      console.log(`Count changed from ${oldValue} to ${newValue}`);
    });
 
    return {
      count
    };
  }
};
```

在这个例子中，我们导入了 ref 和 watch 函数。ref 用于创建一个响应式引用，而 watch 用于观察这个引用的变化。当 count 的值发生变化时，watch 的回调函数会被触发。

 **watch 的选项** 

和 Vue 2 中的 watch 类似，Vue 3 的 watch 函数也支持一些选项，例如 deep 和 immediate。这些选项可以作为 watch 函数的第三个参数传入，它是一个对象：

```javascript
watch(count, (newValue, oldValue) => {
  // ...
}, { deep: true, immediate: true });
```

但请注意，在 Vue 3 的 Composition API 中，通常不需要 deep 选项，因为你可以直接观察响应式对象或数组，而无需深度观察。Vue 3 会自动追踪这些响应式数据的所有嵌套属性。

 **watchEffect** 

除了 watch 之外，Vue 3 还引入了 watchEffect 函数，它是一个更简洁的观察方式，不需要明确指定依赖项。watchEffect 会自动收集依赖项，并在任何依赖项变化时重新运行。

```javascript
import { ref, watchEffect } from 'vue';
 
export default {
  setup() {
    const count = ref(0);
    const message = ref('Hello');
 
    watchEffect(() => {
      console.log(`Count is ${count.value}, Message is ${message.value}`);
    });
 
    return {
      count,
      message
    };
  }
};
```

在这个例子中，每当 count 或 message 的值发生变化时，watchEffect 的回调函数都会被触发。

总的来说，Vue 3 中的 watch 和 watchEffect 提供了灵活且强大的方式来观察和响应数据变化，无论是在 Options API 还是 Composition API 中。

