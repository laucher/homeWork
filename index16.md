
### 为什么要使用模块化
 - 解决命名冲突
 - 可以提高代码的可读性
 - 提高代码的复用性
 - 避免污染全局变量
 - 实现依赖管理
 - 可以实现代码的异步加载，提高页面加载性能，避免网页失去响应。
 - 有利于团队分工

### CMD、AMD、CommonJS 规范分别指什么？有哪些应用

#### CommonJS

CommonJS是node采用的模块化规范，采用同步加载模块的方式，这个在服务端是完全没有问题的。

1. 一个单独的文件就是一个模块，每个模块都是一个单独的作用域，在模块内部定义的变量，无法被其他模块读取，除非定义为global对象的属性

2. 模块输出：模块只有一个出口，module.exports对象，我们需要把模块输出的内容放入该对象

3. 加载模块：加载模块使用require方法，该方法读取一个文件并执行，返回文件内部的module.exports对象，如果请求的模块不能返回，那么"require"必须抛出一个错误。

demo：

```
    //模块定义model.js
    
    var name = "Array"
    
    function printName(){
        console.log(name);
    }
    function printFullName(firstName){
        console.log(firstName + name)
    }
    module.exports = {
        printName: printName;
        printFullName: printFullName
    }
    
    //加载模块
    var nameModule = require("./model.js")
    nameModule.printName() // "Array"
    nameModule.printFullName("Bob") // "Bob Array"
    
    应用 ：因为require是同步的，所以主要是在服务器端使用
    浏览器断加载JavaScript是异步的，所以传统的CommonJs在浏览器环境中无法正常加载

```

#### AMD 

AMD （Async Module Definition）异步模块定义,回一个浏览器断模块化开发的规范，由于有CMD在前，所以网页端也需要有专门管理模块的工具，但是网页端的模块只能是异步加载，如果是同步加载的话，那时间就呵呵了,典型的应用就是require.js。

主要解决：

1. js文件依赖问题
2. js加载时浏览器会停止页面渲染，加载文件越多，页面失去的响应时间越长

demo：

```
//定义module.js
define(['dependencies'],function(){
    var name = 'Array';
    function printName(){console.log(name)}
    return {printName: pirintName}
})

//加载模块
require(['module'],function(module){
    module.printName()
})

/*
* define:
* define(id?dependencies?,factory);
* id:可选参数，用来定义模块的标识，如果没有提供该参数，脚本文件名为模块标识符
* dependencies：是一个当前模块依赖的模块名称数组
* factory：工厂方法，模块初始化要执行的函数或对象，如果为函数，它应该只执行一次，如果是对象，此对象应该为模块的输出值
*
* require:
* require(['dependencies'],function(depName){})
* dependencies:标识所依赖的模块
* function(){}：当模块加载成功后执行的回调函数，加载的模块会以参数形式传入该函数
* require()函数在加载依赖函数时是异步加载，所以浏览器不会失去响应，它指定的回调函数，只有前面的模块都加载成功了，才会运行，解决了依赖性
*
*
*/
```

### CMD

很多时候，我们会发现，我们在首屏的时候，其实没有必要一次性加载那么多的js文件，更多的我们希望js文件在需要的时候才会去记载，于是就有了CMD的出现，主要应用在sea.js。

```

/*
* define
* define(id?,deps?,factory)
* CMD推崇依赖就近，所以一般不再define的参数中写依赖，在factory中写
* factory有三个参数
*
* function(require,exports,module)
* require是一个方法，接受模块标识作为唯一参数，用来获取其他模块提供的接口
* exports是一个对象，用来想外提供模块接口
* module是个对象，上面存储了与当前模块相关的属性和方法
*/

//在a.js中定义模块
define(function(require,exports,module){
    var $ = require("jquery.js")
    // dosomething with jquery
    exports.foo = something
})
//在c.js中使用模块
defind(function(require,exports,module){
    var a = require('./a.js')
    a.foo//do something with a.foo函数
    exports.bar = thisthing//本模块输出的接口
})
```

