# Xray Vless

## 概述

用于在 Heroku 上部署 vless+websocket+tls，每次部署自动选择最新的 alpine linux 和 xray core。  
vless 相比 vmess 性能更加优秀，占用资源更少，运行更加稳定。

## 镜像

经测试本镜像占用内存资源较低，运行稳定。

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://dashboard.heroku.com/new?template=https://github.com/Tonkercke/Xrayvless)

## 注意

### 路径

`WebSocket` 路径(配置文件中的 `path` )为 `/gyfdqwaed` 。

### 端口

`端口` 为 `443` 。

### alterId

`alterId` 为 `0` 。

### UUID

`UUID` 默认为 `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` UUID需要自行更改。

'UUID' 可在 https://www.uuidgenerator.net/ 中獲取。

## 流量中转

可以使用cloudflare的workers来`中转流量`，配置为：  

addEventListener(  
&emsp;&emsp;"fetch",event => {  
&emsp;&emsp;&emsp;&emsp;let url=new URL(event.request.url);  
&emsp;&emsp;&emsp;&emsp;url.hostname="xx.herokuapp.com";//你的heroku域名    
&emsp;&emsp;&emsp;&emsp;let request=new Request(url,event.request);  
&emsp;&emsp;&emsp;&emsp;event. respondWith(  
&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;fetch(request)  
&emsp;&emsp;&emsp;&emsp;)  
&emsp;&emsp;}  
)  
