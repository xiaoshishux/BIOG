## keep-alive 中的生命周期哪些

keep-alive 是Vue提供的一个内置组件，用来对组件进行缓存一一在组件切换过程中将状态保留在内存中，防止重复渲染DOM



如果为一个组件包裹了 keep-alive，那么它会多出两个生命周期：deactivated、activated。同时，beforeDestroy 和 destroyed 就不会再被触发了，因为组件不会被真正摧毁。



当组件被换掉时，会被缓存到内存中，触发deactivated生命周期；

当组件被切换回来时，再去缓存里找这个组件，触发activated钩子函数；