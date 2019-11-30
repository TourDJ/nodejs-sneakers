## [CommonJS](http://www.commonjs.org/)
CommonJS 是服务器端模块的规范，Node.js采用了这个规范。    

根据CommonJS规范，一个单独的文件就是一个模块。加载模块使用require方法，该方法读取一个文件并执行，最后返回文件内部的exports对象。

CommonJS定义的模块分为: 模块标识(module)、模块定义(exports) 、模块引用(require)
