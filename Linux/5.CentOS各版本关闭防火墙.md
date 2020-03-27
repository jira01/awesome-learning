# CentOS 各版本关闭防火墙
## CentOS 6
查看|启动防火墙
```shell
sudo servcie iptables status|start
```

关闭
```shell
# 临时关闭
sudo servcie iptables stop

# 永久关闭
chkconfig iptables off 
```


## CentOS 7
从centos7开始使用systemctl来管理服务和程序，包括了service和chkconfig。

查看|启动防火墙
```shell
systemctl list-unit-files|grep firewalld.service  
systemctl status firewalld.service
```

关闭防火墙
```shell
systemctl stop firewalld.service #停止firewall
systemctl disable firewalld.service #禁止firewall开机启动
```