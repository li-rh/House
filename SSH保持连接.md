---
share: true
---
## 问题描述
在某些情况下，远程连接的时候，如果 ssh 客户端（如： [[MobaXterm|MobaXterm]]）没有收到指令，shh 客户端会自动和服务端断开联系
## 解决方案
修改远程服务端的 `/etc/ssh/sshd_config` 文件
```bash
sudo cat <<eof >> /etc/ssh/sshd_config
ClientAliveCountMax 3    #默认重连3次
ClientAliveInterval 30   #30s重连一次，给客户端发送keepalive信号
eof
```
重启服务端 ssh 服务
```bash
service sshd restart
```
