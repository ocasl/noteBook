### https是什么？

是  ：  超文本传输协议

 在http后面加上tls/lls 进行加密  通信不容易被拦截和攻击

​			ssl是**tls**是前身      他们再tcp 中是**传输层**

#### 对称密文

约定用倒念的方式    只有共同的一套规则就是公钥    发送数据用公钥来解密

#### 非对称

 	私钥和密钥

也就是**公钥加密**  

双方利用自己的私钥和公钥混合 形成一段数据发送 交换 ，之后他们用私钥区解密这段混合的数据    做到的在发送的时候信息不被暴露因为这个混合的数据是需要各自的私钥才能解的

#### 证书

服务器安装ssl 证书之后就可以通过https来访问网站 了默认端口变成443

握手过程：**非常重要的协议**

1.  **client hello**： 第一随机树被客户端发送给服务端，   发送的数据有tls版本和加密套件，第一随机数  ，

2. **serverhello** ：发送之后  服务器来确认一下你发的数据 返回一个 第二随机数   
3. **serverhellodone**：服务端之后还会将证书和公钥发送给客户端 发送完毕之后告知客户端
4. 客户端通过服务端发送的那些数据生成一个**第三随机数预主密钥**（被公钥加密了），用服务端刚刚发送的**公钥**加密之后再发出去  **clentKeycexchange**    准备切换密码 **changecipherspec** 自己将与主密钥给切换了 生成一个**切换后的密码** 
5. 收到了预主密钥的服务端，利用这个第一随机数，第二随机数 ，和预主密钥去计算出会话密钥  发送返回给客户端  两者都拿到了**会话密钥**

得到的会话密钥只限于当前的会话 。。 

### http简介

1. 请求报文

```js
行   POST /s?ie=utf-8 HTTP/1.1 

头   Host: atguigu.com
​    Cookie: name=guigu
​    Content-type: application/x-www-form-urlencoded
​    User-Agent: chrome 83
空行
体   username=admin&password=admin
```

2. 响应报文

```js
行   HTTP/1.1 200 OK

头   Content-Type: text/html;charset=utf-8
​    Content-length: 2048
​    Content-encoding: gzip
空行  
体   <html>
​      <head>
​      </head>
​      <body>
​        <h1>尚硅谷</h1>
​      </body>
​    </html>
```

3. 在控制台如何查看

点网络  - >  header  请求头

​              ==> response  事响应体 返回的是html

#### 跨域

通过xhr对象去自定义响应头    

```js
app.all('server',(request,response)=>{
    response.setHeader('Access-Control-Allow-Origin', '*'); 
    response.setHeader('Access-Control-Allow-Headers', '*');
}
})
```

#### ajax  的请求状态

xhr.readstate = 1 / 2 / 3 / 4       0 ： 没有打开，  1： 打开了没发 ，2：发了部分处理 3：大部分处理完了 4. 完全处理完毕 已经有了响应

#### ajax 的流程

```js
var xhr = new XMLHttpRequest();
xhr.open('GET', '/api/')
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlenc')
xhr.send(body);
xhr.onreadystatechange = function() {
    if(xhr.readyState == 4 && xhr.status == 200){
        console.log('成功了 ');
        // 可以拿到服务端的响应体
        var text =xhr.responseText
        console.log(text);
    }
}
```

#### IE浏览器有缓存问题

解决：  参数后面**加时间戳**

```js
xhr.open('GET', '/api?t='+Date.now())
```

#### get 和post 区别

1. GET把参数包含在**URL**中，POST通过**request body**传递参数

注意：GET和POST本质上就是TCP链接，并无差别   ， 其实在get： 中写 request body 和  post： 中写url 也是可以互相实现的

2. GET产生一个TCP数据包；POST产生两个TCP数据包。

get 将http header 和data 一起发送到服务端

post  将http header 先发  然后再发 data  给服务端  （Firefox就只发送一次）

#### xhr 的异常情况

两个xhr回调的api 

1. 超时了 

ontimeout     

2. 网路异常

onerror        

```js
xhr.onerror = function() {
    console.log('出错了啦。 ');
}
```

​          

3. 取消请求 （中断）

在xhr.readstate 没有到4的之前

abort            使用这个api 来取消请求

**应用：**解决反复的去请求的问题

```js
var xhr = new XMLHttpRequest();
xhr.open('GET', '/api?t='+Date.now())
xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlenc')
xhr.send(body); //下面设置一个布尔值来表示请求的状态

let isSending  =true;
xhr.onreadystatechange = function() {
    if(xhr.readyState == 4 && xhr.status == 200){
        console.log('成功了 ');

        isSending=false;
    }
}
```

### Axios

1. axios.get(url,data,params)

```js
axios.default.baseURL = "http://localhost";
btn.addEventListener("click",()=>{
axios.get('/axios/server',{
    // 参数
    params: {id:100 ,name :'lll'},
    // 请求头信息
headers: {
    name:'atguigu',age:20
} 
}).then(value=>{
    console.log(value);
})
})
```

2. axios （）

把请求的方法  请求头 ，请求体参数 请求成功的回调都写在这里面

method          url       headers         data （参数）  

###      Fetch  

window 自带的 不需要安装    拿来就可以使用          简单使用的例子

```js
btn.onclick = function (){
    fetch('url',{
        method: 'GET',
        headers: {name:'ddd'},
        body: 'username=1213&password=13212'
    }).then((response)=>{
        return response.json();
    }).then((response)=>{
        console.log(response);
    })
}
```

### 解决跨域问题

1. **概念**：协议、域名、端口号            三个必须要相同   

2. **为什么要这样**?    1. 保证用户的信息安全  

3. **跨域会造成**：如果跨域了就不可以共享cookie 不能获取dom （渲染失败  ）   ajax 发送不了不符合同源的 请求 （但是谷歌已经可以发了 ，但是在服务器端返回的头中还是会被浏览器发现不符合同源  ） 
4. **解决方案**

jsonp   程序员想出来的**scirpt 标签支持跨域**的

cors   ：  设置响应报文 （推荐）

```js
//设置允许跨域的域名，*代表允许任意域名跨域
response.header( 'Access-Control-Allow-Origin' , '*');
//跨域允许的请求方式
response.header("Access-Control-Allow-Methods", ’);
response.setHeader("Access-Control-Allow-Headers", '*');
```

使用nginx做转发 (推荐)



