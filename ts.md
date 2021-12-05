

# TypeScript 

1. **静态类型**的好处
   - 杜绝手误导致的变量名写错。
   - 自动完成。
   - 重构支持。
   - 类型可以一定程度上充当文档
2. 编译选项

tsconfic里面放的是   编译器的配置

outfile 代码合成一个模块

outdir 用来指定编译后文件所在的目录./dist

module 指定模块化的规范

 lib  指定模块的类库

“inlude" 编译的目录

allowjs'  true 是否对js文件进行编译

checkjs  检查js代码是否符合语法的规范

removeComments ture 是否移除注释

noemit false 不生成编译的文件 

noemitoonerror false  有错误时不生成编译文件

 alawsstrict true      用来设置严格模式   use 

noimplicitany  不允许隐式的any的类型 手动指定any解决

strictnullchecks  在编译的时候如果有空的情况会报错

strict  严格检查的总开关   true   使代码更严谨

3. 使用webpack打包ts代码

对项目进行初始化 npm init -y

cnpm i -D webpack webpack-cli typescript ts-loader

安装好四个包

​      const path =require("path")



module.exports= {

entry"指定入口的们见“

output:path.resolve(__dirname, "dis")

filename：js

}

module:{

rules:【写入规则】

test 指定的是规则生效的文件

user ‘ts-loader

}





#### gitee项目上传到远程仓库中

1. 打开项目文件夹gitbush一下  git clone +地址  项目里自动生成一个本地仓库文件 里面confic 文件可以设置配置 

2. 把项目放入本地仓库中 

3. 仓库文件中cmd  git add .  -> git commit -m "beizhu" ->

   git pull origin master -> git push -u origin master  结束 

#### git的使用

1. git branch 名字   创建分支
2. git checkout 名字  切换到分支上
3. git merge 名字  将..合并到主分支上
4. git clone 复制仓库
5. git fetch 获取远程的数据
6. git pull  先抓取再合并

#### 一个ts项目 贪吃蛇

1. package.json文件

```tsx
$ npm init
```

可以自动生成文件name  version  是必填的

`peerDependencies`字段，就是用来供插件指定其所需要的主工具的版本



bin项用来指定各个内部命令对应的可执行文件的位置



`main`字段指定了加载的入口文件，



`require('moduleName')`就会加载这个文件。这个字段的默认值是模块根目录下面的`index.js`。



配置文件  ：  用init自动生成

2. ##### package-lock.json 文件

当运行 `npm update` 时，`package-lock.json` 文件中的依赖的版本会被更新。



`package-lock.json` 会固化当前安装的每个软件包的版本，当运行 `npm install`时，`npm` 会使用这些确切的版本。

3. tsconfig.json

- 如果一个目录下存在一个`tsconfig.json`文件，那么它意味着这个目录是TypeScript项目的根目录。 `tsconfig.json`文件中指定了用来编译这个项目的根文件和编译选项
- `"files"`指定一个包含相对或绝对文件路径的列表。 `"include"`和`"exclude"`属性指定一个文件glob匹配模式列表

### 学习笔记

#### food类

![image-20211022194440720](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211022194440720.png)

 get  x 返回从左到右的距离

get y 是返回从上面到下面的距离



当按下一个键的时候就调用一个方法让蛇进行移动

```ts
init(){ document.addEventListener('keydown',this.keydownHandler.bind(this));
    this.run();
```

![image-20211022223524359](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211022223524359.png)



#### 取整

```ts
Math.round    向上取整
```

```ts
Math.floor   向下取整
```

#### 设置样式的属性值

```tsx
this.element.style.left = left + 'px'; 
```

#### 插入html

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211023155231646.png" alt="image-20211023155231646"  />



#### 类型断言（Type Assertion）

语法：值 as 类型   或   <类型>值  

告诉编译器具体的类型是什么

总结：

- 联合类型可以被断言为其中一个类型
- 父类可以被断言为子类
- 任何类型都可以被断言为 any
- any 可以被断言为任何类型

#### ts中变量的声明方式

```tsx
maxLevel: number;    score = 0;  
```

 格式是 不带var let  const    变量名字：变量的类型 后面可以赋值 也可以不赋值   不说变量的类型那么这个变量的类型就是any   

var和不var 的区别： 带var    在当前域中那么声明的就是这个域的局部变量 在外面的带var就是全局变量
  不带var 只是对属性赋值操作 

```markdown
HTMLElement   对象表示html中的一个元素 用dom方法获取
```

#### 修改开始标签和结束标签之间的html

![image-20211023162834980](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211023162834980.png)

innerhtml方法改两个标签之前的内容    可以拼串

<html id=myanchor>runoob </html>

后面跟属性名可以修改标签内的属性值

#### HTML DOM addEventListener() 方法

![image-20211023164219777](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211023164219777.png)

语法：

```js
document.addEventListener(*event*, *function*, *useCapture*)
```

三个参数：事件名称，方法，ture or false  代表的是是否捕获的时候执行方法 。

#### 定时器

![image-20211023172830096](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211023172830096.png)

需要传两个参数   代码执行一次    方法名，时间 ，时间不写默认立即开始   第三个可以给方法传参

- setTimeout之行前终止其运行就可以使用clearTimeout()。
- clearTimeout()用于重置js定时器，如果你希望阻止setTimeout的运行，就可以使用clearTimeout方法
-  window.setInterval(调用函数, 延时时间);  反复的调用 这个方法
- 注意：就算设置为0秒 还是比window里的方法要慢

#### querySelector和getelbyid  的区别

前者后面是要用 . #        

element.getElementsByTagName('标签名'); 父元素必须是                            指定的单个元素

```
getElementsByClassName 根据类名获得某些元素集合
```

```
 querySelector 返回指定选择器的第一个元素对象  切记 里面的选择器需要加符号 .box  #nav
```

```
querySelectorAll()返回指定选择器的所有元素对象集合
```

```
1.获取body 元素
var bodyEle = document.body;
```

```
2.获取html 元素
// var htmlEle = document.html;
var htmlEle = document.documentElement;
```



#### 事件的三要素

```js
// 1. 事件是有三部分组成  事件源  事件类型  事件处理程序   我们也称为事件三要素
//(1) 事件源 事件被触发的对象   谁（任意对象）  按钮
var btn = document.getElementById('btn');
//(2) 事件类型  如何触发 什么事件 比如鼠标点击(onclick) 还是鼠标经过 还是键盘按下
//(3) 事件处理程序  通过一个函数赋值的方式 完成
btn.onclick = function() {
    alert('点秋香');
}  过程：获取事件源，绑定事件，添加事件处理方法
```

#### innerhtml 和text 的区别

** innerHTML指的是*从对象的起始位置到终止位置的全部内容,包括Html标签。
**  innerText指的是从起始位置到终止位置的内容,但它去除Html标签。

#### 修改元素的属性

```
描述：设置元素的【属性】
    语法：元素名.setAttribute('属性','属性值');
```

```
描述：获取属性值
    语法：元素名.getAttribute('属性名')；
```

```
描述：删除一个属性
    语法：元素名.removeAttribute('属性名');
```

```
 2.1.1获取css样式
   语法：元素名.style.样式名   直接得到
```

```
 2.1.2设置css样式
    语法：元素名.style.样式名="属性描述"  为空的时候就是清除的意思直接写null也行
```

```
注意：
       1.只能操作行内样式
       2.当设置的样式含有单位时 则必须+单位
       3.如果样式是js中的关键字 则需要在样式前+css
       4.如果样式由下划线连接 则需要去掉下划线将后面的单词首字母变为大写
```

```
4.1设置样式
    语法：通过元素名.style.setProperty();
    例子：
       box.style.setProperty('background-color','red');
       box.style.setProperty('height','100px');
4.2获取样式值
    语法：元素名.style.getPropertyValue('样式名')
      console.log(box.style.getPropertyValue('width'));
4.3清除样式
   语法：元素名.style.removeProperty('样式名');
     box.style.removeProperty('height');
```

```
1.1setAttribute('属性名'，'属性值')
    描述：关联内部样式
    语法：setAttribute('属性名'，'属性值');
     注意：
       1.可以追加自定义属性的
         div.setAttribute('a','box');
       2.多次对一个属性设置值 则最后一次生效
         var div = document.querySelector('div');
         div.setAttribute('class','a');
         div.setAttribute('class','box');
 1.2removeAttribute  删除【属性】
     div.removeAttribute('class');
    例子：
         var div = document.querySelector('div');
         div.setAttribute('class','a');
         div.setAttribute('class','box');
         div.removeAttribute('class');

```

```
1 className
   描述：设置元素的类及其值
   语法：元素名.className
   例子：
       var div = document.querySelector('div');
       div.className = 'box';
   注意：当一个属性多次被赋值则最后一次赋值有效
       div.className = 'a';
       div.className = 'box';//有效

2清除类名
    div.className='';

```

#### 属性的增删改

原版的方式：element.属性= '值'  修改  class特殊点变成className     不支持自定义

用啊球biu特     支持自定义属性

```js
element.setAttribute('属性', '值'); 
```

getAttribute()   setAttribute()  removeAttribute()

#### H5自定义属性

```js
dataset 是一个集合里面存放了所有以data开头的自定义属性
```

获取方式是emlement.dataset     属性的命名方式是data-后面连接名字    获取data只需要写data后面的

如果自定义属性里面有多个-链接的单词，我们获取的时候采取 驼峰命名法

#### console.dir()的使用

dirxml可以打印出div本身和标签内的节点元素 用于节点问题

16. 节点相关

elelment.parentNode     获取最近的父节点 ，

elelment.childNodes   获取所有的子节点  标签和标签内的内容也读  

ul.children  获取的是ul里面的子元素节点  只读标签

**元素节点的nodeType属性值是1。**
**属性节点的nodeType属性值是2。**
**文本节点的nodeType属性值是3。**

#### 克隆节点

```
// 1. node.cloneNode(); 括号为空或者里面是false 浅拷贝 只复制标签不复制里面的内容
// 2. node.cloneNode(true); 括号为true 深拷贝 复制标签复制里面的内容
```

innerHtml的拼接效率数组的形式最高

#### 注册事件

有两种方式可以注册事件   1. 元素.事件名=function(){   } 2.

```js
btns[1].addEventListener('click', function() 
```

attachevent  在ie9之前也可以注册事件现在用的少 

#### 删除事件 

传统的方式删除直接=null    元素.事件名=null；

```js
divs[0].onclick = null;
```

```js
divs[1].removeEventListener('click', fn);
```

```js
divs[2].detachEvent('onclick', fn1);
```

fn指的是要删除的函数名字   参数第三个可以传 *useCapture* 默认是等于false  在冒泡的时候删除或者true是在捕获的地方。

#### 事件对象

```js
// 1. event 就是一个事件对象 写到我们侦听函数的 小括号里面 当形参来看
// 2. 事件对象只有有了事件才会存在，它是系统给我们自动创建的，不需要我们传递参数
// 3. 事件对象 是 我们事件的一系列相关数据的集合 跟事件相关的 比如鼠标点击里面就包含了鼠标的相关信息，鼠标坐标啊，如果是键盘事件里面就包含的键盘事件的信息 比如 判断用户按下了那个键
// 4. 这个事件对象我们可以自己命名 比如 event 、 evt、 e
// 5. 事件对象也有兼容性问题 ie678 通过 window.event 兼容性的写法  e = e || window.event;
```

```
event.target.nodeName 　　//获取事件触发元素标签名（li，p，div，img，button…）
event.target.id　　　　　　//获取事件触发元素id
event.target.className　　//获取事件触发元素classname
event.target.innerHTML　 //获取事件触发元素的内容（li）
```

e.target 点击的对象              this和currentTarget  指向的就是调用者  调用方法的对象

#### 事件对象阻止默认行为的方法

默认行为就是一个事件触发了不是方法内的是本身标签就特有的方法  只需要在方法体内 return false 就可以让默认事件不发生   或者e.preventDefault();

#### 阻止事件冒泡

```js
e.stopPropagation(); // stop 停止  Propagation 传播
e.cancelBubble = true; // 非标准 cancel 取消 bubble 泡泡
```

#### 事件委托

在一个标签下很多子标签的情况下 我们只需要注册一个父元素的监听器  然后利用e.target 是指的的点击的元素  让单个元素发生变化

```js
var ul = document.querySelector('ul');
ul.addEventListener('click', function(e) {
    // alert('知否知否，点我应有弹框在手！');
    // e.target 这个可以得到我们点击的对象
    e.target.style.backgroundColor = 'pink';
    //将点击的对象设为pink
})   ul内存在很多li标签
```

#### 鼠标事件对象   获取鼠标点击的坐标方法

```js
document.addEventListener('click', function(e) {
    // 1. client 鼠标在可视区的x和y坐标
    console.log(e.clientX);
    console.log(e.clientY);
    console.log('---------------------');
    // 2. page 鼠标在页面文档的x和y坐标
    console.log(e.pageX);
    console.log(e.pageY);
    console.log('---------------------');
    // 3. screen 鼠标在电脑屏幕的x和y坐标
    console.log(e.screenX);
    console.log(e.screenY);
})
```

#### 跟随鼠标的图标

```js
var pic = document.querySelector('img');
document.addEventListener('mousemove', function(e) {
    // 1. mousemove只要我们鼠标移动1px 就会触发这个事件
    // console.log(1);
    // 2.核心原理： 每次鼠标移动，我们都会获得最新的鼠标坐标， 把这个x和y坐标做为图片的top和left 值就可以移动图片
    var x = e.pageX;
    var y = e.pageY;
    console.log('x坐标是' + x, 'y坐标是' + y);
    //3 . 千万不要忘记给left 和top 添加px 单位
    pic.style.left = x - 50 + 'px';
    pic.style.top = y - 40 + 'px';
```

#### location

```js
// 记录浏览历史，所以可以实现后退功能
// location.assign('http://www.itcast.cn');
// 不记录浏览历史，所以不可以实现后退功能
// location.replace('http://www.itcast.cn');
```

```js
location.href = 'http://www.baidu.cn';
//给事件源绑定页面跳转
```

#### offset系列

```js
// offset 系列
var father = document.querySelector('.father');
var son = document.querySelector('.son');
// 1.可以得到元素的偏移 位置 返回的不带单位的数值  
console.log(father.offsetTop);
console.log(father.offsetLeft);
// 它以带有定位的父亲为准  如果么有父亲或者父亲没有定位 则以 body 为准
console.log(son.offsetLeft);
var w = document.querySelector('.w');
// 2.可以得到元素的大小 宽度和高度 是包含padding + border + width 
console.log(w.offsetWidth);
console.log(w.offsetHeight);
// 3. 返回带有定位的父亲 否则返回的是body
console.log(son.offsetParent); // 返回带有定位的父亲 否则返回的是body
console.log(son.parentNode); // 返回父亲 是最近一级的父亲 亲爸爸 不管父亲有没有定位
```

```js
// offset与style的区别  
console.log(box.offsetWidth);  //无单位
console.log(box.style.width);  //有单位
```

#### 计算鼠标在盒子里面的坐标

```js
// 我们在盒子内点击， 想要得到鼠标距离盒子左右的距离。
// 首先得到鼠标在页面中的坐标（ e.pageX, e.pageY）
// 其次得到盒子在页面中的距离(box.offsetLeft, box.offsetTop)
// 用鼠标距离页面的坐标减去盒子在页面中的距离， 得到 鼠标在盒子内的坐标
var box = document.querySelector('.box');
box.addEventListener('mousemove', function(e) {
    // console.log(e.pageX);
    // console.log(e.pageY);
    // console.log(box.offsetLeft);
    var x = e.pageX - this.offsetLeft;
    var y = e.pageY - this.offsetTop;
    this.innerHTML = 'x坐标是' + x + ' y坐标是' + y;
})   
```

#### mouseenter和mouseover的区别

不论鼠标指针穿过被选元素或其子元素，都会触发 mouseover 事件。

只有在鼠标指针穿过被选元素时，才会触发 mouseenter 事件。

#### 学习程序

1. 要求：

![image-20211028000045009](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211028000045009.png)

2. 多线程学习

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211028000200906.png" alt="image-20211028000200906" style="zoom:150%;" />



3. 如何深入的学习

![image-20211028000528607](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211028000528607.png)

#### 操作

多行复制多行操作 ：Ctrl键配合使用

替换                          ：ALT+R

32. unshift()和push方法

前者是将元素加在数组的前面，后者是将元素加在数组的后面

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.unshift("Lemon","Pineapple");
```



#### 排序

假设有一个包含学生名字和年级的列表，已经将它按学生名字字母顺序进行预排序：

```js
const students = [
  { name: "Alex",   grade: 15 },
  { name: "Devlin", grade: 15 },
  { name: "Eagle",  grade: 13 },
  { name: "Sam",    grade: 14 },
];
```

对这个数组执行 `grade` 升序排序后：

```js
students.sort((firstItem, secondItem) => firstItem.grade - secondItem.grade);
```

   总结：利用sort方法里面传数组里两个比较的元素，
升序前减后 ；降序后减前

#### splice方法

**`splice()`** 方法通过删除或替换现有元素或者原地添加新的元素来修改数组,并以数组形式返回被修改的内容。此方法会改变原数组。

  总结：传入三个参数 **start**开始的索引 **deleteCount**删除的个数  **item1**后面要添加的数组从start位置开始

#### Vue.set()和this.$set()介绍、

区别在于Vue.set()是将set函数绑定在Vue构造函数上，this.$set()是将set函数绑定在Vue原型上。

set函数接收三个参数分别为 target、key、val，其中target的值为数组或者对象，这正好和官网给出的调用Vue.set()方法时传入的参数参数对应上。

```js
this.$set(this.student,'sex','男')  
```

#### 过滤Array.prototype.filter()

```jsjsx
let nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
let res = nums.filter((num) => {
  return num > 5;
});
console.log(res);  // [6, 7, 8, 9, 10]
```

```js
this.student.hobby = {this.student.hobby.filter((h)=>{
   return h !== '抽烟'
```

  总结：利用箭头函数h代表需要过滤的数组对象，后面可以返回符合过滤条件的数组

#### 内置指令   优化

v-text   将里面的内容全部替换

v-html  替换html里面的全部内容只要是html里面的标签都可以使用

v-clock  本质是一个特殊属性，Vue实例创建完毕并接管容器后，会删掉v-cloak属性。解决网速慢的问题

v-once   所在节点在初次动态渲染后，就视为静态内容了。

v-pre  放在一些不需要vue来编译的可以加快速度

#### 修改mysql数据库的密码

```mysql
ALTER USER 'root'@'localhost' IDENTIFIED BY '123456';
```

#### 请求不到数据的情况

```js
const { data: res } = await this.$http.delete(`goods/${id}`)
```

这里的url  后面不是用单引号 是用   ---------   **反引号** 

#### token登陆原理

1. ![image-20211103221510900](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211103221510900.png)

总结：请求登入之后服务器给客户端一个token便于下次不用再次请求登陆

#### 前端项目初始化

1. ![image-20211103233800210](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211103233800210.png)



#### 后端项目环境安装配置

1. ![image-20211103233849325](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211103233849325.png)

#### 操作

1. npm install安装依赖项
2. npm run serve  和 控制台输入 vue ui 是一样的启动的是脚手架

#### 遇到的问题

1. No ESLint configuration found       ESLint  没有安装

解决方案是：安装   npm i eslint -g   生成配置i文件eslint --init

#### 什么是ESLint？ 如何使用特点 配置相关

1. ESLint 是一个用来识别 ECMAScript/JavaScript 并且按照规则给出报告的代码检测工具。

   总结：ESLint 就是一个工具，而且是一个用来检查代码的工具。

2. 初始化

```js
# 全局安装 ESLint
$ npm install -g eslint
# 进入项目
$ cd ~/Code/ESLint-demo
# 初始化 package.json
$ npm init -f
# 初始化 ESLint 配置
$ eslint --init
```

总结：..

3. ESlint的特点

- 内置规则和自定义规则共用一套规则 API。
- 内置的格式化方法和自定义的格式化方法共用一套格式化 API。
- 额外的规则和格式化方法能够在运行时指定。
- 规则和对应的格式化方法并不强制捆绑使用。
- 每条规则都是各自独立的，可以根据项目情况选择开启或关闭。
- 用户可以将结果设置成警告或者错误。
- ESLint 并不推荐任何编码风格，规则是自由的。
- 所有内置规则都是泛化的。

#### bable是什么？ 

是把高级的es6转化成es5的工具 

#### 登入页面

1. ：model=“data数据”   最外层的

 v-model =”data数据里面的某个属性值

```js
model="loginForm.username"
```

```js
prefix-icon="el-icon-lock"
```

2. 用于表单输入框的前面的图标属性

```js
:loading="loginLoading"
```

3. e-button里面的是否加载属性  在data里面
4. 表单的验证规则

```js
:rules="loginFormRules"
```

最外层绑定规则

```js
el-form-item prop="username"
```

在每个输入表单中定义prop

```js
loginFormRules: {
  username: [
    {
      required: true,  
      message: '请输入登录名称',
      trigger: 'blur'
    },
```

在data里面定义

5. 表单重置

| resetFields | 对整个表单进行重置，将所有字段值重置为初始值并移除校验结果 |
| ----------- | ---------------------------------------------------------- |
|             |                                                            |

ref是resetFields的缩写

```js
ref="loginFormRef"   //在组件的this中发现￥refs的属性值和这个一样
```

<img src="C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20211105215532624.png" alt="image-20211105215532624" style="zoom:100%;" />

我们为重置按钮绑定单机事件

```js
<el-button type="info" @click="resetLoginForm">重置</el-button>
```

在data后面我们methods中定义方法

```js
this.$refs.loginFormRef.resetFields()
```

refs可以调用这个方法

ref是整个表单的引用

6. 表单的预验证

| validate | 对整个表单进行校验的方法，参数为一个回调函数。该回调函数会在校验结束后被调用，并传入两个参数：是否校验成功和未通过校验的字段。若不传入回调函数，则会返回一个 promise | Function(callback: Function(boolean, object)) |
| -------- | ------------------------------------------------------------ | --------------------------------------------- |
|          |                                                              |                                               |

拿到ref的引用之后可以进行表单预验证 回调第一个是验证的布尔值

争对布尔值进行一个函数

