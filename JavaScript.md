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

##### new 这个过程做了哪些事情？ 

创建空对象 this 指向他继承函数的原型 往这个空对象加属性和方法，新建的对象被this所引用，隐式的返回this  

```javascript
var obj = {};
obj.__proto__ = Base.prototype;
Base.call(obj);
```

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



#### 迭代方法

 every 和 some 是相反的  传入的函数返回一个true  那结果是true 是some反之必须要全部是true 结果是true 是every      **every每个真才真，some一个真就算真

#### 事件捕获和冒泡

捕获从外到内

冒泡从内到外

#### 代理

```javascript
const proxy = new Proxy(target, handler); 
```

参数一代理目标 对象      参数二捕获器的方法名

代理没有自己的原型  所有instanceof 没有用的

===用来区分代理和目标对象

```javascript
const target = { 
    foo: 'bar' 
   }; 
   const handler = { 
    // 捕获器在处理程序对象中以方法名为键
    get() { 
    return 'handler override'; 
    } 
   }; 
```

handle 是代理的第二个参数也就是捕获器的名字

每当代理需要读取任何属性的时候都会去触发这个方法拿到方法的返回值 。

#### 函数的柯里化

```javascript
function sum(x) {
    return function (y) {
        return function (z) {
            return x + y + z;
        };
    };

    }  
sum(1)(2)(3);
  console.log(sum(1)(2)(3));
```

解释：  柯里化是一种将使用多个参数的一个函数转换成一系列 使用一个参数的函数的技术

#### 创建对象的方法 

1. 字面量创建 

   ```java、
   var obj = {}   
   ```

2. new 出来的对象 

3. 使用显式的构造函数创建的函数          函数名字第一个字母的是大写

4. 利用对象的create 方法 创建 。

#### 原型、构造函数、实例、原型链

1. Object.prototype属性原型链的顶端 。
2. 引用类型（非基本数据类型）都有proto属性，所有函数都有prototype属性是一个普通的对象    

#### Es5 es6 声明一个类

5 函数声明    6 构造器声明

```javascript
class wo{
    constructor() {   
        this.name = name; //  函数直接可以赋值了 。 
        this.sex = sex;
    }
}
wo.sex='name'
console.log(wo.sex);
```

#### call、apply的共同点与区别

都是改变this 的指向  this 指向改变之后就是改变了对象的作用域 。 

apply 后面只可以传一个数组包含全部的参数  

```javascript
var myFun = function (arg1, arg2) {
    return arg1 === arg2
};
//调用
myFun.call(this,1,1); // true
myFun.apply(this, [1, 1]); // true
```

#### 对象的继承

```javascript
function Parent5() {
this.name = 'name';
this.play = [1, 2, 3];
}
function Child5() {
Parent5.call(this);
this.type = 'child5';
}
Child5.prototype = Object.create(Parent5.prototype); // Object.create创建的对象 就
是参数 Child5.prototype.constructor = Child5; var s7 = new Child5();
console.log(s7 instanceof Child5, s7 instanceof Parent5);
console.log(s7.constructor); // 构造函数指向Child5 他是利用chdld5函数构造的
```

**bind **  不可以使用函数声明式  只可以使用函数表达式           绑定之后不会调用 **要自己去调用**

返回的是新对象           上面只是改变函数的this指向

#### 闭包的应用

 函数的嵌套  默认是作用域链是从内往外找变量的 但是闭包可以实现从外部拿到函数作用域里面的变量，并且保持对变量的引用不被垃圾回收 ， 将最外层的函数赋给一个标识符

1. 作为返回值  2. 作为参数来传递

#### 语义化的好处？

H5   (audio,video)    (Canvas)  (Geolocation)  新：webworker, websocket,

（header,nav,footer,aside,article,section）

1. 基本上不用写什么样式就可以正常表示。
2. 利于seo  。
3. 方便其他无障碍设备渲染 。
4. 便于开发维护可读性强，减少差异化。 

#### 浮动的原理

1. 浮动遇到浮动就不可以移动了。 

消除：

1. overflow:auto/ hidden; zoom:1;
2. 加一个空标签   定义cssclear:both  修改两边标签的样式
3. after伪类可以清除浮动。

浮动会发生什么问题

1. 因为浮动起来了所以父元素的高没有元素去撑开
2. 其他元素将会替换掉浮动元素的位置 。
3. 若第一元素浮动了其他元素也要跟着浮动。

怎么解决？

```javascript
.clearfix:after{content:".";display: block;height:0;clear: both;visibility: hidden;}
 .clearfix{display: inline-block;} /* for IE/Mac */
```



#### 浏览器存储

1. 本地离线存储 localStorage 长期存储数据

2. sessionStorage 的数据在浏览器关闭后自动删除

#### null 和undefined 的区别

1. 数值上null 是 0   undefined  是NaN
2. null 表示不存在的对象**不应该有值**，  undefined 表示本来**应该**有值但是没有赋值

#### 手写ajax 是必须的

```javascript
 var xhr = new XMLHttpRequest(); // new 对象
        xhr.open('GET', 'demo.php', 'true'); // 创建请求
        xhr.send()  // 发送请求
        xhr.onreadystatechange = function () { // 根据返回的数据来接受数据
            if (xhr.readyState === 4 & xhr.status === 200) {
            }
        }
```

**get和post**请求方法的区别

1. get 获取信息，url 限制在2000个字符
2. post 修改服务器的数据，  发送的信息没有限制
3. get 是根据url传值，post 通过提交表单来传值

#### JS异步加载和延迟加载

1. 插入script 标签   defer  或者async  实现
2. 创建并且插入  i frame
3. 通过ajax 去获取js代码 然后利用eval执行 。 

#### 同源策略？为什么要有这个？

协议，域名，端口相同，同源策略是一种安全协议。

**为什么？** 

比如一个黑客程序，他利用Iframe把真正的银行登录页面嵌到他的页面上，当你使用真 实的用户名，密码登录时，他的页面就可以通过Javascript读取到你的表单中input中的内容，这样用户 名，密码就轻松到手了。

#### document.write()的用法

document.write只能重绘整个页面。innerHTML可以重绘页面的一部分

#### 事件代理（事件委托）

原本需要绑定的事件绑在父元素让父元素去监听

原理： dom元素的事件冒泡，可以提高性能

#### 说mongoDB和MySQL的区别

monggo是nosql 型的数据库  以二进制的形式来存储的，对海量的数据存储有明显的优势

优点： 1. 最终一致 保证用户的访问速度 2. 文档结构的存储方式 便捷的获取数据 。

#### 304缓存的原理

http码304 状态码    表示了服务器对这个数据没有进行更改 ，不返回任何的内容   

1.  请求 之后  A页面               服务器返回A 页面 并且需要加上 ETag 一起缓存
2. 之后再次发请求这时会带上etag  服务器发现这个页面（带上etag的页面）没有改变 然后返回304  未修改 和空的响应体。  



