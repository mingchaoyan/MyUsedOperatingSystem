## 安装

CentOS 7 安装界面打开网络

## 管理

### 开关机

* 关机

    shwtdown -h now

### 用户

* 创建用户

    useradd mingchaoyan
    passwd mingchaoyan

* 用户添加sudo权限

    vim /etc/sudoers

### 服务

#### ssh 

* 修改sshd 配置

    PubkeyAuthentication yes
    #PasswordAuthentication yes

* 建 .ssh 目录

    mkdir -p /home/xxx/.ssh

* 粘贴 key

    vim /home/xxx/.ssh/authorized_keys

* 调整权限

    chmod 700 /home/xxx/.ssh
    chmod 600 /home/xxx/.ssh/authorized_keys
    chown -R xxx:xxx /home/xxx/.ssh

* 重启sshd

    systemctl restart sshd

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
