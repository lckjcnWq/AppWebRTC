# 1 AppWebRTC--应用端

Yet another AppRTC demo which split from [njovy/AppRTCDemo](https://github.com/njovy/AppRTCDemo) 😱
AppWebRTC     -------基于webrtc-m85版本，可支持本地调试c++,不可用于正式版本

[AndroidStudio集成webrtc-c++进行单步调试](https://webrtc.mthli.com/basic/webrtc-breakpoint/)

# 2 AppRTC--服务搭建
搭建来源《WebRTC Native开发实战》
我这边测试的环境是ubuntu
## 2.1 ubuntu服务器防火墙需要配置开放的端口如下：
●　TCP 8080用于Signal Server的HTTP服务。<br>
sudo ufw allow 8080/tcp<br>
●　TCP 8089用于Signal Server的WebSocket服务。<br>
sudo ufw allow 8089/tcp<br>
●　TCP 3033用于ICE Server。<br>
sudo ufw allow 3033/tcp<br>
●　TCP 3478和UDP 3478用于TURN Server供客户端获取公网IP地址。<br>
sudo ufw allow 3478<br>
●　UDP 59000-65000用于TURN Server实现媒体数据中转。<br>
sudo ufw allow 59000:65000/udp<br>

## 2.2 服务器防火墙需要配置开放的端口如下：
macos : docker run -d --rm -p 8080:8080 -p 8089:8089 -p 3033:3033 -p 3478:3478 -p 3478:3478/udp -p 59000-65000:59000-65000/udp -e PUBLIC_IP=<服务器IP地址> -it piasy/apprtc-server <br>

linux/ubuntu/centos : docker run -d --rm --net=host -e PUBLIC_IP=<服务器IP地址>  -it piasy/apprtc-server

# 3 应用端App端设置使用
在设置中Room server URL中输入 http://<服务器IP地址>:8080 <br>
点击右上角的Loopback按钮，即可开始自推自收测试

