# 编写自定义shell脚本工具
## 文件或目录复制到远程机器
### 前提
Linux机器配置了通过ssh免密远程登入

### 实现方式
- scp
```
scp -r 要拷贝的文件路径/名称 目的用户@主机:目的路径/名称
```
- rsync
```
rsync -rvl 要拷贝的文件路径/名称 目的用户@主机:目的路径/名称
```
-r：递归
-v：显示复制过程
-l：拷贝符号链接

### 功能描述
同步文件/目录到远程主机的相同文件/目录下

### 实现
```shell
#!/bin/bash
#1 获取输入参数个数，如果没有参数，直接退出
pcount=$#
if((pcount==0)); then
echo no args;
exit;
fi

#2 获取文件名称
p1=$1
fname=`basename $p1`
echo fname=$fname

#3 获取上级目录到绝对路径
pdir=`cd -P $(dirname $p1); pwd`
echo pdir=$pdir

#4 获取当前用户名称
user=`whoami`

#5 循环
for((host=103; host<105; host++)); do
    echo ------------------- hadoop$host --------------
    rsync -rvl $pdir/$fname $user@hadoop$host:$pdir
done
```
在/home/用户名/bin目录下创建文件  `xsync`

注意：如果将xsync放到/home/用户名/bin目录下仍然不能实现全局使用，可以将xsync移动到/usr/local/bin目录下。

### 遇到的问题
- 无权限创建文件或目录
通过更改目录的用户权限来解决
