---
comments: true
---
# Day 0 - 在云上创建你自己的服务器

请参考 [Day 0 - 获取你自己的服务器](00.md) 来梳理你的选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云上（使用 DigitalOcean、Linode 和 Vultr 之类的服务商）](00-VPS-small.md)
* [云上（使用 AWS、Azure 和 Google Cloud 之类的服务商）](00-VPS-big.md)

**提示**：看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ)中的演示过程。这个视频涵盖了许多可能的方案（用 VirtualBox 搭建本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud），能帮你做选择。

## 注册 VPS

注册相当简单——只需提供你的电子邮箱和一个你自己选择的密码——外加一个用于 2FA 或其他第二重认证方式的手机号码。你还需要提供信用卡信息。

### 对比

| 服务商      | 实例类型           | vCPU | 内存 | 存储   | 价格*  | 试用额度  |
| ------------- | ----------------------- | ---- | ------ | --------- | ------ | -------------- |
| [AWS](https://aws.amazon.com/free/)           | t2.micro                | 1    | 1 GB   | 8 GB SSD  | $18.27 | 免费套餐 1 年 |
| [Azure](https://azure.microsoft.com/free/)         | B1                      | 1    | 1 GB   | 30 GB SSD | $12.26 | $200 / 30 天 + 免费套餐 1 年 |
| [GCP](https://cloud.google.com/free/docs/free-cloud-features)           | e2-micro                | 1    | 1 GB   | 10 GB SSD | $ 7.11 | $300 / 90 天 |
| [Oracle](https://www.oracle.com/cloud/free/)        | VM.Standard.E2.1.Micro  | 1    | 1 GB   | 45 GB SSD | $19.92 | $300 / 30 天 + 永久免费服务 |

* *价格为估算值*

顺便说一句，尽量避开 IBM Cloud。它们没有好的优惠，而且根据以前学员的一些反馈，它们的 Linux 虚拟机被改动得太多，以至于某些命令无法按预期工作。

### 教育套餐

* AWS Educate：<https://aws.amazon.com/education/awseducate/>
* Azure for Students：<https://azure.microsoft.com/en-gb/free/students/>
* Google Cloud for Students：<https://cloud.google.com/edu/students>
* Oracle Academy Cloud Program：<https://academy.oracle.com/en/solutions-cloud-program.html>

## 创建虚拟机

这些 VPS 的流程基本相同，下面是一些分步说明：

* [在 AWS 上创建虚拟机](00-AWS-Free-Tier.md)
* [在 Azure 上创建虚拟机](00-Azure-Free-Tier.md)
* [在 GCP 上创建虚拟机](00-Google-Cloud.md)

### 用 Oracle Cloud 创建虚拟机

* 从左侧边栏菜单选择 "Compute, Instances"。
* 点击 *Create Instance*
* 选一个主机名，因为默认的名字相当难看。
* **Placement**：它会自动选择离你最近的位置。
* **Change Image**：选择镜像 "Ubuntu"，并选最新的 LTS 版本
* **Change Shape**：点击 "Specialty and previous generation"。点击 *VM.Standard.E2.1.Micro*——1GB 内存 / 1 CPU / 符合永久免费资格的那个选项
* **Add SSH Keys**：选择 "Generate a key pair for me"，下载私钥以便通过 SSH 连接。你也可以[添加你在本地新建的公钥](https://www.oracle.com/webfolder/technetwork/tutorials/obe/cloud/compute-iaas/generating_ssh_key/generate_ssh_key.html#summary)
* Create

## 第一次登录

选择你的实例并点击 "SSH"，它会打开一个新的窗口控制台。要访问 root，在命令行中输入 `sudo -i passwd`，然后设置你自己的密码。输入 `su` 再输入你的密码即可登录。注意，输入或粘贴密码时它不会显示出来。

## 通过 SSH 远程访问

你应该会在账号控制面板中看到你的服务器有一项 "Public IPv4 address"（或类似名称）——这是它唯一的互联网 IP 地址，也是你通过 SSH（Secure Shell 协议）连接它的方式——我们会在第一课中讲到它。

如果你使用的是 Windows 10 或 11，请按照说明[使用原生 SSH 客户端连接](https://youtu.be/Z46YbczqbiE)。在较旧版本的 Windows 上，你可能需要安装第三方 SSH 客户端，例如 [PuTTY](https://youtu.be/pWDHUlvcAsg)，并生成一对 [SSH 密钥](https://youtu.be/4jakCV5JYx0)。

如果你用的是 Linux 或 MacOS，打开终端并运行命令：

```bash
ssh username@ip_address
```

或者，使用 SSH 私钥：

```bash
ssh -i private_key username@ip_address
```

输入你的密码（或者如果你的 SSH 密钥受口令保护，就输入口令）。

瞧！你刚刚已经远程访问了你的服务器。

### 那 *root* 用户呢？

与小 VPS 服务商的做法不同，大厂不允许你用 root 连接。别担心，**root** 依然存在于系统中，但既然服务商一开始就为你创建好了管理员用户，你就不必去操心它了。

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
