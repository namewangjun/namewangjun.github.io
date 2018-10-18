# Linux操作系统基础

    ## 1.linux的系统简介

        Linux的出现在1991年,是由李纳斯(发明内核Linus Torvalds)和其他爱好者共同开发,源代码开放的unix.

    ## 2.linux的优良特性

        ### 1.分时的多用户,多任务的操作系统
        ### 2.多数网络协议支持,方便的远程管理
        ### 3.强大的内存管理和文件管理系统
        ### 4.大量的可用的软件和免费的软件
        ### 5.优良的稳定性和安全性 
        ### 6.良好的可移植性和灵活性
        ### 7.可供选择的厂商多
    
    ## 3.linux操作系统的结构
        
        用户-(图形界面)->应用层-(shell命令)->Shell层-(系统调用)->内核层-->硬件

    ## 4.linux的目录结构

	顶层:        
	/	     根目录                   

	次顶层          
       *bin          存放二进制可执行文件
	sbin         存放二进制可执行文件,只有root权限才能访问
       *etc          存放linux系统配置文件 ( root权限修改 )
       *usr	     存放共享的系统资源
       *home	     存放用户文件的根目录
	root	     管理员目录
	dev 	     存放设备文件
       *lib	     存放和文件系统中程序运行有关的共享库和内核模型
	mnt	     系统管理员安装临时文件系统的安装点
	boot         存放系统引导时使用的各种文件
	tmp	     存放临时文件
	var	     存放运行时需要改变数据的文件
	
    ## 5.linux系统的关机开机
	
	### 1.开机
	     
	    reboot 	     重启
	    shutdown -r now (立刻重启)  参数可以是now现在,具体时间,时间段
	    shutdown -c     (取消重启)

	### 2.关机
	    
	    halt 	立刻关机
	    poweroff 	立刻关机
	    shutdown -h now (立刻关机,仅适用于root)
	    shutdown -h 时间段 

    ## 6.linux系统的运行级别 /etc/inittab
	
	### 1.级别说明
	    0           虚拟机关闭
	    1	    单用户,只有少部分进程运行,所有服务不启动
	    2	    多用户模式，和运行级别3一样，只是网络问卷系统（NFC）服务没有启动
	    3	    多用户模式，允许多用户登录系统，是系统默认的启动级别
     	    4       未用
	    5	    多用户模式，并且在系统启动后运行X Windwos，给出一个图形化d登陆窗口
	    6	    所有进程被终止，重新启动系统

	### 2.查看运行级别
	    
 	    runlevel    查看当前运行级别
	    init  级别	切换运行级别

    ## 7.linux的网络配置(很多设置都需要root权限)
	
	### 1.查看主机名并修改主机名
		
	    hostname 			(查看主机名)
	    hostname 临时主机名 	(临时修改主机名,重启恢复)
	    
	    永久修改 vi /etc/hostname    直接修改配置文件
	    
	(su  切换用户root
	exit  退出用户
	vi  编辑
	esc 先退出输入状态
	:q! 强制退出(已输入,无法:q退出)
	:wq! 保存强制退出
	useradd 添加用户
	passwd 用户名 (修改密码)  )
	
	### 2.测试网络连接
	
	    ping 目标主机ip地址 	测试网络连接
	    ctrl + c                    终止测试	
	
	### 3.测试网络接口
	
	    ifconfig 
	    如果不能使用
	    ( root权限 ) yum install [-y] net-tools  (安装) 
	
	### 4.重启network网络服务
  	
	    service network restart

	### 5.设置防火墙
	
	    service firewalld status     查看防火墙状态
	    systemctl stop firewalld     临时关闭
	    systemctl disable firewalld  禁止开机时启动防火墙

	### 6.本地主机映射文件(对应ip地址)
	    
	    vi /etc/hosts/    保存主机名 与 ip地址 的映射

	    #### 从域名中获得映射,在本地中寻找ip地址(若本地中没有,向外部DNS服务器查询)
  	    #### 获取ip地址,发出真实请求
	
	### 7.设置网络信息


	    vim /etc/sysconfig/network-scripts/ifcfg-ens33 配置文件
	    
     	### 8.设置SELinux
	
	    #### 1.查看SELinux
	    
	    getenforce 查看     共有三种状态  
	
	    Enforcing : 强制模式,代表记录安全警告 且 阻止可疑信息
	    Permissive: 宽容模式,代表记录安全警告 但 不阻止可疑信息
	    Disable   : 关闭
	    
 	    #### 2.设置SELinux(当前有效)
	
	    setenforce 设置(重启失效,所以disable不能设置)

	    #### 3.配置文件中修改(永久有效,注意权限为root修改)

	    vi /etc/selinux/config



 






















	    
