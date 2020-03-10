```js
Function.prototype.mycall = function () {
  if(typeof this !== 'function'){
    throw 'caller must be a function'
  }
  let othis = arguments[0] || window
  othis._fn = this
  let arg = [...arguments].slice(1)
  let res = othis._fn(...arg)
  Reflect.deleteProperty(othis, '_fn') //删除_fn属性
  return res
}
```