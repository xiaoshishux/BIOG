### map和weakMap的区别---了解即可

- **（1）Map**

  map本质上就是键值对的集合，但是普通的Object中的键值对中的键只能是字符串。而ES6提供的Map数据结构类似于对象，但是它的键不限制范围，可以是任意类型，是一种更加完善的Hash结构。如果Map的键是一个原始数据类型，只要两个键严格相同，就视为是同一个键。

  

  实际上Map是一个数组，它的每一个数据也都是一个数组，其形式如下：

  ```
  const map = [
       ["name","张三"],
       ["age",18],
  ]
  ```

  Map数据结构有以下操作方法：

  - **size**： `map.size` 返回Map结构的成员总数。
  - **set(key,value)**：设置键名key对应的键值value，然后返回整个Map结构，如果key已经有值，则键值会被更新，否则就新生成该键。（因为返回的是当前Map对象，所以可以链式调用）
  - **get(key)**：该方法读取key对应的键值，如果找不到key，返回undefined。
  - **has(key)**：该方法返回一个布尔值，表示某个键是否在当前Map对象中。
  - **delete(key)**：该方法删除某个键，返回true，如果删除失败，返回false。
  - **clear()**：map.clear()清除所有成员，没有返回值。

  

  Map结构原生提供是三个遍历器生成函数和一个遍历方法

  - keys()：返回键名的遍历器。
  - values()：返回键值的遍历器。
  - entries()：返回所有成员的遍历器。
  - forEach()：遍历Map的所有成员。

  ```
  const map = new Map([
       ["foo",1],
       ["bar",2],
  ])
  for(let key of map.keys()){
      console.log(key);  // foo bar
  }
  for(let value of map.values()){
       console.log(value); // 1 2
  }
  for(let items of map.entries()){
      console.log(items);  // ["foo",1]  ["bar",2]
  }
  map.forEach( (value,key,map) => {
       console.log(key,value); // foo 1    bar 2
  })
  ```

  **（2）WeakMap**

  WeakMap 对象也是一组键值对的集合，其中的键是弱引用的。**其键必须是对象**，原始数据类型不能作为key值，而值可以是任意的。

  

  该对象也有以下几种方法：

  - **set(key,value)**：设置键名key对应的键值value，然后返回整个Map结构，如果key已经有值，则键值会被更新，否则就新生成该键。（因为返回的是当前Map对象，所以可以链式调用）
  - **get(key)**：该方法读取key对应的键值，如果找不到key，返回undefined。
  - **has(key)**：该方法返回一个布尔值，表示某个键是否在当前Map对象中。
  - **delete(key)**：该方法删除某个键，返回true，如果删除失败，返回false。

  其clear()方法已经被弃用，所以可以通过创建一个空的WeakMap并替换原对象来实现清除。

  

  WeakMap的设计目的在于，有时想在某个对象上面存放一些数据，但是这会形成对于这个对象的引用。一旦不再需要这两个对象，就必须手动删除这个引用，否则垃圾回收机制就不会释放对象占用的内存。

  

  而WeakMap的**键名所引用的对象都是弱引用**，即垃圾回收机制不将该引用考虑在内。因此，只要所引用的对象的其他引用都被清除，垃圾回收机制就会释放该对象所占用的内存。也就是说，一旦不再需要，WeakMap 里面的**键名对象和所对应的键值对会自动消失，不用手动删除引用**。

  

  **总结：**

  - Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。
  - WeakMap 结构与 Map 结构类似，也是用于生成键值对的集合。但是 WeakMap 只接受对象作为键名（ null 除外），不接受其他类型的值作为键名。而且 WeakMap 的键名所指向的对象，不计入垃圾回收机制。