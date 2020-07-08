# 腾讯云服务器自动断开连接的解决办法

## 1. 找到sshd_config配置文件

```vi /etc/ssh/sshd_config
vi /etc/ssh/sshd_config
```

使用vi打开进行编辑，在文件中找到以下配置项：

```
# ClientAliveInterval 0
# ClientAliveCountMax 3
```

去掉注释，改为：

```
ClientAliveInterval 30
ClientAliveCountMax 86400
```

这两行的意思是：

> 1. 服务端每隔多少秒向客户端发送一个心跳数据
> 2. 客户端多少次没有相应，服务器自动断掉连接

> + 1、服务端每隔多少秒向客户端发送一个心跳数据
> + 2、客户端多少次没有相应，服务器自动断掉连接



## 2. 重启sshd服务

```
systemctl restart sshd.service
```



![区块列表 list](d:\Users\zx\Desktop\批注 2020-07-08 085832.png)



![md图片](d:\Users\zx\Desktop\批注 2020-07-08 090040.png)





