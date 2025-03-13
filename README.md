# 🚀 **Panabit SD-WAN 客户端正式发布！**

🔹 Panabit 的 **SD-WAN** 之前主要用于 **站点间 VPN 互联**，两端都需要部署 Panabit 设备。  
🔹 现在，**全新发布** Windows 和 Linux 客户端，电脑安装后 **即可接入 SD-WAN 网络**！  

📥 **下载地址**：[👉 点此下载](https://www.panabit.com/download)  

> 📝 **注**：Windows 版本与 Linux 版本均在压缩包内。

---

## 📌 **目录**
1. [🖥 Windows 版本部署](#-windows-版本部署)
2. [🐧 Linux 版本部署](#-linux-版本部署)
   - [📂 创建配置目录](#-创建配置目录)
   - [⚙️ 创建配置文件](#-创建配置文件)
   - [📤 上传程序](#-上传程序)
   - [🔑 赋予执行权限](#-赋予执行权限)
   - [▶️ 运行程序](#-运行程序)
   - [🔍 验证 iwan0 设备](#-验证-iwan0-设备)
   - [🚦 添加静态路由](#-添加静态路由)

---

## 🖥 **Windows 版本部署**
解压后 **双击运行** `iWAN.exe` 即可。

| 配置项    | 说明                          |
|-----------|-------------------------------|
| **服务器** | iWAN 服务端的 IP 地址或域名  |
| **端口号** | iWAN 服务端映射的端口号      |
| **用户名** | iWAN 的登录用户名            |
| **密码**   | iWAN 用户名对应的密码        |

---

## 🐧 **Linux 版本部署**

### 📂 **创建配置目录**
在运行程序前，先 **手动配置服务端信息**。  
使用以下命令 **创建 `/etc/sdwan` 目录**：
```bash
sudo mkdir /etc/sdwan
sudo vim /etc/sdwan/iwan.conf
```

### ⚙️ **创建配置文件**
```bash
[iwan0]
server=对端ip
username=登录账号名
password=密码
port=对端端口
mtu=最大传输单元
encrypt=是否加密：0为不加密，1为加密
```

### 📤 **上传程序**

通过 `scp` 工具上传文件到后台。

### 🔑 **赋予执行权限**

```bash
chmod +x /root/sdwand
```

### ▶️ **运行程序**

```bash
/root/sdwand &
```

###  🔍 **验证-iwan0-设备**

运行 `ifconfig` 可以看到添加的 `iwan0` 接口，并且会自动分配IP。

###  🚦 **添加静态路由**

添加走 iwan 网段的静态路由：

```bash
route add –net x.x.x.x/nn dev iwan0
```

---
[🔝 返回目录](#-目录)  

