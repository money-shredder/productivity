We use remote port forwarding to let GPU using our clash in windows/mac to Accelerate.
- First we use "ssh -N  -R 7890:localhost:7890 usrname@yourGPUip -p your_ssh_port" to Establish a ssh channel.
- Secondly, we set "alias proxy='ALL_PROXT=localhost:7890 http_proxy=localhost:7890 https_proxy=localhost:7890'"in docker's ~/.bashrc
, and source ~/.bashrc
- Then, you can use docker with your clash by add "proxy " in front of your cmd.

---
How to make sure your setting is right?
- using "curl ifconfig.co" and it should return a ip that is your proxy's ip 
- I baidu the ip and found it's located in Taiwan which is the location of my clash proxy.
---
PROBLEM
- "proxy curl ifconfig.co":curl: (52) Empty reply from server 
  - open "允许局域网链接" on your clash
