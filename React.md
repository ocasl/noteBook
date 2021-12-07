# React

### 碎屑：

style Component    CSS  moudule    css 优化的方案 

antd  elemenent  ui     Materrial ui     CSS 框架 

单元测试 ， 集成测试 ， jest  enzyme   测试相关  

ts flow  eslint      prettier                         提升代码质量 

eslint 和prettier  什么区别  ? **eslint：** 用过 保存之后会让代码变得很好看 ， **他解决了代码质量问题 ** 这块做得比较好的是airbnb公司 他有一套**最好的完整**规范 install  eslint-config-airbnb  安装了他的规范还不行  你没说你要用啊 ，所以在.eslintrc中  {“extends”：【‘airbnb’】}我要继承这个配置文件 

**prettier：**解决代码风格的问题 ， 也是要在eslint 的配置文件extends：“perttier”  并且要放在最后才有用   也可以安装插件安装了插件之后我们可以自己自定义prettier  

```javascript
{
  "extends": ["plugin:prettier/recommended"]
}
```

echart       antV      highchart     			数据可视 化、

next.js     nuxt.js                    服务器渲染ssr 

react nactive       weex 微信小程序    hybird    flutter    移动端

微信  支付宝   头条      小程序        		 跨端**uni-app**      taro   

Electron    桌面应用       静态网站搭建  vuepress  hexo    

起飞......................................  这辈子值了   

前端重要的科班 ：  计算机网络 ，系统 ， 算法 。





又是一个js库，发送请求获取数据 ，处理数据 操作dom 

给他数据react 给他渲染  facebook 开发 jordanwalke 

newsfeed  部署   随后在ins 里面 开源 

dom api   导致大量的重绘重排

声明式编码 优秀的diff算法  虚拟dom   jsx 语法糖可以创建虚拟dom



在react中虚拟dom 会被react 转化成真实的dom 

xml 早期用于存储和传输信息 。 

 json代替了他  。

#### 三个核心库

recat   			 react-dom   			.bable

#### 写法

定义一个组件 的话标签必须要首字母是大写 。组件需要去定义 

 标签必须闭合 

内联样式 style={{balabal  }} 样式中的class 改成className 标签不需要写引号  。 

#### data 

1.  data中是不可以有对象的    数组可以遍历  

2. 在const vdom  = {这中间不需要写引号 ，  在引入data中的数据的时候需要{xxx巴拉巴拉  }  
3.   js 表达式 {   }表达式是有结果的 。能接收到一个值的

#### 模块

向外提供功能的js 文件  

#### 组件

结构样式功能都被抽离到一个文件上去了。 复用代码 

#### 模块化，组件化 ，工程化

巴拉巴拉。。

#### 面向组件编程。。。

开发者工具 需要安装好 。

**组件**

函数定义组件 ：  

1. 第一步不是创建虚拟dom  是创建函数式的组件 
2.  利用renden的渲染函数 渲染 组件  在renden函数的组件名需要是大写的。首字母是大写 。 自闭和
3. this 拿不到组件本身在底层是严格模式

ReactDom.render(<Com/>组件名字首字母大写闭合起来)，document.getElementById(''test'');    渲染在id 为test 的元素内部 

4. 在这之后会发生什么？   找到组件  ， 发现组件是函数式的返回一个虚拟的dom 然后转化为 真实的dom  随后渲染在页面中 

#### 在react 可以使用到js中的类 。

1. 一个类在extends一个类之后我们 可以不用写构造函数 ，如果要 添加相关的属性和方法就需要写构造函数 了。
2. 如果写了构造器那么我们这里是**一定**写super 
3. 类定义的方法， 类的原型对象 

tip： 类里面可以直接写赋值语句 给实例中添加一个属性

##### 类式组件 ?

1. class myComponent extend React.Commpoent   {巴拉巴拉}

   如果需要写一个类式组件那么需要继承react 的原型组件 

   构造器是可以省略的  

   但是必须要写render（）{<div>asddadasd}

2. 渲染组件到页面中

ReactDom.render(组件名首字母大写)  这里的render 和上面的render是不一样的 

ReactDom.render(组件名首字母大写) 如果使用的是类的组件那么底层会new出来组件实例 然后调用render方法  

#### 状态 

##### 严重注意：{

状态时不可以修改的需要借助内部的api  setState       

this.setState({对象})    合并的不修改其他不写就默认不变 **}** 

##### 发生一次状态改变  

render会修改1+n次包括第一次  ，构造器只调用一次，函数方法调用几次就调几次  如果绑定在点击事件了那么就是点几次就调用几次 

##### 为什么要写构造器

需要初始化 状态， 还可以解决this指向问题  。

##### 可以不写吗？ 

1. 可以的，因为在类中我们可以直接通过**赋值语句**给类的实例上写属性   

state ={对象 }      **对的**        this.setState({对象})   错的 。

2. 那函数方法呢？

 也可以写成赋值于 change =fun（）=>{babalala}  

**箭头函数**里面是没有this 的 如果写了 this就会往外面找  。 

《br》《br》《br》《br》《br》《br》《br》《br》《br》

状态影响 驱动 影响页面 

State是状态 。   状态是组件实例对象生成的  

函数和类式的组件  ，，  类式的组件才有state  函数只有通过参数传的props

hooks ： 函数式的组件也能有state 可以使用

**例子**：

1. 初始化操作必须放东西在state里面所以这里需要写构造器 

   props 为构造器的参数   super （props）  必须    

   这样才可以设置state的值 。。     数据的类型都可以放在这里 

2. 怎么把state读出来呢？ 

在渲染render函数中我们必须要const {hot}=this.state拿到这个 

用点 . this.state.isHot? '‘热'：“冷”  

hot 是一个函数可以绑定在onclick事件监听器 上  onclick ={hot}   把这个函数直接绑定在onclcik 事件上

3. 实例在react中  其他地方拿不到的 。   解决方案是 

在构造函数中写**that =this** 暴露出组件实例  

然后在外部可以使用组件实例   **原因**： 还是上面说到的组件实例是react去帮我们创建的  他的底层代码是开启了严格模式的所以我们在外部 甚至是在 组件类的函数方法里面也同样是拿不到的。     **解决方案**  如果我们要使用组件的方式我们可以让他不使用实例去调用这个方法  在绑定事件的时候我们可以this .function Name      

4.  bind函数    // 为了解决了 实例类对象方法的this指向问题 

```javascript
this.change =this.change.bind(this)
```

我们拿到了Weater原型上的方法挂载到了change 方法的实例对象去 了这样我们可以不通过调用werather 的实例对象去调用这个函数方法 	

bind 的参数是改变this 的本身 。  const x= bind （object）

**创建新的函数**  

####  props

简写： 

props 是**只读**的不能修改但是可以计算  

可以直接写在类里面的 。直接写赋值语句   static 的静态的

限制类的里面的属性的数据类型 isRequire  必传 

#### 类似组件中的构造器和props相关

 在类中只要写了 **构造器一定要super（）**

​	如果写了构造器 那么构造器的参数要传props 要不然他的实例是拿不到对象的实例的属性的    			 		  （接 传）

#### props的使用  

1.  函数可以接收参数  ，const{name，age，sex}=props     

  只能使用props

#### refs 

**标签**中加上ref**属性**就代表引用refs

在props 里面是refs 属性  但是在标签里面需要写ref   一个组件可以收集多个标签的ref  全部放在refs属性上面  

1. 字符串：refs：{name:input }  ref 取的名字（引用名字  ） 

//  过时了 不建议使用字符串  他存在一些问题 ：  字符串存在效率问题    但是没有太大的影响但是以后还是要写这种简单的

2. **最新的写法**  回调形式的写法 ： React.creatRef   

函数接受到什么参数 应该是谁调他得到谁  返回  

ref={c=>this.input1=c}      

ref 里面的函数react 会自动帮你调用  

状态驱动之后会render会重新调用一次 所有ref里面的函数还是会清空重新调用     **解决**：  通过ref 的回调函数class 的绑定函数方式可以解决这个问题	

在jsx写注释要写花括号内写注释

class 绑定函数的方式： ref =this.saveInput  已经放在了实例上了所以当数据更新之后还是不会重新调用这个函数 

函数放在外部绑定在类实例上面了 

**但是还是内联的写得多** 

#### 事件处理 

切勿过度使用ref   

#### 表单 

非受控组件  

表单提交是默认的事件    需要加事件修饰符

受控组件

随着输入我们把填入的数据绑定在state里面 和vue里面的v-model是一样的道理	 

**最好写受控组件**

#### 高阶函数 

1. 函数中接受参数是一个函数   
2. 一个函数的返回值也是一个函数 

promise   ， set timeout    arr.map 

####  函数的柯里化 

通过函数继续返回函数的方式实现多次接受参数处理函数编码的形式   **最后统一处理**



将数组写进函数的 参数中  



