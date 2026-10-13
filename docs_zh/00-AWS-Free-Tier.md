---
comments: true
---
# Day 0 - 创建你自己的服务器 - 使用 AWS 免费套餐

请参考 [Day 0 - 获取你自己的服务器](00.md) 来梳理你的选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云上（使用 DigitalOcean、Linode 和 Vultr 之类的服务商）](00-VPS-small.md)
* [云上（使用 AWS、Azure 和 Google Cloud 之类的服务商）](00-VPS-big.md)

**提示**：看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=2892s)中的演示过程。这个视频涵盖了许多可能的方案（用 VirtualBox 搭建本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## AWS 免费套餐，它永远免费吗？

AWS Free Tier 旨在让新用户在注册 AWS 之后的 12 个月内能够免费探索和测试各种 AWS 服务，但有一定的用量限制。当你的 12 个月免费使用期到期，或者你的应用用量超出套餐额度时，你就需要按标准的按量付费价格付费。如果你符合条件，可以用 Educate Pack 来延长免费使用期。

## 使用 AWS Educate 套餐注册：

* 访问 AWS Educate 网站 https://aws.amazon.com/education/awseducate/
* 点击页面右上角的 “Join AWS Educate” 按钮。
* 选择最符合你身份的描述，无论你是学生还是教育工作者。
* 填写所需信息来创建 AWS Educate 账号，包括你的姓名、电子邮箱，以及你的学校或机构名称。
* 创建账号后，你就可以访问 AWS Educate Starter Account，其中包含 100 美元的 AWS 促销抵扣额度、超过 25 项 AWS 服务的免费使用权，以及帮助你上手 AWS 的自学实验和教程。

请注意，AWS Educate 项目面向对学习云计算和 AWS 服务感兴趣的学生和教育工作者。为了符合该项目的资格，你需要提供学生或教育工作者身份的证明。

## 注册 AWS

注册相当简单——只需提供你的电子邮箱和一个你自己选择的密码——外加一个用于 2FA（第二重身份验证）的手机号码。
你还需要提供你的 VISA 或其他信用卡信息。

* 支持计划（Support Plan）请选择 “Basic Plan/Free”。

登出，然后重新登录，接着依次选择：

* Services - 在顶部菜单中
* EC2 - 在服务列表中

用 “AWS 的话”说，我们要创建的服务器是一个 “EC2 计算实例（compute instance）”——所以现在选择 “Launch Instance”。你会看到若干镜像选项——选择名称中带有 “Ubuntu Server LTS” 的那个。
在下一个页面上你会看到类型选项——通常只有 “t2.micro” 符合免费套餐资格，不过这也够用了，所以选择 “review and Launch”。
在 review 页面上会有一个 “Security Groups” 选项——这实际上是 AWS 默认提供的一项防火墙配置。总体而言它是好东西，但对我们的目的来说，我们希望服务器完全暴露，所以我们要编辑它以有效地禁用它，像这样：

* 选择 “Configure Security Group”
* 选择 “Add Rule”
* Type: “All traffic”，Source: “Anywhere”

这会开放所有端口和协议，允许从任何地方访问。虽然对生产服务器来说这可能不明智，但这正是我们这门课程想要的。

现在选择 “Launch”。当提示你创建密钥对（key pair）时，创建一个。

你的服务器实例现在应该启动了，你可以通过以下方式登录：

* Services、EC2、Running instances、Connect

## 通过 SSH 远程访问

你应该会在账号控制面板中看到你的服务器有一项 “Public IPv4 address”（或类似名称）——这是它唯一的互联网 IP 地址，也是你通过 SSH（Secure Shell 协议）连接它的方式——我们会在第一课中讲到它。

这个视频 [How to Set Up AWS EC2 and Connect to Linux Instance with PuTTY](https://www.youtube.com/watch?v=kARWT4ETcCs) 对整个过程做了很好的概述。

你将以 `ubuntu` 用户身份登录。它已被加入 `adm` 和 `sudo` 组，在 Ubuntu 系统上，这使它有权读取各种日志——并在需要时通过 _sudo_ 命令“成为 root”。

## 你现在是一名系统管理员了

通过输入以下命令确认你可以执行管理任务：

```bash
sudo apt update
```

（通常这会提示你确认密码，但由于你使用的是公钥认证，系统未曾提示你设置密码——而且 AWS 已经把 `sudo` 配置为不对 `ubuntu` 请求密码。）

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
