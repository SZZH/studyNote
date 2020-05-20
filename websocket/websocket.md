## WebSocket

### 概念

- websocket是一种网络通信协议，目前常用的通信协议有http和websocket
- websocket支持服务器推送，解决了http协议只能单向通信的缺点

### 特点

- websocket只需一次握手，就可建立持久连接
- 单个tcp连接上可以进行全双工通信
- 有状态的通信协议，建立连接后会保持连接状态

### 阮一峰详解

[点这里](https://www.ruanyifeng.com/blog/2017/05/websocket.html)

### 举例

当我想知道当天的天气是，若基于http协议，则得向服务器发送一个请求，然后服务器返回查询的结果。

那么我想在每天早上定时给客户端发送一个天气信息呢？

这个时候http的不足就展现出来了

websocket应运而生，他可以主动向客户端发送信息

### 客户端api

- 创建websocket实例 ：`let ws = new WebSocket('ws/wss://服务器地址')`
- 连接状态：`ws.readyState`
  - 共四种状态：
    - 0：表示正在连接，connecting
    - 1：表示连接成功，可以通信，open
    - 2：表示正在关闭，closing
    - 3：表示已经关闭或打开连接失败，closed
  - 连接成功的回调： `ws.onopen = () => {}`
  - 连接关闭的回调：`ws.onclose = () => {}`
  - 收到服务器数据后的回调函数：`ws.onmessage = (event) => { const data = event.data; }`
  - 向服务器发送数据：`ws.send()`
  - 剩余未发送的二进制数据长度：`ws.bufferedAmount`，可以用来判断发送是否结束
  - 报错回调：`ws.onerror = function(event){}`