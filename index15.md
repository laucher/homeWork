##this 相关问题
### apply、call、bind有什么作用，什么区别?
apply、call、bind都作用本质都是改变函数的执行环境上下文，即this指向。

区别

1. apply和call返回的值是函数的运行结果。
2. apply的参数是传入数组或类数组，而call的参数是若干个指定参数。
3. bind返回的是修改过this的函数。

```
var _thisContext = { color: 'blue' };
window.color = 'yellow';
function getColor() {
	console.log(this.color);
}
getColor(); // 'yellow'
getColor.call(_thisContext); // 'blue'
getColor.apply(_thisContext); // 'blue'
```

```
var arrToCompare = [1,2,3,4,5,6,7,8,9];
Math.max.apply(null, arrToCompare); // 9 
Math.max.call(null, 1,2,3,4,5,6,7,8,9); // 9
```

```
var getAge=function(){
    console.log(this.age);
    console.log(arguments[0]);
}

window.age="window";

var context={
    age:"19"
}

getAge()//window,

getAge.bind(context)();//19,undefined

getAge.bind(context,'另外一个参数')('你猜猜');//19,'另外一个参数'

```

### 以下代码输出什么?

```
var john = { 
  firstName: "John" 
}
function func() { 
  alert(this.firstName + ": hi!")
}
john.sayHi = func //this指向函数执行环境，即john
john.sayHi() // alert John :"hi!"
```

### 下面代码输出什么，为什么?

```
func()  //执行函数，当前执行环境是window，alert [object Window]
function func() { 
  alert(this) 
}
```

### 下面代码输出什么?

```
document.addEventListener('click', function(e){
    console.log(this); //函数执行环境 -> document; this -> document
    setTimeout(function(){
        console.log(this); //函数执行环境 -> 全局(Winodow); this -> Window
    }, 200);
}, false);
```

### 下面代码输出什么，why?

```
var john = { 
  firstName: "John" 
}

function func() { 
  alert( this.firstName )
}
func.call(john) //call改变执行环境，this指向john，this.firstName = "John"
```

### 以下代码有什么问题，如何修改?
```
var module= {
  bind: function(){
    $btn.on('click', function(){
      console.log(this) //this指向eventTarget，在此即被点击的DOM元素($btn)
      this.showMsg(); //dom元素上并没有挂载这个函数，无法执行
    })
  },
  
  showMsg: function(){
    console.log('饥人谷');
  }
}
```

修改版：

```
var module= {
  bind: function(){
	  let _this = this; //将函数执行上下文缓存为一个变量
    $btn.on('click', function(){
      console.log(this) 
      _this.showMsg();
    })
  },
  
  showMsg: function(){
    console.log('You clicked the button!');
  }
}
module.bind();
//点击后显示： You clicked the button!
```

## 原型链相关问题
### 有如下代码，解释Person、 prototype、__proto__、p、constructor之间的关联。
```
function Person(name){
    this.name = name;
}
Person.prototype.sayName = function(){
    console.log('My name is :' + this.name);
}
var p = new Person("kylewh")
p.sayName();

//关系如下
console.dir( 
rel = [
    Person.prototype.constructor == Person,
    Person.prototype == p.__proto__,
    p.__proto__.constructor == Person,
    Person.prototype.__proto__ == Object.prototype,
    Object.prototype.constructor == Object,
    Object.prototype.__proto__ == null
]
); // 6个true
```

### 上例中，对对象 p可以这样调用 p.toString()。toString是哪里来的? 画出原型图?并解释什么是原型链。

```
//toString是从object的原型里继承而来
//构造函数的原型自带一个指针指向object的原型

//验证
console.log( p.toString == p.__proto__.__proto__.toString); //true
```

![](https://ww1.sinaimg.cn/large/006tNc79gy1fcqkyhx364j30mx0lsgm4.jpg)

使用一个构造函数创造一个实例对象，在此对象上调用相应的属性和方法时，首先查找它本身有没有，如果没有，则顺着__proto__这个指针去找它的构造函数的原型上有没有，如果没有，再顺着原型的__proto__向上去找，也就是说，只要存在__proto__这个指针，在没有找到对应的属性与方法时，查找不会停下，直到没有__proto__为止，这样的一种形式可行的结构基础就叫**原型链**。

### 对String做扩展，实现如下方式获取字符串中频率最高的字符

```
function _extend(_prototype, fnName, fn) {
	if( !_prototype[fnName] ) {
		_prototype[fnName] = fn;
	} else {
		alert('This function is already exist!');
	}
	return _prototype;
}

function getMaxOccur() {
	let strObj = {},
		key,
		max = 0,
		maxKeys;

	for(let i = 0; i<this.length; i++){
		key = this[i];
		if ( !strObj[key] ) {
			strObj[key] = 1;
		} else {
			strObj[key] ++;
		}
	}

	for(let keys in strObj){
		if(strObj[keys] > max){
			max = strObj[keys];
			maxKeys = keys;
		}
	}
	
	return maxKeys;
}

_extend(String.prototype, 'getMaxOcuur', getMaxOccur);
'aaaaaaaaaaaaaaaaabbbbbbbcccccddd'.getMaxOcuur(); // a
```

### instanceOf有什么作用？内部逻辑是如何实现的？

```
//instanceof运算符用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性。

function _instanceOf(obj, fn) {
	let protoOfObj = obj.__proto__;
	do{
		if( protoOfObj == fn.prototype ) {
			return true;
		} else {
			protoOfObj = protoOfObj.__proto__;
		}
	}while(protoOfObj)
	return false;
}

arr = [1,2,3,4,5];
_instanceOf(arr, Array); //true
_instanceOf(arr, Object); //true
```

## 继承相关问题
### 继承有什么作用?

抽象事物的从一般到特殊的过程，使得更具体的事物共享那些更一般的事物的属性与方法，减少重复，通常我们将更具体的事物成为子类，比其抽象的事物称为父类。我们可以灵活的给子类添加特定的属性与方法以此来使其拓展父类的功能，而又不影响父类本身。

### 下面两种写法有什么区别?
```
//方法1
function People(name, sex){
    this.name = name;
    this.sex = sex;
    this.printName = function(){
        console.log(this.name);
    }
}
var p1 = new People('饥人谷', 2)
//构造函数法，复用性不好，不同的对象需要重复添加属性与方法。

//方法2
function Person(name, sex){
    this.name = name;
    this.sex = sex;
}

Person.prototype.printName = function(){
    console.log(this.name);
}

var p1 = new Person('若愚', 27);

//原型链方法，给构造函数原型添加方法，减少重复。
```


### Object.create 有什么作用？兼容性如何？

接收两个参数，第一个参数是一个原型对象，用来作为将要返回的新对象的原型，第二个参数是一个参数对象，里面的key代表了这个新对象的key，而：后面代表了这个key对应的属性，比如value, enumerable等。
```
o2 = Object.create({}, {
  p: {
    value: 42,
    writable: true,
    enumerable: true,
    configurable: true
  }
});
// o2 {p:42}
```

### hasOwnProperty有什么作用？ 如何使用？
用来判断一个属性或方法是否是此对象的实例属性或方法

```javacsript
function Person() {
	this.name = 'kylewh';
}
Person.prototype.age = 25;

let me = new Person();
console.log( me.hasOwnProperty('age') );

console.log( me.hasOwnProperty('age') ); //false
console.log( me.__proto__.hasOwnProperty('age') ); //true
```

### 如下代码中call的作用是什么?
```
function Person(name, sex){
    this.name = name;
    this.sex = sex;
}
function Male(name, sex, age){
    Person.call(this, name, sex);    //调用Person构造函数，将执行环境执向新建立的对象(此处的this将来的指向)
    //效果是当new Person建立对象时，对象会添加传入的name和sex作为实例属性。
    this.age = age;
}
```

###  补全代码，实现继承 

```
function Person(name, sex){
    // todo ...
    this.name = name;
    this.sex = sex;
}

Person.prototype.getName = function(){
    // todo ...
    console.log('name: ' + this.name);    

function Male(name, sex, age){
   //todo ...
   // 寄生组合式继承 （1）
   Person.call(this, name, sex);
   this.age = age;
}

//todo ... 
//寄生组合式继承 （2）
function inheritPrototype(subType, superType) {
	subType.prototype = Object.create(superType.prototype);
	Object.defineProperties(subType.prototype, {
		constructor: {
			enumerable: false;
			value: subType
		}
	});
}

//todo ...
inheritPrototype(Male, Person);

Male.prototype.getAge = function(){
    //todo ...
    console.log( this.age);
};

var kyle = new Male('kyle', 'male', 25);
kyle.getName(); //name: kyle
kyle.getAge(); //age: 25
```