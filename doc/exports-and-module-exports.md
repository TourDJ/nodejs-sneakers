
## exports 与 module.exports 的区别

在nodejs的代码中使用require加载模块，在模块中使用exports或者module.exports导出接口，为什么require、module、exports可以直接使用呢？因为node在编译js模块的时候，将我们所写的代码进行了包装，将整个代码放进了一个函数中：
```javascript
(function(exports, require, module, __filename, __dirname){ 

});
```
例如：
(function(exports, require, module, __filename, __dirname){ 
  var hello = function() { 
    console.log('Hello World!'); 
  } 

  module.exports = hello; 
});
此外还有__dirname和__filename 也可以直接使用。

那么，exports 和 module.exports 有什么区别呢？

看个例子，

//index.js
```javascript
console.log(module.exports); 
console.log(exports); 
```
打印出结果都是 {}，说明初始状态下：

exports = module.exports = {};
exports本身就只是module.exports的引用。

接着， 

//test.js
```javascript
let a = 1;
exports.a = 200; 
exports = 'test'; 
```
//index.js
```javascript
var a = require('/test');
console.log(a) 
```
输出：{a : 200}

结果表明：
* require导出的内容是module.exports的指向的内存块内容
* exports 重新赋值则指向了新的内存


