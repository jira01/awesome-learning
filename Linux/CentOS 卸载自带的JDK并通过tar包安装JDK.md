# CentOS 卸载自带的JDK并通过tar包安装JDK
## 卸载自带JDK
```shell
# 查询是否安装Java软件
rpm -qa|grep java

# 卸载自带的jdk
sudo rpm -e  java-1.6.0-openjdk-1.6.0.41-1.13.13.1.el6_8.x86_64
sudo rpm -e  --nodeps java-1.7.0-openjdk-1.7.0.181-2.6.14.10.el6.x86_64
```
## 通过jdk tar安装JDK
```shell
# 解压tar包到指定目录
tar -zxvf /opt/software/jdk-8u212-linux-x64.tar.gz -C /opt/module/

# 编辑/etc/profile
vim /etc/profile
# 添加如下内容
export JAVA_HOME=/opt/module/jdk1.8.0_212
export PATH=$PATH:$JAVA_HOME/bin

# 修改后文件生效
source /etc/profile
```