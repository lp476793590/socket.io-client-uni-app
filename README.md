uniapp上使用的socket.io-client

使用方法：和socket.io-client 一样

解决了socket.io 在Android APP 上无法使用的问题

原socket.io-client无法使用是XMLHttpRequst、WebSocket无法识别，不清楚是不是打包后把引用包搞丢了。。。。

在原socket.io-client中的engin.io-client模块做了部分修改：
1，握手强制使用websocket协议
2，websocket连接、发送数据等使用uniapp内置websocket代替

NPM下载:
 npm i socket.io-client-uni-app

import io from 'socket.io-client-uni-app'


		this.socketio = io('wss://***.****.com');
		// 连接成功
		this.socketio.on('connect', () => {
			console.log('连接成功');
			uni.showToast({
				title:'连接成功'
			})
		});
		// 正在连接
		this.socketio.on('connecting', d => {
			console.log('正在连接', d);
		});
		// 连接错误
		this.socketio.on('connect_error', d => {
			console.log('连接失败', d);
		});
		// 连接超时
		this.socketio.on('connect_timeout', d => {
			console.log('连接超时', d);
		});
		// 断开连接
		this.socketio.on('disconnect', reason => {
			console.log('断开连接', reason);
		});
		// 重新连接
		this.socketio.on('reconnect', attemptNumber => {
			console.log('成功重连', attemptNumber);
		});
		// 连接失败
		this.socketio.on('reconnect_failed', () => {
			console.log('重连失败');
		});
		// 尝试重新连接
		this.socketio.on('reconnect_attempt', () => {
			console.log('尝试重新重连');
		});
		// 错误发生，并且无法被其他事件类型所处理
		this.socketio.on('error', err => {
			console.log('错误发生，并且无法被其他事件类型所处理', err);
		});
