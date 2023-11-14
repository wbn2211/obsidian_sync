# 在 Ubuntu 上搭建使用 Jellyfin 的影视库
---
tag:

#学习/电脑/linux/docker/jellyfin #学习/电脑/linux/ssh 

---
学习目标：
1. 熟练使用SSH
2. 学会在 web 配置 Jellyfin
3. 使用  进行刮削

---
记录时间：


---
## 远程链接及初次设置
1. 远程链接 Raspberry Pi 
使用 `ssh -p 22 user@ipaddress` 命令进行局域网内部的访问
![[Pasted image 20221226100816.png]]

2. 初次登录 `Ubuntu Server` 需要进行密码的更改
![[Pasted image 20221226100910.png]]

3. 从上到下依次是 `原密码` 、`新密码` 、`重复新密码`
![[Pasted image 20221226100926.png]]

4. 使用新密码重新登录 SSH
![[Pasted image 20221226101406.png]]

5. 对 `Ubuntu` 进行换源
首先备份源
```shell
sudo cp /etc/apt/sources.list /home/ubuntu
#这句话是把 sources.list 文件备份到 /home/ubuntu/ 目录下的意思
```

![[Pasted image 20221226104402.png]]

然后使用指令编辑源文件
```shell
sudo vim /etc/apt/sources.list
```

如果提示*未知指令* 则使用 `sudo apt install vim` 安装 vim 软件

在整文档的最后加入来自清华大学开源网站镜像站的源
```shell
# 默认注释了源码镜像以提高 apt update 速度，如有需要可自行取消注释
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-updates main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-backports main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-security main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-security main restricted universe multiverse

# 预发布软件源，不建议启用
# deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-proposed main restricted universe multiverse
# deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ jammy-proposed main restricted universe multiverse
```

我使用的是 `Ubuntu Server 22.04 LTS` 版本，请根据自己的实际情况选用合适的源

6. 更新源和系统文件
```shell
sudo apt-get update
sudo apt-get upgrade
```

7. 打开所需端口（注意不要把22端口关了，血的教训）
```shell
sudo ufw status
# 注意查看端口信息

sudo ufw allow <port>
# 打开相关端口

sudo ufw enable
# 打开防火墙
```

## 开始安装
1. 如果没有 `curl` 和 `gnupg` 先进行安装
```shell
sudo apt install curl gnupg
```

2. 安装 apt 的 https 传输
```shell
sudo apt install apt-transport-https
# 有了就不需要了
```

3. 导入 GPG 签名密钥
```shell
wget -O - https://repo.jellyfin.org/ubuntu/jellyfin_team.gpg.key | sudo apt-key add -
```
4. 启用 `universe`
```shell
sudo add-apt-repository universe
# 获取所有FFMpeg依赖项
```

5. 添加源在`/etc/apt/sources.list.d/jellyfin.sources`
```shell
cat <<EOF | sudo tee /etc/apt/sources.list.d/jellyfin.sources
Types: deb
URIs: https://repo.jellyfin.org/$( awk -F'=' '/^ID=/{ print $NF }' /etc/os-release )
Suites: $( awk -F'=' '/^VERSION_CODENAME=/{ print $NF }' /etc/os-release )
Components: main
Architectures: $( dpkg --print-architecture )
Signed-By: /etc/apt/keyrings/jellyfin.gpg
EOF
```

6. 更新源
```shell
sudo apt update
```

7. 安装 Jellyfin
```shell
sudo apt install jellyfin
```

8. 管理你的 Jellyfin 系统服务
```shell
sudo service jellyfin status
sudo systemctl restart jellyfin
sudo /etc/init.d/jellyfin stop
```
