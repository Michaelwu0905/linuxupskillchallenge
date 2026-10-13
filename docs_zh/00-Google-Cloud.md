---
comments: true
---
# Day 0 - 创建你自己的服务器 - 使用 Google Cloud Platform 免费套餐

请参考 [Day 0 - 获取你自己的服务器](00.md) 来梳理你的选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云上（使用 DigitalOcean、Linode 和 Vultr 之类的服务商）](00-VPS-small.md)
* [云上（使用 AWS、Azure 和 Google Cloud 之类的服务商）](00-VPS-big.md)

**提示**：看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=8778s)中的演示过程。这个视频涵盖了许多可能的方案（用 VirtualBox 搭建本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## 注册 GCP

注册相当简单——只需提供你的电子邮箱和一个你自己选择的密码——外加一个用于 2FA（第二重身份验证）的手机号码。
你还需要提供你的 VISA 或其他信用卡信息。

* 选择 "Compute Engine" 并点击 "VM Instances"。
* 创建一个新实例。
* 选择你想要的区域。
* 在 Machine Configuration 中选择系列并设为 "E2"，机器类型设为 "e2-micro"。
* 把启动盘（boot disk）改为 "Ubuntu LTS"

在我们创建好自己的服务器之后，需要开放所有端口和协议，以便从任何地方访问。虽然对生产服务器来说这可能不明智，但这正是我们这门课程想要的。

打开你的 GCP 首页，进入 Networking > VPC Network > Firewall > Create Firewall

把 "Direction of Traffic" 设为 "Ingress"
把 "Target" 设为 "All instances in the network"
把 "Source Filter" 设为 "IP Ranges"
把 "Source IP Ranges" 设为 "0.0.0.0/0"
把 "Protocols and Ports" 设为 "Allow All"
创建之后，重复这些步骤，再新建一条 Firewall，把 "Direction of Traffic" 设为 "Egress"

## 第一次登录

选择你的实例并点击 "SSH"，它会打开一个新的窗口控制台。要访问 root，在命令行中输入 `sudo -i passwd`，然后设置你自己的密码。输入 `su` 再输入你的密码即可登录。注意，输入或粘贴密码时它不会显示出来。

## 通过 SSH 远程访问

如果你打算通过第三方工具（例如 Putty）访问你的服务器，也可以参考 <https://cloud.google.com/compute/docs/instances/connecting-advanced#thirdpartytools>。

## 你现在是一名系统管理员了

通过输入以下命令确认你可以执行管理任务：

```bash
sudo apt update
```

然后：

```bash
sudo apt upgrade -y
```

不要太在意这些命令的输出和消息，但它们是否成功应该很明确。（遇到任何提示就采用默认选项。）这些命令是你在 Ubuntu Linux 系统上强制安装更新的方式，只有管理员才能执行。

**重启**

如果在这次首次检查更新时发现有内核更新，系统可能会请求用户重启。这是你需要重启服务器的少数场合之一，所以在更新完成后就重启吧：

```bash
sudo reboot now
```

你的服务器现在已经全部配置好，可以开始课程了！

请注意：

* 这台服务器现在正在运行，并且完全暴露在整个互联网面前
* 管理它的责任完全由你承担
* 你刚刚安装了最新更新，所以它目前应该是安全的

要登出，输入 `logout` 或 `exit`。

## 当你完成之后

在挑战进行的这一个月里让虚拟机保持运行是安全的，但你随时可以**停止（Stop）**这个实例。不过它仍会继续计入账单。

当你不再需要这台虚拟机时，请**终止/销毁（Terminate/Destroy）**实例。

**现在你已经准备好开始挑战了。[第 1 天](01.md)，出发！**
