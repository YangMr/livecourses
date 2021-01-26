# 第四节 通过Nodejs搭建自己的流媒体服务器实现直播-鉴权验证

## 4.1 为什么要对流媒体服务器进行鉴权验证?

如果我们对流媒体不进行鉴权验证,那如果用户知道了我们的服务器地址,就可以进行随意的推流,这种情况是我们非常不愿意看到的,这个会造成我们的直播内容混乱,没有安全性

## 4.2 实现Nodejs流媒体服务器鉴权验证

1. **加密后的 URL 形式:** 

```javascript
rtmp://hostname:port/appname/stream?sign=expires-HashValue 
http://hostname:port/appname/stream.flv?sign=expires-HashValue 
ws://hostname:port/appname/stream.flv?sign=expires-HashValue
```

	2. **原始推流或播放地址:**

```javascript
rtmp://192.168.0.10/live/stream
```

	3. **配置验证秘钥为**: 'nodemedia2017privatekey'，同时打开播放和发布的鉴权开关

```javascript
const config = {
		rtmp: {
				port: 1935,
				chunk_size: 60000,
				gop_cache: true,
				ping: 60,
				ping_timeout: 30
			},
			http: {
				port: 8000,
				allow_origin: '*'
			},
			auth: {
				play: true, //表示拉流的时候是开启鉴权验证 
				publish: true, //表示推流的时候开启鉴权验证 
				secret: 'nodemedia2017privatekey' ,
			} ,
	}
```



## 4.3

## 4.4