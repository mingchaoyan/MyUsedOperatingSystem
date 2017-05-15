# CentOS

## 历史
* 查看发行版本
    ```
    cat /etc/redhat-release
    ```
* 6.2 20111220 (redheat发布20111206) (4399)
* 7-1511 20151214 (redhat 发布 20151119) (码虫)



## 安装

CentOS 7 安装界面打开网络

## 管理

### 开关机

* 关机
```
shwtdown -h now
```

### 用户

* 创建用户

```
useradd mingchaoyan
passwd mingchaoyan
```

* 用户添加sudo权限
```
vim /etc/sudoers
```

### 修改主机名
```
hostnamectl set-hostname <主机名> 
```

### 防火墙
```
yum install iptables-services
systemctl mask firewalld.service
systemctl stop firewalld.service 
systemctl disable firewalld.service
systemctl start iptables.service 
systemctl enable iptables.service
$EDITOR /etc/sysconfig/iptables
-A INPUT -m state --state NEW -m tcp -p tcp --dport 22 -j ACCEPT
systemctl restart iptables.service 
```

### 服务

#### ssh 

* 无密码登录
    * 修改sshd 配置
    ```
    #PasswordAuthentication yes
    ```

    * 重启sshd
    ```
    systemctl restart sshd
    ```

* 添加用户

    * 建 .ssh 目录
    ```
    mkdir -p /home/<user-name>/.ssh
    ```

    * 粘贴 key
    ```
    vim /home/<user-name>/.ssh/authorized_keys
    ```

    * 调整权限
    ```
    chmod 700 /home/<user-name>/.ssh
    chmod 600 /home/<user-name>/.ssh/authorized_keys
    chown -R <user-name>:<group-name> /home/<user-name>/.ssh
    ```


#### 时间同步

    # 安装ntp服务
    yum install ntp
    # 开机启动服务
    systemctl enable ntpd
    # 启动服务
    systemctl start ntpd
    # 设置亚洲时区
    timedatectl set-timezone Asia/Shanghai
    # 启用NTP同步
    timedatectl set-ntp yes
    # 重启ntp服务
    systemctl restart ntpd
    # 手动同步时间
    ntpq -p

### 开发软件

#### Erlang

    yum install ncurses-devel
    yum install openssl-devel

#### 网络工具

    yum install net-tools # ifconfig
