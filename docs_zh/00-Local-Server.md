---
comments: true
---
# Day 0 - 创建你自己的本地服务器

请参考 [Day 0 - 获取你自己的服务器](00.md) 来梳理你的选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云上（使用 DigitalOcean、Linode 和 Vultr 之类的服务商）](00-VPS-small.md)
* [云上（使用 AWS、Azure 和 Google Cloud 之类的服务商）](00-VPS-big.md)

**提示**：看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=643s)中的演示过程。这个视频涵盖了许多可能的方案（用 VirtualBox 搭建本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## 没有信用卡的话，在云上创建服务器很困难

我们通常推荐使用 Amazon 的 AWS “免费套餐” 或 Digital Ocean——但两者都要求你有信用卡。Microsoft Azure、Google 的 GCP，以及 Low End Box（<https://lowendbox.com/>）上列出的绝大多数服务商也都是如此。

有些会接受 PayPal 或比特币——但通常没有信用卡的人也没有这些。

**警告：** 如果你在这个领域搜索得太深，很可能会遇到一堆诈骗、虚假或欺诈性的网站。虽然我们已努力从下面的链接中排除这类网站，但请务必小心！不用说，这些都不是“推广/返利”链接，我们不会从其中任何一个拿到回扣 :-)

### 可以当作信用卡使用、或类似信用卡的卡

* 借记卡
* <https://www.paysafecard.com/>
* privacy.com（仅限美国）

## 但如果我不想用云服务商呢？你完全可以用本地虚拟机

你可以在家用服务器上完成这个挑战，所有命令的运行方式都会和在云服务器上一样。不过，不暴露在“野外”确实会失去真实系统管理员所面对的那种感觉。

如果你要在私人服务器上搭建自己的虚拟机，请按最低要求来：1GHz CPU 核心、1GB 内存和 5GB 磁盘空间。你随时可以按自己的心意（或者你手头有多少硬件）来调整。

我们的建议是：如果可以，就用云服务器来获得完整体验，但不要被它限制住。**这是你的服务器。**

## 下载 Linux ISO

前往官方 [Ubuntu](https://ubuntu.com/download/server) 页面，下载最新的 LTS（长期支持）版本。

**注意**：下载**服务器（server）**版本，而不是**桌面（desktop）**版本。

## 用 VirtualBox 创建虚拟机

* [用 VirtualBox 创建本地 Linux 服务器（视频）](https://youtu.be/nKcfhI1B4mA)

安装 [VirtualBox](https://www.virtualbox.org/)，准备好之后：

* 点击 *Machine > New*
* 给你的虚拟机起个名字，*Type* 选择 Linux。点击 *Next*。
* 调整硬件：1024MB 内存和 1 个 CPU（这是最低配置，如果你的宿主机性能够，可以多分配一些）。点击 *Next*
* 虚拟硬盘：最小 2.5GB，5GB 是个不错的数值。点击 *Next*。
* 点击 **Finish**，但我们还没做完。
* 新虚拟机应该会出现在虚拟机列表中，选中它。
* 点击 *Machine > Settings*
* 点击 *Storage*。右键点击 Controller IDE，再点击 *Optical Drive*。
* 如果列表中有你下载的 Linux ISO，就选它；如果没有，点击 *Add* 并在你的目录中找到它。点击 *Choose*。
* 点击 *Network*，把网络适配器改为 **Bridged Adapter**（桥接网卡）。
* 点击 *OK*
* 点击 **Start**，或者 *Machine > Start > Normal Start*。

## 安装 Linux

几秒钟后，欢迎界面会加载出来。
每个页面底部都有 DONE 和 BACK 按钮。
用**方向键**和**回车键**来选择选项。当你的选择没问题时，用方向键向下移到 DONE，再按**回车**进入下一页。

* **欢迎界面（Welcome Screen）：** 选择你的语言
* **键盘配置（Keyboard Configuration）：** 选择键盘类型
* **选择安装类型（Choose type of install）：** 选择 _Ubuntu Server (minimized)_。它包含你需要的大部分软件包，同时又不臃肿。安装也会更快。

**关于 UBUNTU SERVER MINIMIZED 的说明**：它是 Ubuntu Server 的精简版本。主要优势是资源占用更少；与标准 Ubuntu Server 安装相比，它占用更少的磁盘空间、内存和 CPU，非常适合硬件受限的环境。不过它缺少许多便利工具和默认软件包，因此这些之后可能需要手动安装。这不算世界末日，反而会逼你更频繁地练习命令行。但如果你不想这么麻烦，而且硬件也够，那就预留 2GB 内存和 20GB 磁盘，直接进行完整的标准 Ubuntu Server 安装。

* **网络连接（Network Connections）：** 如果你按说明把虚拟机设置成了 **bridged adapter**（桥接网卡），其实就不用太担心。安装程序会自动从你本地网络路由器检测 DHCP 设置，你只需选择 DONE。
* **配置代理（Configure Proxy）：** 如果你的系统需要 http 代理才能连接互联网，就输入代理地址，否则直接选择 DONE。
* **配置 Ubuntu 归档镜像（Configure Ubuntu archive mirror）：** 保持默认。DONE。
* **引导式存储配置（Guided Storage Configurations）：** 我们要使用为这台虚拟机预留的全部存储空间，因此选择 **Use the Entire Disk** 选项。
* **存储配置（Storage Configuration）：** 保持标准存储配置并选择 DONE。当提示确认时，不用担心。这只会使用虚拟机磁盘，不会动你电脑的磁盘。
* **配置文件设置（Profile Setup）：** 输入你的名字、服务器名称、用户名和密码。这个用户将成为系统中的 `administrator` 用户（也就是 `sudo`），所以别忘了这个密码。
* **升级到 Ubuntu Pro（Update to Ubuntu Pro）：** 不用。暂时跳过。
* **SSH 设置（SSH setup）：** 选择安装 OpenSSH server，因为稍后你要通过它连接到服务器。
* **精选服务器 Snaps（Featured Server Snaps）：** 这些软件包现在都不重要，直接选择 DONE。
* **正在安装系统（Installing System）：** 现在你需要等几分钟让系统安装完成。你可以“取巧”通过跳过下载更新来加速安装：当页面底部出现 **Cancel update and Reboot** 时选择它，稍等片刻。你可以在首次启动后完成更新。安装完成后系统会自动重启。

## 第一次登录

第一次重启后，它会显示一个黑色屏幕，要求你 `login`。这时候就用你在安装时创建的那个用户名和密码。

注意：密码不会显示出来，连 `******` 都没有，相信它已经接收了输入就好。

如果你需要找出虚拟机的 IP 地址，只需在控制台输入：

```bash
ip address
```

这会给出 `inet`，也就是 IP 地址。你会需要它来通过 SSH 连接。

## 通过 SSH 远程访问

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

* 这台服务器现在正在运行，但并没有暴露在互联网上，也就是说其他人无法尝试连接它。我们建议你保持这样。把云端服务器暴露出去是一回事，把家里网络暴露出去就是另一回事了。为了你自己的安全，不要这么做。

要登出，输入 `logout` 或 `exit`。

## 当你完成之后

要在不使用时关闭服务器，只需输入：

```bash
sudo shutdown now
```

或者点击 _Force Shutdown_

## 其他一些选项

* [在 Windows 上用 WSL 安装 Linux](https://docs.microsoft.com/en-us/windows/wsl/install)
* [把一台旧 PC 变成 Linux 服务器](https://dev.to/jayesh_w/this-is-how-i-turned-my-old-laptop-into-a-server-1elf)
* [在树莓派上安装 Ubuntu server](https://ubuntu.com/tutorials/how-to-install-ubuntu-on-your-raspberry-pi#1-overview)
* [在 Docker 容器中运行 Linux](https://hudsonmendes.medium.com/docker-have-a-ubuntu-development-machine-within-seconds-from-windows-or-mac-fd2f30a338e4)


**现在你已经准备好开始挑战了。[第 1 天](01.md)，出发！**
