# MentuHUST-SDJTU

## 主要功能

> 1、支持锐捷V2和V3客户端校验算法，完全兼容锐捷
>
> 2、支持多网卡
>
> 3、较好模拟锐捷各版本数据，支持所有版本锐捷
>
> 4、支持静态IP和DHCP（动态IP）认证
>
> 5、支持静态IP用户自定义IP（即绑定IP可与上网IP不同）
>
> 6、支持服务器消息提示和计费信息提示
>
> 7、认证成功稳定在线，即使掉线也可自动重连，支持ping某个IP智能重连
>
> 8、有相关工具支持，可自定义数据文件以实现尽可能的兼容，无需修改代码即可兼容所有版本

## 安装方式

- ### Ubuntu

  1. 下载本仓库内所有文件。

  2. 终端内依次执行以下命令：

     ```shell
     sudo dpkg -i mentohust_0.3.4-1_i386.deb
     sudo mkdir /etc/mentohust
     sudo mv ./8021x.exe /etc/mentohust
     sudo mv ./W32N55.dll /etc/mentohust
     sudo mv ./SuConfig.dat /etc/mentohust
     sudo mv ./data.mpf /etc/mentohust
     ```
     
  3. 修改MentoHUST配置文件：

     ```shell
     sudo gedit /etc/mentohust.conf
     ```
     ```ini
     [MentoHUST]
     ;用户名，长度不超过64
     Username=【账号】
     ;密码
     Password=【密码】
     ;网卡
     Nic=【网卡名称，可通过ifconfig命令查看】
     ;静态IP用户可以使用非本机IP
     IP=
     ;掩码，无关紧要
     Mask=
     ;网关，如果指定了就会监视网关ARP信息
     Gateway=
     ;DNS服务器，无关紧要
     DNS=
     ;Ping主机，用于掉线检测，0.0.0.0表示关闭该功能
     PingHost=0.0.0.0
     ;每次发包超时时间（秒）
     Timeout=8
     ;发送Echo包的间隔（秒）
     EchoInterval=30
     ;失败等待（秒）认证失败后等待RestartWait秒或者服务器请求后重启认证
     RestartWait=15
     ;寻找服务器时的组播地址类型 0标准 1锐捷 2将MentoHUST用于赛尔认证
     StartMode=0
     ;DHCP方式 0(不使用) 1(二次认证) 2(认证后) 3(认证前)
     DhcpMode=3
     ;是否后台运行: 0(否) 1(是，关闭输出) 2(是，保留输出) 3(是，输出到文件/tmp/mentohust.log)
     DaemonMode=0
     ;是否显示通知： 0(否) 1~20(是)
     ShowNotify=5
     ;客户端版本号，如果未开启客户端校验但对版本号有要求，可以在此指定，形如3.30
     Version=6.80
     ;认证数据文件，如果需要校验客户端，就需要正确设置
     DataFile=/etc/mentohust/
     ;进行DHCP的脚本
     DhcpScript=dhclient
     ```

  4. 终端执行命令：
     ```shell
     sudo mentuhust
     ```
