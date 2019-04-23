## 简介

在开始学习JS的时候，会看到很多资料上写到JS是一门面向对象的语言，对于
熟悉C++/JAVA等语言的人而言，面向对象看起来是非常自然的存在，但是在JS
中，为了实现所追求的面向对象开发的效果，我们还是需要理解费些功夫的。

谈到面向对象，会说到四大特征:
* 封装
* 继承
* 多态
* 重载
  
那么在JS中，哪些是**可以被支持**，**如何被支持**呢。

在通过js模拟类的过程中有几个概念需要理解:
* new操作符
* 原型继承(prototype)
  
## 思考面向对象设计

### 封装

封装将数据及针对数据的操作组合在一样，使得我们在不改变接口的情况下，
可以根据情况改变内部的数据结构。针对C++而言，我们一般会使用`private`
修饰符来组织外部对该成员变量的访问，很遗憾，目前js中并不支持概念上的
私有成员变量。

下面来实现一个`person`类，可以为该实例设置名称及年纪。

```js
function Person(age, name) {
    this._age = age;
    this._name = name;
}
Person.prototype.setAge = function (age) {
    this._age = age;
}
Person.prototype.getAge = function () {
    return this._age;
}
Person.prototype.setName = function (name) {
    this._name = name;
}
Person.prototype.getName = function(){
    return this._name;
}
var p1 = new Person(18, 'jack');
console.log("Before change age:",p1.getAge());
console.log("Before change name:",p1.getName());
p1.setAge(20);
p1.setName('tom');
console.log("End change age:",p1.getAge());
console.log("End change name:",p1.getName());
```

* js不支持私有成员变量，个人喜欢使用`_xxx`格式代表私有变量

### 重载
  
在c++中重载是指多个函数可以拥有相同的函数名，但是不同的参数类型或个数。
在实际调用过程中，会根据传入的参数不同来决定调用哪个函数。

但js是一门动态语言，且并不限制传入的参数个数及类型，所以js是不支持函数
重载的。

* [arguments object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments)