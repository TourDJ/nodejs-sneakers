
## exports 与 module.exports 的区别

在**nodejs**的代码中使用`require`加载模块，在模块中使用`exports`或者`module.exports`导出接口，为什么`require`、`module`、`exports`可以直接使用呢？因为node在编译js模块的时候，将我们所写的代码进行了包装，将整个代码放进了一个函数中：
```javascript
(function(exports, require, module, __filename, __dirname){ 

});
```
例如：
```javascript
(function(exports, require, module, __filename, __dirname){ 
  var hello = function() { 
    console.log('Hello World!'); 
  } 

  module.exports = hello; 
});
```
此外还有__dirname和__filename 也可以直接使用。

那么，`exports` 和 `module.exports` 有什么区别呢？

看个例子，

//index.js
```javascript
console.log(module.exports); 
console.log(exports); 
```
打印出结果都是 {}，说明初始状态下：

    exports = module.exports = {};
`exports`本身就只是`module.exports`的引用。

接着， 

//test.js
```javascript
let a = 1;
exports.a = 200; 

var hello = function(){
    console.log('Hello World');
};

exports = hello;
```
//index.js
```javascript
var test = require('./test');
console.log(test) 
test();
```
输出：{a : 200}

结果表明：
* `require` 导出的内容是 `module.exports` 的指向的内存块内容
* `exports` 重新赋值则指向了新的内存     
* 会报 TypeError 的错误，因为最终返回的 `module.exports` 只是一个空对象



### 参考资料
[exports的用法：Node.js模块的接口设计模式 ](https://gywbd.github.io/posts/2014/11/using-exports-nodejs-interface-design-pattern.html)     
