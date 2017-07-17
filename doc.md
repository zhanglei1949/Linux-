# 服务器相关
## ssh
### ssh命令在操作多个多台服务器组成的集群的时候非常重要，可以提供安全，高效的访问通道。ssh服务器一般在22端口监听，ssh也可以建立到本地的连接。

### 从当前主机建立到${target ip address}的连接
```
ssh ${target ip address}
```
### 在分布式集群中，往往要求无密码ssh登录，可以用ssh-keygen来生成密钥，然后分发至目标节点，之后ssh登录无需输入密码
```
ssh-keygen
# use the default file name and empty for passhphrase
ssh-copy-id {username}@{target node}
```
### 可以通过修改hosts文件避免一直输入节点的ip地址。hosts文件位于 /etc/hosts,格式为
``` 
${ip address} hostname
```

#文本阅读编辑
## cat 
### 用于查看文件内容，会将文件内容输出到终端屏幕上。适用于内容较少的文件
```
cat ${filename}
# -n 以显示行号
cat -n ${filename}
```
## more
### 提供一页一页的显示方式，按空格键向下一页，Enter键向下一行，Q键退出
```
more ${filename}
```
## less
### 功能与more相似但更强大
## head
## tail

#文件（夹）操作

## 查找