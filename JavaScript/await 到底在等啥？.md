# await 到底在等啥？

`await`是JavaScript中用于处理异步操作的关键字，它通常与`async`函数一起使用。关于`await`到底在等什么，可以从以下几个方面进行解释和归纳：

1. **等待Promise对象的解析结果**：

- `await`主要用于等待一个Promise对象的解析结果。Promise是JavaScript中用于处理异步操作的对象，它代表了某个尚未完成的操作的最终结果。`await`可以暂停`async`函数的执行，直到Promise对象的状态变为已解决（fulfilled）或已拒绝（rejected），并返回相应的结果。

1. **等待任意表达式的计算结果**：

- 从语法上讲，`await`等待的是一个表达式的计算结果，这个表达式可以是一个Promise对象，也可以是其他任何值。如果`await`后面跟的不是Promise对象，那么JavaScript引擎会自动将其包装成一个已解决的Promise，然后`await`等待这个Promise的解析结果。

1. **操作对象的then方法**：

- 更深入地理解，`await`实际上是在操作对象的`then`方法。它会调用对象的`then`方法，并传入`resolve`和`reject`参数，然后等待`then`方法内部调用这两个参数之一。这也是为什么`await`可以等待Promise对象的原因，因为Promise对象具有`then`方法。

1. **只能在async函数中使用**：

- 需要注意的是，`await`只能在`async`函数内部使用。如果在普通函数或全局作用域中使用`await`，会导致语法错误。这是因为`async`函数会将其内部的代码块包装成一个Promise对象，并通过`await`来管理异步操作的执行顺序。

综上所述，`await`在等待的是Promise对象的解析结果或任意表达式的计算结果，它通过操作对象的`then`方法来实现等待功能，并只能在`async`函数中使用。这使得异步代码可以像同步代码那样编写和理解，提高了代码的可读性和可维护性。