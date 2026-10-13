---
comments: true
---
# Day 0 - 在云上创建你自己的服务器（更省钱的方式）

请参考 [Day 0 - 获取你自己的服务器](00.md) 来梳理你的选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云上（使用 DigitalOcean、Linode 和 Vultr 之类的服务商）](00-VPS-small.md)
* [云上（使用 AWS、Azure 和 Google Cloud 之类的服务商）](00-VPS-big.md)

**提示**：看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ)中的演示过程。这个视频涵盖了许多可能的方案（用 VirtualBox 搭建本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud），能帮你做选择。

## 注册 VPS

注册是即时的——只需提供你的电子邮箱和一个你自己选择的密码，你就进来了！不过要创建虚拟机，你可能需要在账户部分提供信用卡信息（或其他用于计费的信息）。

### 对比
| 服务商      | 实例类型           | vCPU | 内存 | 存储   | 价格 | 试用额度  |
| ------------- | ----------------------- | ---- | ------ | --------- | ----- | -------------- |
| [Digital Ocean](https://m.do.co/c/0543704a0b92) | Basic Plan              | 1    | 1 GB   | 25 GB SSD | $6.00 | $200 / 60 天 |
| [Linode](https://www.linode.com/lp/refer/?r=5f3727944be972fe99747977e0a25fc21390c5d0)        | Nanode 1GB              | 1    | 1 GB   | 25 GB SSD | $5.00 | $100 / 60 天 |
| [Vultr](https://www.vultr.com/vultr-vs-linode/?promo=LINODE150)         | Cloud Compute - Regular | 1    | 1 GB   | 25 GB SSD | $5.00 | $250 / 30 天 |

更多细节：

* [Digital Ocean 入门](https://docs.digitalocean.com/products/getting-started/)
* [Linode 入门](https://www.linode.com/docs/products/platform/get-started/)
* [Vultr 入门](https://www.vultr.com/resources/faq/)

## 创建虚拟机

这些 VPS 的流程基本相同，下面是一些分步说明：

### 用 Digital Ocean 创建虚拟机（也就是 Droplet）

* 从左侧边栏选择 "Manage, Droplets"。（“droplet”是 Digital Ocean 给服务器起的可爱名字！）
* 点击 *Create > Droplet*
* **Choose Region**：选择离你最近的区域。注意价格可能因区域而异。
* **DataCenter**：使用默认值（它会替你选一个）
* **Choose an image**：选择镜像 "Ubuntu"，并选最新的 LTS 版本
* **Choose Size**：Basic Plan（共享 CPU）+ Regular。点击 1GB 内存 / 1 CPU / 25GB SSD 磁盘的那个选项
* **Choose Authentication Method**：选择 "Password"，为 root 账号输入一个强密码。
* *注意，由于服务器在互联网上，它会立刻遭到机器人尝试“暴力破解” root 密码的攻击。把密码设强一点！*
* **或者，如果你想更安全**，选择 "SSH Key"，并[添加你在本地新建的公钥](https://docs.digitalocean.com/products/droplets/how-to/add-ssh-keys/)
* 选一个主机名，因为默认的名字相当难看。
* Create Droplet

### 用 Linode 创建虚拟机（也就是 Node）

* 点击 *Create Linode*（“linode”是 Linode 给服务器起的可爱名字）
* **Choose an Distribution**：选择镜像 "Ubuntu"，并选最新的 LTS 版本
* **Choose Region**：选择离你最近的区域。注意价格可能因区域而异。
* **Linode Plan**：Shared CPU + Nanode 1GB。这个选项有 1GB 内存 / 1 CPU / 25GB SSD 磁盘
* **Linode Label**：选一个主机名，因为默认的名字相当难看。
* **Choose Authentication Method**：在 "Root Password" 处为 root 账号输入一个强密码。
* *注意，由于服务器在互联网上，它会立刻遭到机器人尝试“暴力破解” root 密码的攻击。把密码设强一点！*
* **而且，如果你想更安全**，点击 "Add An SSH Key"，并[添加你在本地新建的公钥](https://www.linode.com/docs/guides/use-public-key-authentication-with-ssh/)
* Create Linode

### 用 Vultr 创建虚拟机

* 从左侧边栏选择 "Products, Instances"。（没有可爱的名字）
* 点击 *Deploy Server*
* **Choose Server**：Cloud Compute（共享 vCPU）+ Intel Regular Performance
* **Server Location**：选择离你最近的位置。注意价格可能因区域而异。
* **Server image**：选择镜像 "Ubuntu"，并选最新的 LTS 版本
* **Server Size**：点击 1GB 内存 / 1 CPU / 25GB SSD 磁盘的那个选项
* **SSH Keys**：点击 "Add New"，并[添加你在本地新建的公钥](https://www.vultr.com/docs/deploy-a-new-server-with-an-ssh-key/)
* *注意，由于没有仅用 root 密码认证的选项，你需要创建一对 SSH 密钥。*
* **Server Hostname & Label**：为你的服务器选一个主机名。
* **禁用** "Auto Backups"。本挑战不需要它们，只会增加账单。
* Deploy Now

## 第一次通过控制台登录

我们将通过 SSH 访问服务器，但如果出于某种原因你卡在了那一步，还有通过控制台访问的办法：

* Digital Ocean：[Droplet Console](https://docs.digitalocean.com/products/droplets/how-to/connect-with-console/)
* Linode：[LISH Console](https://www.linode.com/docs/products/compute/compute-instances/guides/lish/)
* Vultr：[Web Console](https://www.vultr.com/docs/vultr-web-console-faq/)

## 通过 SSH 远程访问

你应该会在账号控制面板中看到你的服务器有一项 "Public IPv4 address"（或类似名称）——这是它唯一的互联网 IP 地址，也是你通过 SSH（Secure Shell 协议）连接它的方式——我们会在第一课中讲到它。

* **Digital Ocean**：点击 *Networking tab > Public Network > Public IPv4 Address*
* **Linode**：点击 *Network tab > IP Addresses > IPv4 - Public*
* **Vultr**：点击 *Settings tab > Public Network > Address*

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

## 创建一个可用的管理员账号

我们要遵循最佳实践，不以 "root" 身份远程登录，因此我们会创建一个普通用户账号，但它有权在需要时“成为 root”，像这样：

```bash
adduser snori74
```

```bash
usermod -a -G admin snori74
```

```bash
usermod -a -G sudo snori74
```

（当然，把 `snori74` 换成你自己的名字！）

*这个*账号就是你将来登录并操作服务器所用的账号。它已被加入 `adm` 和 `sudo` 组，在 Ubuntu 系统上，这使它有权读取各种日志，并在需要时通过 _sudo_ 命令“成为 root”。

要用你的新用户登录，请[从 root 复制 SSH 密钥](https://askubuntu.com/questions/1218023/copying-ssh-key-from-root-to-another-user-on-same-machine/1218026#1218026)。

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
