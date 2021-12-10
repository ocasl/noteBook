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

#### 对组件中props 的限制  指定属性的默认值

1. props 是组件的属性 我们可以对他进行限制 提高代码的质量就像 ts一样 

组件名.propTypes= {属性:propTypes.string.isRequired  ....}

2. 指定属性的默认值 

Person.defaultProps{  sex:"nan "  ,age:1}// 默认是男的1岁

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

```java
saveFormData = (dataType)=>{
   return (event)=>{
      //  return之后收到是什么咯
      this.setState({[dataType]:event.target.value})
   }
}
```

没有使用：

```javascript
saveFormData = (dataType,event)=>{
   this.setState({[dataType]:event.target.value})
}
```

将数组写进函数的 参数中  

#### 生命周期

render函数开始 挂载

mount 挂载   unmount  卸载  

componentDidMount      出生了  一般做初始化的工作

componentWillMount  交代后事   做一些收尾的事情

生命周期函数钩子    reacat 会在特定的时间会调用一些函数

钩子是不受代码的写的顺序影响的。

1.  正常更新 : shouldComponentUpdate   问是否需要更新， 写了需要要有布尔值  不写默认是放行的 。之后需要通过componentwillupdate     在将要更细前  

2. 强制更新  ： 不对状态做出任何的修改 ，forceUpdate  强制更新  不需要走shouldComponent Update



componentWillreviceProps 第一次不算 第二次更新才算  

  

在最新的钩子里面需要加一个unsafe  

componentWillmount    recevice    update   这三个将来弃用

过时的生命周期带来不安全的编码时间   进行异步的编码

被误解和滥用，如果异步渲染出来之后可能会有bug 所以这个是预估以后版本有问题 。  很少使用钩子  。。。

#### 新的钩子和旧的钩子有什么区别啊

废除三个钩子

新推出来的钩子两个不常用

1. getDerivedStateFromProps（props，state）两个参数

得到一个派生的状态罕见的用例 

state值在任何时候都取决于props    横跨在挂载的地方

2. getSnapshotBeforeUpdate

在更新之前获取快照  值必须要返回快照或者null

perprops和perstate   之前的props和之前的状态 

再提交dom之前调用  返回的任何参数值传给 componentDidUpdate    快照之前获取信息将给这个钩子

处于render和Didupdate之前

```javascript
componentDidUpdate(preProps,preState,snapshotValue)
```

更新前获取快照

#### React 脚手架

组件文件夹中用index.jsx    

css 可以使用样式模块化 

rcc 可以快速生成模板  ，是不用手巧的  rcc 是模板

#### React  ajax  发生网络请求 

```javascript
getStudentData = ()=>{    axios.get('http://localhost:3000/api1/students').then(
  response => {console.log('成功了',response.data);},
      error => {console.log('失败了',error);}
    )
  }
```

node和express写的代理服务器   

**跨域**

3000发5000  跨域  发了 但是没有回来   

##### 如何配置代理

配置多个代理

setupProxy.js 文件里面  

```javascript
const proxy = require('http-proxy-middleware')
然后我们配置两个服务器
module.exports = function(app){
  app.use(
   proxy('/api1',{ *//遇见/api1前缀的请求，就会触发该代理配置*
      target:'http://localhost:5000', *//请求转发给谁*
     changeOrigin:true,*//控制服务器收到的请求头中Host的值*
     pathRewrite:{'^/api1':''} *//重写请求路径(必须)*
    }),
    proxy('/api2',{
      target:'http://localhost:5001',
      changeOrigin:true,
      pathRewrite:{'^/api2':''}
    }),
  )
}
```

#### 消息订阅和发布

##### 实现兄弟组件间的通讯

```javascript
this.token=PubSub.subscribe('atguigu',(_,stateObj)=>{
      this.setState(stateObj)
      })
```

参数三个   要发送的消息，回调函数  

订阅方就是发送消息的人，

在这个组件卸载前需要取消订阅   

```javascript
componentWillUnmount(){
    PubSub.unsubuscribe(this.token)
  }
```



订阅报纸：交钱说好地址订阅哪种报纸

订阅消息： 消息名

发布机制 pubsubJs    发布订阅js

yarn add pubsub.js 

app不应该有状态 放在list里面谁需要放在谁哪里

任意组件的沟通都行， 消息订阅发布技术 

#### axios配合订阅和发布  得到信息 。 

例子等于是一个获取搜索信息的请求 

```javascript
*const {keyWordElement:{value:keyWord}} = this*
```

连续的一个结构赋值

```javascript
axios.get(`/api/search/users2?q=${keyWord}`).then(response=>{
   //  PubSub.publish('尚硅谷',{isLoading:false,users:response.data.items})
},error=>{
    pubsub.publish('巴拉巴拉',isloading:false,err:error.message))
}
}
```



#### fetch 发送请求

xhr    =》 axios   都是对xhr 的封装

fetch  没有利用到xhr                    直接可以在浏览器使用

1. 第一步联系服务器，数据没有取出来
2. response.json里面是promise 
3. 老版本不支持fetch   不用下载不用引用 浏览器原生的

axios 为主 : : : : :: :  

##### fetch 优化

```javascript
	try {
			const response=await fetch(`/api1/search/users?q=${keyWord}`)
			const data=await response.json()
			console.log(data);
			PubSub.publish('atguigu',{isLoading:false,users:data.items})
		}catch(error){
			console.log('请求出错',error)
			PubSub.publish('atguigu',{isLoading:false,err:error.message})
		}
```



#### Spa应用的理解    

单页面应用  ， 整个应用只有一个完整的页面，点击链接指挥做页面的局部更新 数据需要哦通过ajax请求获取，在前端异步展现

#### 路由  

kv映射的关系  key是路径，value 是方法或者是组件 

后端路由和前端路由

1.  value 是方法函数 ， ， ， ，node接受到一个请求之后后端路由根据路径去调用函数来处理请求 返回数据   

router.get(path , fn(req,res))

2.  value  是组件  浏览器的path变了页面编程相应的组件

#### 路由到底怎么配置

1. 其他不说必须先安装npm i react-router-dom -S

一般用的history模式

### [React](https://so.csdn.net/so/search?from=pc_blog_highlight&q=React) 路由匹配规则

1. excat 是精确匹配 ，
2. switch 包住。



#### 前端路由的原理 

1. history

bom 中的history   ， 

浏览器的记录是栈的数据结构    h5 推出的。   

push  是入栈 ， ，  ，

前进和后退  ，   replace  是栈顶的被换成 replace 的记录 。 

2.  hash  

多了一个＃ ， 

#### 路由的基本使用 

1. react router 理解  dom     我们选择web 的

有三种 web  native  any    官方维护的router库 ， ，

yarn add  react-router-dom   **安装路由**   

可以实现      页面不  刷新的

原生中靠<a> 标签实现页面条状 ，  在react 中我们靠路由连接跳转页面，

不应在路由器外面写link ，把整个app用路由器包住在index.js包住

路由器分两种   browsrouter  和hash router

#### 路由组件和和一般组件

路由组件放在pages    一般组件放在components  

路由组件需要靠路由匹配才能渲染

区别：路由组件能收到**路由器**给他的三个东西，history，location，match  

#### Navlink 的使用

想要高亮就要使用这个路由链接，

为什么？link 加active   ，   在navlink里面有actveclassName 的样式属性名我们可以给他取名字然后区给他加样式。

bootstrap 的权限有点高， 所有如果要自定义我们要用！import

#### 封装navlink组件

navlink里面需要批量的传参数

1.  在navlink 里面利用{...this.props}

2. 标签体内容是一个标签属性  ，  在标签属性就是children

this.props.children    

#### switch 的使用 

怎么提高路由的匹配效率 

我们用switch 包住路由  

#### 使用二次路由掉了样式

public 里面是devserver    locallhost ：3000     是这个路径

index.html 是兜底的人，如果服务器在public 找不到资源最终会用index.html 兜底。

解决办法： 

1. herf 写%PUBLIC_URL%    react 才认识  
2. herf 前面点去掉
3. 使用hash路由  # 后面不看的    少用 

#### 重定向

写在全部的路由最下方   < reactve



#### 引入路由

```javascript
<BrowserRouter>
				<Switch>
					<Route path="/login" component={Login}></Route>
					<Route path="/admin" component={admin}></Route>
				</Switch>
			</BrowserRouter>
```

#### 根据id 获取商品 

```javascript
export const reqCategorys = (parentId: string): Promise<ResponseValue<any>> =>    //  promise 是一个respsonse  任意类型的。
	ajax<ResponseValue<any>>(`/api/category/list/${parentId}`);
```

##### ajax 封装 带上antd 组件  message 效果 。

需要axios 和antd 里面的message  自行引入把。

默认暴露ajax 方法泛型  

要参数 ： url ，data  得到的数据， 成一个对象  ， method 方法请求方法默认是Get   

```javascript
method: ReqMethodEnum = ReqMethodEnum.GET
```

在 ts文件里面定义了一个枚举类型

```javascript
export enum ReqMethodEnum {
	GET = 'GET',
	POST = 'POST',
	PUT = 'PUT',
	DELETE = 'DELETE',
}
```

封装的ajax 本身是一个promise 他有两种i结果。  reject 和reslove  结果 。

因为请求的方法有点多 ，所以reject 不能使用因为一个promise 只能有一个结果。   我们这里用cath代替。

promise = aixos.get(url,axosrequest config : 是一个对象 里面你可以存放请求头 以及是数据的data 参数 )















