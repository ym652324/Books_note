## 第五章：引用类型  
### 一. Object类型  
#### 1. 创建Object实例方式  
（1）使用new操作符以及Object构造函数  
```
var person = new Object();
person.name='abc';
person.age=29;
```
（2）使用对象字面量表示法  
 ```
var person={
  name:'abc',
  age:29
};
```
### 二、Array类型  
#### 1.特点
（1）数组是松散的，每一项可以保存不同的数据类型  
（2）数组大小可以动态调整，自动增长以容纳新数据  
（3）数组的length属性不是只读的  
# 未 完 待补充
## 第六章 面向对象的程序设计
### 一、创建对象
#### 1. 创建Object实例方式    
```
var person = new Object();
person.name='abc';
person.age=29;
person.job='software engineer';
person.sayName=function(){
 alert(this.name);
};

person.sayName();
```
（1）缺点：使用同一个接口创建很多个对象会产生大量重复代码  
（2）解决：工厂模式变体  
#### 2. 工厂模式（用函数来封装以特定接口创建对象的细节）  
```
function createPerson(name,age,job){
  var o = new Object();
  o.name=name;
  o.age=age;
  o.job=job;
  o.sayName=function(){
   alert(this.name);
  };
  return o;
}

var person1=createPerson('abc',29,'Software engineer');
var person2=createPerson('def',27,'Docter');

person1.sayName();//abc
person1.sayName();//def
```
（1）缺点：虽然解决了创建多个相似对象的问题，但是没有解决对象识别的问题（即怎样知道一个对象的类型）  
（2）解决：构造函数模式  
#### 3. 构造函数模式  
```
function Person(name,age,job){
  this.name=name;
  this.age=age;
  this.job=job;
  this.sayName=function(){
   alert(this.name);
  };
}

var person1=new Person('abc',29,'Software engineer');
var person2=new Person('def',27,'Docter');

person1.sayName();//abc
person1.sayName();//def
```
<ul>（1）区别：
 <ol>没有显示地创建对象；</ol>
 <ol>直接将属性和方法赋值给了this对象；</ol>
 </ul>
