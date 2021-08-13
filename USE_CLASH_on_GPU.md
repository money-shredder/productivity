# Using local proxy on remote SSH server

We use remote port forwarding to let GPU using our clash in windows/mac to Accelerate.
1. First we use
   ```bash
   ssh -N -R 7890:localhost:7890 usrname@yourGPUip -p your_ssh_port
   ```
   to Establish a ssh channel.
   
   Alternatively, you can set up a host config in `.ssh/config` (on Linux / macOS, path will be different on different windows SSH clients).
   ```ssh-config
   Host <your_gpu_name>
       HostName <your_ip>
       Port <your_port>
       RemoteForward 7890 localhost:7890
   ```
   and connect to <your_gpu_name> simply with:
   ```bash
   ssh <your_gpu_name>
   ```
2. Add the following line
   ```bash
   alias proxy='ALL_PROXY=localhost:7890 http_proxy=localhost:7890 https_proxy=localhost:7890'
   ```
   to your `~/.bashrc`, and either run `exec bash` or re-login to your server.
3. You can now use your local Clash as a proxy on the server, by adding `proxy` in front of your cmd.
   E.g. `proxy git clone ...`.

## Testing your config

How to make sure your setting is right?
- Run `proxy curl ifconfig.co` and it should return your proxy's external IP address.
- Search the IP address in baidu.com to make sure it is outside the mainland.

## FAQs

- "proxy curl ifconfig.co":curl: (52) Empty reply from server 
  - enable "允许局域网链接" on your clash
