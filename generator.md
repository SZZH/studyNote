## Generator

### 阮一峰generator教程

[地址](http://www.ruanyifeng.com/blog/2015/04/generator.html)

### 基础概念

- generator是为了解决promise代码冗余问题，因为一个异步请求会使用到很多then才能获取到数据
- generator函数返回的是一个generator对象，这也是与普通函数不同的地方
- generator函数中yield会暂停当前函数，yield的返回值会保存到next().value中
- 调用generator下的next方法会分段执行函数，向next里传参可以往函数里传值

### 实例

```javascript
var fetch = require("node-fetch");

function* gen() {
  var url = "https://api.github.com/users/github";
  var result = yield fetch(url);
  console.log(result);
}
var g = gen();
var result = g.next();

result.value
  .then(function(data) {
    return data.json();
  })
  .then(function(data) {
    g.next(data);
  });

```

