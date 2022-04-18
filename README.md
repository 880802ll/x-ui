# vps搭建x-ui面板

## **x-ui支持多协议多用户的 xray 面板**

------

**1. 功能介绍**

系统状态监控
支持多用户多协议，网页可视化操作
支持的协议：vmess、vless、trojan、shadowsocks、dokodemo-door、socks、http
支持配置更多传输配置
流量统计，限制流量，限制到期时间
可自定义 xray 配置模板
支持 https 访问面板（自备域名 + ssl 证书）
更多高级配置项，详见面板

------

**2. 准备工作**

1>域名一个做好解析，并且win+R输入CMD回车：键入ping空格输入你的域名，检查一下是否可以ping通
(PS:有cloudflare.com账号，申请域名并解析到了cloudflare)

2>境外VPS一台重置好主流系统，例如：**Debian/Ubuntu/CentOS**

3>下载并安装**FinalShell** **SSH**工具,服务器管理,远程桌面加速软件

Windows版下载地址:[点此直接进入下载](http://www.hostbuf.com/downloads/finalshell_install.exe)

macOS版下载地址:[点此直接进入下载](http://www.hostbuf.com/downloads/finalshell_install.pkg)

------

**安装更新运行环境**

**Debian/Ubuntu系统执行以下命令：**

```
apt update -y && apt install -y curl && apt install -y socat
```

------

**CentOS系统执行以下命令：**

```
yum update -y && yum update -y && yum install -y socat
```

------

**运行Acme脚本**

```
curl https://get.acme.sh | sh
```

**申请证书及密钥**
PS：修改代码中注释的域名，改为你自己的域名

```
~/.acme.sh/acme.sh --register-account -m xxxx@gmail.com
~/.acme.sh/acme.sh  --issue -d 你的域名   --standalone
```

**下载证书及密钥**

```
~/.acme.sh/acme.sh --installcert -d 你的域名 --key-file /root/private.key --fullchain-file /root/cert.crt
```

------

**安装&升级x-ui面板一键脚本**

```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

------

**BBR2加速**

```
wget --no-check-certificate -q -O bbr2.sh "https://github.com/yeyingorg/bbr2.sh/raw/master/bbr2.sh" && chmod +x bbr2.sh && bash bbr2.sh auto
```
