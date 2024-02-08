# GPU servers

## Management

## 拿到容器后

第一时间修改默认弱密码为强密码，在服务器上执行，并妥善保管输出的随机密码：
```bash
password=$(openssl rand -base64 21)
echo "root:$password" | chpasswd
echo "Your password is changed to $password"
```

使用以下指令，在客户端本地生成公密钥对:
```bash
ssh-keygen -t ed25519
```

使用以下指令，将生成的公钥加到服务器上的`.ssh/authorized_keys`，可免密码登录:
```bash
ssh-copy-id -f -i ~/.ssh/id_ed25519.pub <server>
```

### 使用说明

关于服务器、实验平台的使用方法，请查阅
[此处（院内局域网连接）](http://172.16.101.131:30000/tinker/awsometools/-/wikis/How-to-Use-GPU-Containe)。

有任何使用上的问题先在这个仓库下提Issue，
我们会收到邮件通知，也欢迎提PR完善我们的实验环境。
