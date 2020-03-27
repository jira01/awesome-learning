## Linux通过SSH实现免密远程登入
### 原理
### 生成公钥和私钥
```shell
ssh-keygen -t rsa
```
### 将公钥拷贝到要免密登入的目标主机上
```shell
ssh-copy-id hadoop102 # 需要输入密码，执行后会在hadoop103的~/.ssh/authorized_keys文件中添加由ssh-keygen 生成的公钥
ssh-copy-id hadoop103  
ssh-copy-id hadoop104
```
要实现各机器间免密登入，每台机器上都需要执行上面的步骤（别忘了`ssh-copy-id 自己`）。