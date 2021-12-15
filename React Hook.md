### Hook？

# State Hook

1. 它可以让你在不编写 class 的情况下使用 state 以及其他的 React 特性

2. Hook 还提供了一种更强大的方式来组合：**props， state，context，refs 以及生命周期**

3. Hook 是一个特殊的函数  

```javascript
import React, { useState } from 'react';

function Example() {
  // 声明一个叫 "count" 的 state 变量
  const [count, setCount] = useState(0); 
```

1. 唯一的参数就是初始 state
2. 定义一个 “state 变量”。我们的变量叫 `count`

3. 返回值 当前 state 以及更新 state 的函数

4. setCount` 来更新当前的 `count

### state操作

1. 读取：直接用 `count` { count  }  在class中需要this.state.count

2. 更新： 函数：

   ```javascript
    <button onClick={() => setCount(count + 1)}> 
   ```

   class ：

   ```javascript
    <button onClick={() => this.setState({ count: this.state.count + 1 })}>
   ```

#### 总结：

```javascript
   const [fruit, setFruit] = useState('banana');
```

**数组解构**，创建了fruit 和setFruit 

```javascript
function handleOrangeClick() {
    // 和 this.setState({ fruit: 'orange' }) 类似
    setFruit('orange');
  }
```

**不必**使用多个 state 变量  函数中更新是合并的  state 可以很好的存储对象和数组

# Effect Hook

1. *Effect Hook* 可以让你在函数组件中执行副作用操作

2. `useEffect` Hook 看做 `componentDidMount`，`componentDidUpdate` 和 `componentWillUnmount` 这三个函数的组合
3. 它在第一次渲染之后*和*每次更新之后都会执行

#### 副作用？

数据获取，设置订阅以及手动更改 React 组件中的 DOM 都属于副作用

#### 副作用实例

1. class  :  副作用操作放到 `componentDidMount` 和     `componentDidUpdate` 函数中

