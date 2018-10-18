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
