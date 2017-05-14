### 问题1： OOP 指什么？有哪些特性

   OOP：
   
   - Object Oriented Programming,面向对象的程序设计。所谓“对象”在显式支持面向对象的语言中，一般是指类在内存中装载的实例，具有相关的成员变量和成员函数（也称为：方法）。
   
   特点：
    
   - 封装： 也叫做信息封装：确保组件不会以不可预期的方式改变其它组件的内部状态；只有在那些提供了内部状态改变方法的组件中，才可以访问其内部状态。每类组件都提供了一个与其它组件联系的接口，并规定了其它组件进行调用的方法。
   - 多态性：组件的引用和类集会涉及到其它许多不同类型的组件，而且引用组件所产生的结果依据实际调用的类型。
   - 继承性：允许在现存的组件基础上创建子类组件，这统一并增强了多态性和封装性。典型地来说就是用类来对组件进行分组，而且还可以定义新类为现存的类的扩展，这样就可以将类组织成树形或网状结构，这体现了动作的通用性。
   
### 问题2： 如何通过构造函数的方式创建一个拥有属性和方法的对象? 

   ```
    var Preson=function(name,age){
        this.name=name||"addam";
        this.age=age||19;
        this.say=function(){
            console.log(this.name)
        }
    }
    
    var preson=new Preson();
   
   ```

### 问题3： prototype 是什么？有什么特性 

   1. prototype：javascript采用prototype机制代替类机制，每个构造函数都有一个prototype，而prototype也是一个对象，prototype表示该函数的原型，也表示一个类的成员的集合。
   2. 特点：prototype的属性和方法会被拥有该prototype的对象所共同享有。

### 问题4：画出如下代码的原型图
```
    function People (name){
      this.name = name;
      this.sayName = function(){
        console.log('my name is:' + this.name);
      }
    }
    
    People.prototype.walk = function(){
      console.log(this.name + ' is walking');  
    }
    
    var p1 = new People('饥人谷');
    var p2 = new People('前端');
```
![原型图](http://i1.piimg.com/588926/aa0c05ce24290e32.png)

### 问题5： 创建一个 Car 对象，拥有属性name、color、status；拥有方法run，stop，getStatus 

```
    function Car(name,color,status){
        this.name=name||"墨菲";
        this.color=color||"red";
        this.status=status||"stop";
    }
    
    Car.prototype={
        
        run:function(){
            this.status="running"
        },
        
        stop:function(){
            this.status="stop";
        },
        getStatus:function(){
            console.log(this.status);
        }
    }
    
    Car.prototype.constructor=Car;

```
