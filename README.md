##  centos6 vps安装远程桌面环境

###  先下载桌面环境    
    yum update -y
    yum -y groupinstall "Desktop" "Desktop Platform" "X Window System" "Fonts"
    yum -y groupinstall "General Purpose Desktop"
    
###  添加额外package   
    wget http://download.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm
    rpm -ivh epel-release-6-8.noarch.rpm
    
    
 ###  下载用于远程连接的vncserver   
    yum install tigervnc-server
    yum install fontforge
     
###  修改/etc/sysconfig/vncserver   
    VNCSERVERS=""1:root""
    VNCSERVERARGS[1]=""-geometry 1024x768 -alwaysshared -depth 24""
    访问的端口是5900+1=5901
     
运行vncpasswd来设置密码   

### 运行vncserver来生成/root/.vnc/xstartup   
     #!/bin/sh
     startx
     
### 远程桌面vnc server命令  
    service vncserver start
    service vncserver stop
    chkconfig vncserver on(开机启动)
    
电脑或者ipad或者chrome下载VNC客户端

###  参考：    
* https://www.earnworld.in/how-to-install-xfce-desktop-on-centos-6-32bit64bit-vps/
* https://www.server-world.info/en/note?os=CentOS_6&p=x
* https://wiki.centos.org/HowTos/VNC-Server
