## 第五章：引用类型  
### 一. Object类型  
#### 1. 创建Object实例方式  
（1）使用new操作符以及Object构造函数  
```
var person = new Object();
person.name='abc';
person.age=29;
```
 (2) 使用对象字面量表示法  
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
