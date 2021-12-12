### 基本类型的声明

1. 在ts会给你传错 提前写好数据类型

2. **any**  可以赋给别人也不报错  

3. **unkonw** 类型安全的any  不可以赋给其他变量

4. 变量**as**  类型       <类型>  变量
5. **void** 是空值   没有返回值  **undefined**  和**nul**l 都行 不写也行 ，  **|** 是或者的意思 

6. **never** 是永远不会返回结果    never 就是什么都没有 用于报错  ，报错了就没有返回值了 程序结束 
7. object  表示是一个对象    {v：k}   限制object 的类型  

在属性后面加一个小问号？ 说明可有可无。

【propName：string】：string      限制字符串类型的变量 

8. 数组            类型【】            Array<类型>
9. tuple 元组  ， 固定长度的数组   let h ：【string，number】；   限制变量的个数和类型   固定长度的数组
10. enum   枚举  
11. &表示同时  ， 一个名字有两个对象 
12. type 别名    let k ： mytype     type mytype =1|2|3|4|5

### 面向对象

类中有属性和方法    参数也要有参数的类型声明

get set 方法可以设置属性的值 

### 泛型

不指定泛型ts可以自动对类型进行推断 

 指定泛型就已经确定了类型

泛型可以同时指定多个。  。 

在类型不明确的时候给我们一个变量用来指明是什么类型









### Ajax  

发请求不刷新页面     

  用就加载不用就不加载

#### xml  

超文本标记语言被设计来传输 和存储数据

#### json 

被json 代替了 现在 是使用json来发送请求

#### 优缺点

优点：不用刷新就可以通信   允许你根据用户的时间来更新部分页面的内容

缺点：没有浏览的历史， 存在cors 跨域  seo 不友好  对爬虫不友好爬不到数据

#### http协议

**请求报文**： 行 （请求方式，字符集，协议/1.1），头 host cookie content-type user agent   ，体  参数 

**响应报文**  行： 协议 状态码  状态值  contnet type  conent-length  content encoding  ：gazip    ，  空行   ， 体  返回的html  标签  

headers 是头的意思    response header    request header  请求头 。 view parsed 是请求行  。 view parsesd 是原始的报文或者是请求头 

response 

#### 服务端express 端框架

利用express写服务器后端

```javascript

const express = require('express');

const app = express();

app.get('/server', function (req, res) {
    res.setHeader('Access-Control-Allow-Origin', '*');
    res.send('Hello World')
})

app.listen(8000,()=>{
    console.log('服务器启动了，8000端口监听中')
})
```

利用本机做服务器构建服务器发送服务器端的信息

#### 发送端利用ajax

```javascript
 const xhr = new XMLHttpRequest(); 

       xhr.open('GET','http://127.0.0.1:8000/server')  // open可以换成是all  可以服务器可以接受任何的请求
       xhr.setRequestHeader('Accept',   'application/dasdasdasdasda')  //  设置响应头

             // 设置请求头
             xhr.send('a=100&b=200&c=300')
             xhr.onreadystatechange = function() {
                 // 当4的时候就返回全部的数据
                 if(xhr.readyState === 4){ 
                     if(xhr.status >= 200 && xhr.status<300){
                         // 相应行
                        console.log(xhr.status)
                        console.log(xhr.statusText)
                        console.log(xhr.getAllResponseHeaders())
                        console.log(xhr.response)
                        result.innnerHTML = xhr.response; 
                     }else{
                     }
                 }
             }
        }
        
```

xhr 上的方法可以设置响应体的数据类型  xhr.responseType='json'; 设置为json 的形式

#### nodemon 为了防止来回启动服务端

不用来回的启动服务端他会自动的重新启动   **这时启动方式不是node server.js  而是nodemon server.js  自动检测变化自动重启**

#### 解决 IE 缓存问题

如何去避免这个缓存造成的浏览器无法及时从服务器更新问题

在xhr请求方法中url 后面加上时间戳     参数后面加上时间戳

#### 请求超时提示

1. xhr.timeout = 2000;  设置超时 

```javascript
 xhr.ontimeout = function(){
                    alert('chaoshi ')
                }
```

2. 超时 之后的回调。

3. 网络异常的回调

```javascript
 xhr.onerror=function(){
                    alert('你的网不行啊')
                }
```

#### 取消请求 

abort 方法     

#### 避免用户瞎点重复发送请求占用服务器

1. 在点击事件之前声明一下标识变量 
2. 在点击事件内如果在发请求的话就取消掉该请求

```javascript
 *if*(isSending)xhr.abort();
```

3. 在点击事件函数之内 讲变量改为 true 代表已经发送请求

```javascript
let isSending = false;
```

4. 在readystate  ===4是的时候我们将这个状态改为false 

**readystate** 是   HTTP 就绪状态  从0到4讲 ，未初始化，已经建立了，已发送服务端在处理了 ，请求处理中（这里已经拿到了数据了），响应完成 

#### axios        vue 推荐的ajax 封装

配置baseurl	 是  http://127.0.0.1:8000  例子

url 参数 ： parms ：{对象 kv}              请求头： headers:{同对象}



#### 啥是同源策略 ，跨域

同源就是协议 域名端口号必须完全相同

违背同源就等于是跨域了 。

#### 如何解决跨域问题

1. jsonp解决  不是官方的是还得是程序员发现的，只支持get请求

我们在请求cdn 的时候 肯定是跨域了  但是为什么没有发生跨域  

因为scipt 标签本身就不存在跨域问题   在里面指定src

原理  : 返回的形式是一个函数的调用  而函数的实参就是我们想要服务器返回给我们的数据，这个函数需要在scipt提前声明 要不然找不到数据的存放位置

2. 设置cors  官方的跨越的资源共享。

添加cors 中间件  ，  app.user(cors({

origin :['http://localhost:3000','http://domain2.com']// 指定了允许的地址 

}))

服务端设置cors  一般前端操作不到 

在服务端设置响应头

```javascript
response.setHeader('Access-Control-Allow-Origin', '*');
```

设置所有的地址都可以实现跨域

3. 配置代理

安装http-proxy-middleware  库 

```javascript
app.use('/api',createProxyMiddleware({
    target:'http://localhost:5000',
    changeOrigin: true,
    pathRewrite:(path)=> path.replace(path)
}))                //  path 是RegExp
```



## fetch 

啥也不用导入直接用就完事  







# 新技术 graphQL

前端可以快速找到后端文档中的api .....很是方便。建议项目中可以使用这个技术



### 贪吃蛇的项目复习一下 

#### flex 布局

1. 行列 ，   dispaly flex  

2. 默认是按行的布局           主轴默认是x 轴  和主轴垂直的就是交叉轴

3. 改变主轴的布局方式  justify-content ： center  /space-between 两边对齐 / space-evenly  平分空间           **靠哪边对齐**  
4. 改变交叉轴的  用a'lign-items ：flex-end/center
5. 改变主轴方向  flex-direction :column

####  gird 布局

```javascript
#test{
display : grid;
grid-template-columns: 1fr  1fr  1fr ;   // 占用一行的空间 有几列就有几个数
column-gap:24px ; // 列之间的间距 
row-gap:24px  // 行间距
gap :24px  //  统一设置成一个间距 

align-content :end  ;  // 相对于父元素对齐方式 列的
justify-content: space-between;  // 两端对齐  
}
```

#### 

