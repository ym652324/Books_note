## 第2章：let和const命令  
### 一、let命令
1. 概念  
let用于声明变量，但只在let所在的代码块内有效。 
2. 用于for循环  
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
