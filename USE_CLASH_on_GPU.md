# Using local proxy on remote SSH server

We use remote port forwarding to let GPU using our clash in windows/mac to Accelerate.
- First we use "ssh -N  -R 7890:localhost:7890 usrname@yourGPUip -p your_ssh_port" to Establish a ssh channel.
  - Alternatively, you can set up a host config in `.ssh/config` (on Linux / macOS, path will be different on different windows SSH clients).
    ```
    Host <your_gpu_name>
        HostName <your_ip>
        Port <your_port>
        RemoteForward 7890 localhost:7890
    ```
    and connect to <your_gpu_name> with:
    ```bash
    ssh your_gpu_name
    ```
- Secondly, we set `alias proxy='ALL_PROXT=localhost:7890 http_proxy=localhost:7890 https_proxy=localhost:7890'`
  in docker's ~/.bashrc, and either `exec bash` or re-login to your server.
- Then, you can use docker with your clash by adding `proxy` in front of your cmd.

## Testing your config

How to make sure your setting is right?
- Run `proxy curl ifconfig.co` and it should return your proxy's external IP address.
- Search the IP address in baidu.com to make sure it is outside the mainland.

## FAQs

- "proxy curl ifconfig.co":curl: (52) Empty reply from server 
  - enable "允许局域网链接" on your clash
