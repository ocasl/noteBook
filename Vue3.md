### Diff算法

#### 有key

![image-20220106224322440](Vue3.assets/image-20220106224322440-16414802032463.png)



![image-20220106223318397](Vue3.assets/image-20220106223318397-16414795992002.png)

**红黑树的删除操作**

### 计算属性

#### 比method 返回值好在哪里 ？ 

1. method要反复的去调用，在插值语法{{}}中不容易看出插入的到底是什么东西  看到是一个方法名和一个括号
2.  计算属性有缓存  **只执行一次**

**对数据进行一些复杂的处理**







#### 对象的引用赋值， 和对象的浅拷贝

引用赋值是同一个对象

拷贝是两个对象

当一个对象里面还有一个对象之后，对象对自身内部的对象也是引用赋值 ，  当其他的对象拷贝这个对象的时候  拷贝到的就是一个 对象的引用  虽然对象本身 改变  复制之后的对象不会改变 但是在对象里面的那个对象  被复制的对象继续引用  /

![image-20220107212739498](Vue3.assets/image-20220107212739498-16415620604211.png)

```js
const obj = {
    name :'why',
    age:234,
    friends :{
        name:'hello',
        age:13
    }
}
const info = Object.assign({},obj);
console.log(info);
obj.friends.name='luohao'
console.log(info);
```

怎么样深拷贝 

```JS
const info = JSON.parse(JSON.stringify(obj));
```

深拷贝不会造成上面的情况 ， 就是对象里面的对象不会拷贝他的引用  而是改变了引用的地址 ， 形成了一个新的对象

### 组件

vite更新不好需要手动刷新 ， 还是有一些问题

#### v-model

双向绑定 ， 本质是一种语法糖

``` js
 v-model can only be used on <input>, <textarea> and <select> <radio>  <label>
```

背后两个操作 ， 绑定一个：value   和 监听事件 ，  不断的去修改  调用修改的方法 

背后其实更复杂的。 

radio  本身是互斥的   

##### 修饰符

lazy  number  trim 去除 空格  

### 组件化开发 

#### vue的组件化 

1. 注册  

```js
  app.component('app-a',{
          template : '#app-a'
        })
```

全局注册的组件在所有的组件中都可以使用

组件的data写在组件中  methods

2. 局部注册

在组件中的components：  {} 对象中写组件的名字 可以es6简写 。 

### webpack

1. 配置文件

![image-20220107223432705](Vue3.assets/image-20220107223432705-16415660743272.png)

2. loader

用于解析模块

-d 在加载的时候 才运行 这个loader

在webpack.config.js 配置文件中的moudel 中的rules 来给loader配置相关  ，    说一下遇到什么文件的时候启动loader

less-loader =》 css-loader =》 style-loader 的文件 

3. postcss

插件autoprefix  自动加上前缀的插件 

给css 加上浏览器的前缀 。   

配置方案 : 

![image-20220107224212852](Vue3.assets/image-20220107224212852-16415665336533.png)

当使用到postcss-loader  的时候 会使用到插件 。 

4. postcss -prest -env

预设的环境    把现在的css 转成 浏览器认识的css

### webpack打包 

1. file loader 打包 

对文件的图片资源进行打包 

图片的名称不好看   如果不配置的话会随机的名称hash值防止重复

文件命名的规则可以配置  

![image-20220107231043953](Vue3.assets/image-20220107231043953-16415682448114.png)

使用的是palcehoders

同样是在options里面配置的是

![image-20220107231521688](Vue3.assets/image-20220107231521688-16415685224045.png)

outpath 设置  文件打包的出口

2. url -loader

和file -loader 类似 ，  

但是可以将**小文件** 可以转成base64的url

大文件就不要转了

![image-20220107232041436](Vue3.assets/image-20220107232041436-16415688426136.png)

限制图片的大小

### babel

![image-20220107234330118](Vue3.assets/image-20220107234330118-16415702112727.png)

到底是什么东西  搞半天 ， 是工具链， 语法转换源代码转换的作用

1. 如何使用？

安装预设preset   转换的内容比较多这个时候我们要配置到底什么东西要转成什么东西 

2.  底层原理 



![image-20220107234821549](Vue3.assets/image-20220107234821549-16415705026868.png)

源代码比较优秀可以看一下 。 

过程是 ：  原生的代码 ， 解析  ，转换    ， 代码生成 

目标的源代码  

![image-20220107234943089](Vue3.assets/image-20220107234943089-16415705843269.png)

和浏览器v8 渲染dom  差不多 ，  

3. 配置

![image-20220107235226729](Vue3.assets/image-20220107235226729-164157074761010.png)

配置预设

### Devserve

#### webpack 的watch

在build 后面-- watch  就配置成功了 。

 导出的配置watch ： true      在moudle.exprot

很少使用  没有自动刷新  ，自动刷新是live  reloading

#### webpack -dev -server

####   ![image-20220108001751627](Vue3.assets/image-20220108001751627-164157227249011.png)

#### contentBase 拷贝资源加载



#### 模块的热替换

在程序运行中  **替换删除添加**  而无需重新去刷新整个页面 

模块当成整体 ，  一个模块修改  就刷新浏览器  

  ![image-20220108002003497](Vue3.assets/image-20220108002003497-164157240407212.png)

 

vue-loader 

框架中已经有了自己的方案 。

### vue cli 和vite

脚手架，内置了webpack相关的配置我们不需要从0开始配置webpack   ，  可以通过cli来选择项目的配置

### ref

解构之后没有响应式

###  FILE过渡技术

即FLIP（First, Last, Invert, Play）

作用：FLIP技术可以以一种高性能的方式动态的改变css（比如，height、width、float、绝对定位、Flexbox和Grid等）。

#### 为什么好？

为了性能 ，平常中使用transform和opacity 是高性能

FiLE模拟布局 . 

####  **Animations API**      

在一些浏览器是不支持的 

时序模型 和 动画模型来实现的。

### @keyframes

通过 @keyframes 规则，您能够创建动画。

一套css 变成另外一套的css样式

通过百分比的形式表示时间，from to 也行

#### translate3d

在x y z 方向上移动的位置 。 

**perspective**   表示是观察者到z平面距离 



### 组合api

生命周期 ， 

setup 替代了 之前的 beforecreate  和created 

#### privide 和inject   

共享数据和共享对象   使用readonly数据说明父组件给子组件共享的数据是不可以被子组件  **修改的**

mixin 的缺陷， 命名的冲突，    

组合api解决这些问题 

#### hooks

将setup中的函数全部放在hook中js文件  命名的规则是usexxx.js 

在使用的时候就要在vue文件中导入(import usexx.js from  hooks)usecount 的函数 ，可以进行解构  。

也是可以在return 中直接... usecount()  解构 ， 直接返回 ，

#### 封装hooks

exprot default function （title='xxx'）

修改docoment 里面的title

  使用watch 去监听修改的新值可以获取新值将新值赋给titleref.value 的值 。

wacth是惰性的 ，只有发生改变才会进行操作watch 里面的回调 ，   也可以在watch 的实参里面传入immediate：true 保证他可以立即的执行回调 

#### jsx的使用

render（）{return <div>dddd</div>}

vue确实是支持的jsx   安装babael 的插件 ，jsx 的插件就支持

方法写在render（）函数中

组件也可以使用这种方式写 ， helloworld组件 ， 利用插槽的话，{{对象 this.$slots=.default==}}   在写hooks 的时候可以用jsx 来编写

#### 

#### vue3高级语法的补充

自定义组件，v-show  v-for -v-model  

当我们需要对**dom元素进行底层操作**的时候才自定义

通过directives选项，组件中的这个选项是**局部**的指令

自定义**全局**指令app的directive方法就是全部的指令

实践：

1. 

导入ref  onmount 生命周期

```
setup(){
const input =ref(null)
onmount（（）=》{
input.value.focous();)
}
return {
input 
}
}
```

把这个focus放在了挂载的函数上面

2. 在input标签上面放v-focus的属性

然后在export default { directives 定义选项   focus：{

mounted（el，bindings，vonode， prenode ）{logxxxx操作

el.focus // focus 操作 }

我们这里只需要是前面的el

3. 全局

app.directives(''focus',{

mounted(el,bindings,vnode, prevonode 

log.....     换行      el.focus  //   对el的相关操作     })

#### 指令的生命周期

created ： 在绑定元素属性和事件监听器被应用之前调用

beforemounted ; 当指令第一次被绑定并且挂载父组件之前被调用

mounted  ，   beforeupdate  update  ， unmount  ...

这些生命周期写在自定义的组件里面 。 。

el就是标签的整体，  bindings 放的是修饰符和自定义组件的属性       **这两个参数是常用的**

#### vue插件

对象类型和函数类型  

install函数  对象的类型 

添加全局的方法或者属性  添加全局资源指令过滤器过渡

全局mixin  添加一些组件的选项 

 一个库提供自己的api   

install(app){app.config.globalpropeoties.$name='codewhy'}

函数： 

export default function （app）{log 。。。。 app}

#### 渲染器的实现

通过h函数来创建两个个vnode，通过判断两个vnode 的长度， 通过patch 函数去做移除操作 。

#### 响应式的思想

先收集响应式， 然后在收集里面去运行这个响应式

往每个依赖加上一个订阅，用集合去存放  保证不重复

dep的实现  **手动的通知 ，手动的收集**

addeffect（effect）{ 副作用的函数 this.suscribers.add(effect);

notify（）{通知this.suscribers.foreach(effect=》{effect（）);   拿到effect 之后执行

**自动的收集**

可以把dep.addeffect(effect)这个过程放在watcheffect 函数里面让他来自动的去收集依赖   在watcheffect函数中调用dep.depend() 自动把effect添加到set里面

effect如何获取？ 添加depend函数   

let actveeffect =null ；    把effect 赋给activeeffect  之后去调用dep.depend()   然后把activeeffect 滞空 

#### vue-router

vue的官方路由， vue.js核心深度继承

需要安装

```js
import { createRouter, createWebHistory, createWebHashHistory } from 'vue-router'
```

两种路由可以选择

内置的组件routerlink ：    需要传参数  to属性   repalce 属性默认情况下是push形式 ， 如果标签有repalce属性那不可以返回   	

映射关系：  放在一个名字叫做routes的对象里面 一个路径对应一个组件

```js
const routes = [
  { 
    path: "/", 
    redirect: "/home" 
  },
```

重定向：  访问默认的路径的时候   直接重定向直接跳到path

active-class：点击routerlink 标签之后 会默认自动加上一个class名字   active-class 属性可以修改他

 














































​                 

