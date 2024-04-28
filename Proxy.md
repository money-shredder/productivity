## 如何在命令行使用代理上网

1. 假设你的clash（或其他代理软件）
   已经在本地有一个7890的http代理端口，
   那么可以在ssh中使用反向代理打通7890端口，
   让服务器可以直接访问你的客户端的7890端口。
   在你的本地客户端执行：
   ```bash
   ssh -R 7890:localhost:7890 <用户名>@<ssh服务器ip> -p <ssh服务器端口>
   ```
   可连接服务器的同时并打通7890这个端口。
   或者，可以在`~/.ssh/config`
   （Linux和macOS路径，
   Windows路径取决于SSH客户端，
   详见客户端说明文档）
   中配置服务器，
   自动转发端口：
   ```ssh-config
   Host <ssh服务器昵称>
       HostName <ssh服务器ip地址>
       Port <ssh服务器端口>
       RemoteForward 7890 localhost:7890
   ```
   那么，
   可以直接通过以下指令使用昵称连接服务器，
   并依照`.ssh/config`里刚才写的配置，
   自动转发端口：
   ```bash
   ssh <ssh服务器昵称>
   ```
   或者，
   加入下面这个让将来所有的ssh连接都自动转发7890端口：
   ```ssh-config
   Host *
       RemoteForward 7890 localhost:7890
   ```
3. 在服务器`~/.bashrc`中加入以下内容：
   ```bash
   alias proxy='all_proxy=socks5://localhost:7890 http_proxy=http://localhost:7890 https_proxy=http://localhost:7890'
   ```
   然后执行`exec bash`重载shell，
   或者重新登录服务器。
4. 至此，在你的命令前面加上`proxy`，
   就可以使用客户端本地的代理软件来上网了，
   比如：`proxy git clone ...`。

## 如何测试连接是否成功？

服务器命令行中执行
`proxy curl ipinfo.io`，
如果正确走代理，
应该会返回代理的IP地址，
以及IP所在地（应当在海外）。
