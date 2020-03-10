```js
Function.prototype.mybind = function (oThis) {
  if(typeof this != 'function'){
    throw 'caller must be a function'
  }
  let fThis = this
  //Array.prototype.slice.call 将类数组转为数组
  let arg = Array.prototype.slice.call(arguments,1)
  let NOP = function(){}
  let fBound = function(){
    let arg_ = Array.prototype.slice.call(arguments)
    // new 绑定等级高于显式绑定
    // 作为构造函数调用时，保留指向不做修改
    // 使用 instanceof 判断是否为构造函数调用
    return fThis.apply(this instanceof fBound ? this : oThis, arg.concat(arg_))
  }
  // 维护原型
  if(this.prototype){
    NOP.prototype = this.prototype
    fBound.prototype = new NOP()
  }
  return fBound
}
```