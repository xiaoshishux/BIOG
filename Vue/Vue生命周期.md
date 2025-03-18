# `Vue`的生命周期

`Vue`实例有一个完整的生命周期，从开始创建、初始化数据、编译模板、挂载DOM、渲染、更新、渲染、卸载等一系列过程，这就是`Vue`的生命周期。

在实例化`Vue`过程中，会直接触发生命周期有`beforeCreate`、`create`、`beforeMount`、`mounted`；在数据更新的过程中触发的生命周期有`beforeUpdate`、`updated`；在数据销毁的过程中触发的生命周期有`beforeDestroy`、`destroyed`。

以下是`Vue`中提供的钩子函数：

- `beforeCreate`（创建前）：数据观测和初始化事件还未开始，此时 data 的响应式追踪、event/watcher 都还没有被设置，也就是说不能访问到data、computed、watch、methods上的方法和数据
- `create`（创建后）：实例创建完成，实例上配置的 options 包括 data、computed、watch、methods 等都配置完成，但是此时渲染得节点还未挂载到 DOM，所以不能访问到 `$el` 属性。
- `beforeMount`（挂载前）：在挂载开始之前被调用，相关的render函数首次被调用。实例已完成以下的配置：编译模板，把data里面的数据和模板生成`html`。此时还没有挂载`html`到页面上。
- `mounted`（挂载后）：在el被新创建的 `vm.$el` 替换，并挂载到实例上去之后调用。实例已完成以下的配置：用上面编译好的`html`内容替换el属性指向的DOM对象。完成模板中的`html`渲染到`html` 页面中。此过程中进行`ajax`交互。
- `beforeUpdate`（更新前）：响应式数据更新时调用，此时虽然响应式数据更新了，但是对应的真实 DOM 还没有被渲染。
- `updated`（更新后）：在由于数据更改导致的虚拟DOM重新渲染和打补丁之后调用。此时 DOM 已经根据响应式数据的变化更新了。调用时，组件 DOM已经更新，所以可以执行依赖于DOM的操作。然而在大多数情况下，应该避免在此期间更改状态，因为这可能会导致更新无限循环。该钩子在服务器端渲染期间不被调用。
- `beforeDestroy`（销毁前）：实例销毁之前调用。这一步，实例仍然完全可用，`this` 仍能获取到实例。
- `destroyed`（销毁后）：实例销毁后调用，调用后，`Vue` 实例指示的所有东西都会解绑定，所有的事件监听器会被移除，所有的子实例也会被销毁。该钩子在服务端渲染期间不被调用。

![](C:\Users\Administrator\Desktop\project\掘金发布文章\vue的生命周期\vue的生命周期.png)