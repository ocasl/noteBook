### Object.keys

获取对象的key 的集合  

### Array.prototype.forEach

1. 数组的遍历方法。

```javascript
const arr =[1,1,3,4,5,6,7,8,9,10]
   arr.forEach((item,index,arr) => {
       console.log(item,index)
   })      
```

item是每个遍历出来的元素  index 是索引 ，arr需要遍历的数组

2. map :  操作遍历出来的数组

```
const arr =[1,1,3,4,5,6,7,8,9,10]
   arr.map((item,index,arr) => 2*item
   consle.log(arr)
   })
```

3. filter  :过滤
4. some :如果有一个真就返回

5. every  ： 所有为真才返回
6. reduce    (pre, next)         第一个参数是回调函数  pre为上次return 的值 next 为数组本次遍历的项  

 

### 函数参数的length

在第一个具有默认参数之前的参数 

剩余参数是不算长度的 。   

```javascript
console.log(123['toString'].length + 123)
```

### h5加入的requestAnimationFrame

专门为动画提供的 API
