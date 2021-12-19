### 类数组和Array.from  

1. 类数组转成数组会自动给他加一个length
2. 第三个参数配置   常量   perfix 前缀 可以被使用
3. 只有一个必须的参数 ：array.from.length   的长度为1

```javascript
var obj = {
    0:1,
    1:2,
    2:3,
    length:3
}
const newarr = Array.from(obj,function (item,index) {
    return{
        studentID:this.prefix+item,
        order:index
    }
},{prefix:'no.'})  // 后面也可以加配置 
// foreach   map    filter   every   some   find  都有回调 ， 也有相关的配置
console.log(newarr)
```

![image-20211217183323213](JavaScript.assets/image-20211217183323213-16397372053781.png)

### new Object   

new 出来的不是原始值

```JAVA
 var a =1;
        var newA=new Number(a);
        console.log(a===newA);
```

这是原始值这能一样吗？       new 出来的是不一样的东西  new 代表新空间了。  

#### object.keys  / getOwnPropertyNames 

getOwnPropertyNames   忽略了描述符。

```javascript
   var object ={a:1, b:2, c:3, d:4, e:5, f:6}
        Object.defineProperty(object,'b',{
            enumerable:false
        })
    console.log(Object.keys(object))
    console.log(Object.getOwnPropertyNames(object))
```

下面的可以枚举b出来 

#### with 语句

使用 with 语句的主要场景是针对一个对象反复操作  

把对象名字放在with里面默认指向就是with里面的对象如果发现连接不上那就去属性里面找 ，最后操作的不是对象而是属性。

```javascript
with(location) { 
 let qs = search.substring(1); 
 let hostName = hostname; 
 let url = href; 
} 
```

#### 块级作用域

**If语句，switch语句，循环语句等语句块中定义变量**

外部访问不到里面的 变量就是块级作用域 。 

let 和const 不可以重复声明  有块级作用域 。    var  可以  没有块级作用域 。 

 也就是说在上面那些语句包裹的变量在外部可以访问得到 ，  函数内除外。   。 

**执行上下文分全局上下文、函数上下文和块级上下文** 

#### 内存泄漏

1. 不使用上 var、let 或 const 关键字 就声明变量导致变量被加到window上面去了  ，直到网页关闭才会清除
2. 定时器使用变量如何这个定时器不关闭那么这个变量不会去清除
3. 闭包导致，返回函数 函数中需要引用外部的变量   这个函数在调用的时候 就一直不清楚 这个变量 。 。 

### 基本引用类型

1. 引用类型与原始值包装类型的主要区别在于对象的生命周期

就是说基本的引用类型是没有属性的 ，  对象才有属性。 可以去添加属性。

2. 所有对象在布 尔表达式中都会自动转换为 true

3. 理解原始布尔值和 Boolean 对象之间的区别非常重要，强烈建议永远不要使用后者

```javascript
 let falseObject = new Boolean(false);   // 实际是true
let result = falseObject && true;  
console.log(result); // true 
let falseValue = false; 
result = falseValue && true; 
console.log(result); // false 
console.log('--------------------------------------------------------'); //
console.log(typeof falseObject); // object 
console.log(typeof falseValue); // boolean 
console.log(falseObject instanceof Boolean); // true  
console.log(falseValue instanceof Boolean); // false  他是对象吗?  不是
```

对象和原始值是不一样的   1. 对象出来会自动转换成true  2 . 强烈建议使用原始值就行了 。 不要去new 对象   

#### Number 类型 

1. tostring  方法  将数字转成不同进制的数字 。 
2.  tifixed 方法   将数字接受参数   参数表示我要保存几位小数 四舍五入的方式 。  最大是支持20位小数 ，  
3. isInteger  方法 辨别一个数值是否是一个整数 。  

#### Global

ECMA-262 规定 Global 对象为一种兜底对象，它所针对的是不属于任何对象的属性和方法   = 》    全局变量或全局函 数就是他  

 isNaN()、isFinite()、parseInt()和 parseFloat()，实际上都是 Global 对象的方法    

浏览器window 实现他的代理 

####  eval()方法

是一个完 整的 **ECMAScript 解释器**，它接收一个参数，即一个要执行的 ECMAScript（JavaScript）字符串

用来解析js代码的。  

**注意**: eval()的时候必须 极为慎重  要避免xss 的攻击噢。  





