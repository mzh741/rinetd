FORK FORM MIXOOL*
最推荐的一键脚本：
  
    curl https://raw.githubusercontent.com/linhua55/lkl_study/master/get-rinetd.sh | bash
    wget "https://github.com/linhua55/lkl_study/releases/download/v1.2/rinetd_bbr_powered" -O /usr/bin/rinetd
    
 （bbr原版）
使用[@linhua](https://github.com/linhua55/lkl_study)的黑科技rinetd为OVZ构架的VPS开启bbr,**适用于CentOS/RHEL7+，Ubuntu15+，Debian8+**
***

       curl https://raw.githubusercontent.com/mzh741/rinetd/master/get-rinetd.sh | bash
#### 下载rintd二进制文件(原版bbr和修改版bbr二选一即可):
    1. wget --no-check-certificate https://raw.githubusercontent.com/mzh741/rinetd/master/rinetd
    2. wget --no-check-certificate https://raw.githubusercontent.com/mzh741/rinetd/master/rinetd_bbr_powered -O /root/rinetd
  * 修改权限:  
`chmod +x rinetd`
#### 修改rinetd的配置文件rinetd.conf,添加监听地址:
`vim /root/rinetd.conf`
```Bash
# bindadress bindport connectaddress connectport
0.0.0.0 8388 0.0.0.0 8388
```
#### 设置开机启动
`vim /etc/systemd/system/rinetd.service`
```Bash
[Unit]
Description=rinetd

[Service]
ExecStart=/root/rinetd -f -c /root/rinetd.conf raw venet0:0
Restart=always
  
[Install]
WantedBy=multi-user.target
```
#### 最后执行:
`systemctl enable rinetd.service && systemctl start rinetd.service`  
***
##### LKL BBR RINETD  
For more details:[linhua55/lkl_study](https://github.com/linhua55/lkl_study)  
PS: 推荐使用最新的[One-key script](https://github.com/linhua55/lkl_study#one-key-script)  
  * 更新个自己写的一键(rinetd文件不一定是最新的)：  
`curl https://raw.githubusercontent.com/mixool/script/master/rinetd.sh | bash`
