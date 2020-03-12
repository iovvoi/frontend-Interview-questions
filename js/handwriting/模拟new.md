`new`使用构造函数创建实例对象，为实例对象添加`this`属性和方法

`new`的过程：

创建新对象  
新对象`__proto__`指向构造函数原型  
新对象添加属性方法（`this`指向）  
返回t`his`指向的新对象  
```js
function new_(){
  let fn = Array.prototype.shift.call(arguments)
  if(typeof fn != 'function'){
    throw fn + ' is not a constructor'
  }
  let obj = {}
  obj.__proto__ = fn.prototype
  let res = fn.apply(obj, arguments)
  return typeof res === 'object' ? res : obj
}
```