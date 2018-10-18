# 第2章：let和const命令  
## 一、let命令
### 1. 概念  
let用于声明变量，但只在let所在的代码块内有效。 
### 2. 用于for循环  
> 
```
var a=[];
for(var i=0;i<10;i++){
  a[i]=function(){
    console.log(i);
  };
}
a[6](); //10
```  
以上代码中，i是全局有效的，所以每次循环新的i值都会把旧的i值覆盖，导致输出的是最后一轮循环的i值。若使用let，最后将输出6。
> 
```
var a=[];
for(let i=0;i<10;i++){
  a[i]=function(){
    console.log(i);
  };
}
a[6](); //106
```
### 3.不存在变量提升
let不像var一样会发生变量提升，所以必须先声明再使用，否则会报ReferenceError  
### 4. 暂时性死区  
只要块级作用域内存在let命令，它所声明的变量就绑定这个区域，只要在let声明变量之前使用该变量就会报错。这在语法上成为“暂时性死区”（TDZ）
>
```
if(true){
  tmp='abc';//ReferenceError
  console.log(tmp);//ReferenceError
  let tmp;//TDZ结束
  console.log(tmp);//undefined
  tmp=123;
  console.log(tmp)//123
}
```
### 5.不允许重复声明
let不允许在相同作用域里重复声明一个变量。  
## 二、块级作用域  
### 1.为什么需要块级作用域
没有块级作用域，可能导致内层变量覆盖外层变量；在用变量计数循环时循环变量会泄露为全局变量。
### 2. 应用  
块级作用域使得立即执行匿名函数（IIFE）不再必要了
```
//IIFE写法
(function(){
  var tmp=1;
  ...
}());

//块级作用域写法
{
  let tmp=1;
  ...
}
```
ES6也规定函数本身的作用域在其所在的块级作用域之内，并且块级作用域外部无法调用块级作用域内部定义的函数。  
 ```
{
  let a='secret';
  function f(){
    return a;
  }
}
f();//报错

//应该这样处理
let f;
{
  let a='secret';
  f=function(){
    return a;
}
f();//secret
```
