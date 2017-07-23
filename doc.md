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
## more and Less
### 提供一页一页的显示方式，按空格键向下一页，Enter键向下一行，Q键退出。less 功能与more相似但更强大
```
more ${filename}
```
## 

## head and tail
### 分别用于显示文本开头或者末尾的内容，-n指定显示地行数，如不指定则是默认行数
```
head -n ${filename}
```

#文件（夹）操作
## pwd
### 显示当前路径
## cd
```
cd   #进入用户主目录
cd - #进入上一个目录
cd ~ #进入用户主目录
cd / #进入根目录
cd ..#进入上级目录
```
## ls
```
ls -l  #列出当前目录下文件及其属性
ls -a  #列出当前目录下所有文件，包括隐藏文件
ls ${path/to\dir} #列出指定目录下的文件
```
## chmod and chown
```
chown [-R] ${username} ${file or directory}
```
chmod 用于改变文件权限设置
```
chmod [-R] 777 ${filename}
```




# 查找
## grep
### grep(global search regular expression) 可以用于查找文件中的关键词
```
grep -n ${target string} ${filename}
grep -r ${target string} *    #在当前目录下递归搜索包含指定字符串的文件
grep -l -r ${target string} * #在当前目录下递归搜索包含指定字符串的文件,只显示文件名
```
### 正则表达式
http://www.cnblogs.com/ggjucheng/archive/2013/01/13/2856896.html
## 查找文件 find,locate,whereis
```
find ${path} -name ${ketword} -print [- type d(目录)/f(文件)]
locate ${filename}
whereis   # used to find executable files
```

# 获取帮助
```
man ${command}
```

# 输出

### 输出重定向 >
``` 
ls > ls.log #覆盖
ls > ls.log #追加
```

# 管道
### |
```
ls | grep sy  # 将左边的输出进行处理和筛选再输出
```

# 进程管理
### 杀死进程
```
ps aux | grep ${keyword}  # 列出包含keyword的进程
kill ${process id}
kill -9 $(process id}     # 强制kill
```
# 磁盘


# 软件包
## APT(Advanced Package Tool)
### 常用的两个命令，apt-get 和 apt-cache。 前者安装软件包，后者用于查找相关信息。
```
apt-get update
apt-get install ${package}
apt-get upgrade
apt-get remove[autoremove]
apt-get clean                #删除已下载的包文件

apt-cache search ${package name}
```
###apt-get 的安装源以文件的形式存放在/etc/apt/sources.list中
## dpkg
### dpkg是运行于ubuntu和debian系统上的包管理器，安装包以.deb结尾。
```
dpkg [--force] [-i(nstall)] ${package}
dpkg -l | grep ${ketword}
dpkg --remove ${package}
```