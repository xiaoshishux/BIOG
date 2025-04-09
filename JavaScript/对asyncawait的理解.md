# 对async/await的理解

async/await 是 JavaScript 中用于处理异步操作的一种语法糖，它使得异步代码在书写和理解上更接近同步代码。这两个关键字是 ES2017 (ECMAScript 2017) 引入的，并且它们通常一起使用。

 **async** 

async 关键字用于声明一个函数是异步的。这意味着这个函数总是返回一个 Promise 对象。如果函数体返回一个非 Promise 的值，JavaScript 引擎会自动将这个值包装成一个已解决的 Promise。

 **await** 

await 关键字只能在 async 函数内部使用。它会暂停当前 async 函数的执行，并等待其右侧的表达式的结果。这个表达式通常是一个 Promise，但也可以是任何值。如果表达式是 Promise，await 会等待这个 Promise 解决（fulfilled）或拒绝（rejected）。

-  如果 Promise 解决，await 表达式的结果就是 Promise 解决的值。
- 如果 Promise 拒绝，await 会抛出异常，这个异常可以通过 try...catch 结构来捕获。

如果 await 右侧的表达式不是一个 Promise，则会被转换成一个立即解决的 Promise。

 **理解** 

1. **简化异步流程**：在 async 函数中，你可以使用 await 来等待一个异步操作完成，而不必使用 .then() 或 .catch() 方法来处理 Promise。这使得代码更加清晰和易于理解。
2. **顺序执行**：await 允许你以顺序的方式编写异步代码，即使这些操作本身是并发的。这使得代码更易于阅读和维护，因为它避免了回调函数的嵌套（也称为“回调地狱”）。
3. **错误处理**：在 async 函数中，你可以使用 try...catch 语句来捕获由 await 抛出的异常，这与同步代码中的错误处理非常相似。
4. **非阻塞：**虽然 await 会暂停 async 函数的执行，但它不会阻塞主线程。在等待 Promise 解决或拒绝期间，JavaScript 引擎可以继续执行其他任务。

 **示例** 

下面是一个简单的示例，展示了如何使用 async/await 来读取文件内容（假设有一个返回 Promise 的 readFile 函数）：

```JavaScript

async function readFileContent(filePath) {
  try {
    const content = await readFile(filePath); // 等待文件读取完成
    console.log(content); // 打印文件内容
  } catch (error) {
    console.error('Error reading file:', error); // 处理读取错误
  }
}
```

在这个示例中，readFileContent 是一个 async 函数，它使用 await 来等待 readFile(filePath) 这个异步操作的结果。如果文件成功读取，它会打印文件内容；如果发生错误，它会捕获并打印错误信息。









若有收获，就点个赞吧