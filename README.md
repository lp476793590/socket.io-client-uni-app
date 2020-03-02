uniapp上使用的socket.io-client

使用方法：和socket.io-client 一样

解决了socket.io 在Android APP 上无法使用的问题

原socket.io-client无法使用是XMLHttpRequst、WebSocket无法识别，不清楚是不是打包后把引用包搞丢了。。。。

在原socket.io-client中的engin.io-client模块做了部分修改：
1，握手强制使用websocket协议
2，websocket连接、发送数据等使用uniapp内置websocket代替
