`instanceof` 判断左边的原型是否存在于右边的原型链中。

实现思路：逐层往上查找原型，如果最终的原型为`null`时，证明不存在原型链中，否则存在。

```js
function instanceof_(left, right){
  left = left.__proto__
  while(left !== right.prototype){
    left = left.__proto__ // 查找原型，再次while判断
    if(left === null){
      return false
    }
  }
  return true
}
```

