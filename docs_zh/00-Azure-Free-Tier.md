---
comments: true
---
# Day 0 - 创建你自己的服务器 - 使用 Azure 免费额度

请参考 [Day 0 - 获取你自己的服务器](00.md) 来梳理你的选项：

* [本地服务器/虚拟机](00-Local-Server.md)
* [云上（使用 DigitalOcean、Linode 和 Vultr 之类的服务商）](00-VPS-small.md)
* [云上（使用 AWS、Azure 和 Google Cloud 之类的服务商）](00-VPS-big.md)

**提示**：看看[配套视频](https://www.youtube.com/live/_-6UYOjRIVQ?t=7020s)中的演示过程。这个视频涵盖了许多可能的方案（用 VirtualBox 搭建本地服务器、AWS、Digital Ocean、Azure、Linode、Google Cloud、Vultr 和 Oracle Cloud）。

## 注册 Azure

注册相当简单——只需提供你的电子邮箱和一个你自己选择的密码——外加一个用于 2FA（第二重身份验证）的手机号码。Azure 对“企业”邮箱地址可能有点挑剔，例如使用工作地址或你自己的域名。如果是这种情况，请用注册页面上的链接新建一个 @outlook 或 @gmail.com 账号。
你还需要提供你的 VISA 或其他信用卡信息。

- 点击 'start building in azure'
- 点击 'Deploy a virtual machine'
- 点击 'Create a linux virtual machine'
- 搜索并选择 Ubuntu Server LTS
- 使用 Standard _D2s_v3 规格——在本课程期间，你的试用额度应该足以轻松覆盖它
- 确保认证方式选择 'SSH Public Key'，SSH 公钥来源选择 'generate new key pair'
- 暂时把 'allow selected ports' 保持为 'ssh (22)'
- 点击 'Review + Create'
- Azure 会生成并下载用于 SSH 登录该机器的私钥文件
- （Windows）双击它在 Windows 中打开，它会被添加到该机器的证书存储中
- （Mac OS X 和 Linux）运行命令 'sudo ssh-add -K /下载文件的路径'
- 注意：如果上面的命令对你不起作用，就试着不带 sudo 运行。如果遇到任何与权限相关的错误，先试一下 'chmod 400 文件名'。
- 使用 `ssh azureuser@公网IP` 连接到该机器

现在，为了把机器和所有端口完全暴露给互联网：

- 打开 <https://portal.azure.com/#home>
- 选择 'Virtual Machines'
- 选择你创建的虚拟机，并在设置窗格中选择 'Networking'
- 点击 'Inbound Port Rules'，再点 'Add inbound port rule'
- 把 'source port ranges' 和 'destination port ranges' 设为 '*'，把 'Source' 和 'Destination' 设为 'any'。确保协议设为 'any'，操作设为 'allow'。把优先级（priority）设为 '100'，并起一个合适的名称
- 点击 'Outbound port rules'，再点 'add outbound port rule'
- 把 'source port ranges' 和 'destination port ranges' 设为 '*'，把 'Source' 和 'Destination' 设为 'any'。确保协议设为 'any'，操作设为 'allow'。把优先级设为 '101'，并起一个合适的名称

这会开放所有端口和协议，允许从任何地方访问。虽然对生产服务器来说这可能不明智，但这正是我们这门课程想要的。

## 通过 SSH 远程访问

确保你的机器处于 'running' 状态（如果没有，点击 'start'），然后使用 'connect -> ssh' 下拉菜单并按照说明连接。

你将以 `azureuser` 用户身份登录。它已被加入 `adm` 和 `sudo` 组，在 Ubuntu 系统上，这使它有权读取各种日志——并在需要时通过 _sudo_ 命令“成为 root”。

## 你现在是一名系统管理员了

通过输入以下命令确认你可以执行管理任务：

```bash
sudo apt update
```

（通常这会提示你确认密码，但由于你使用的是公钥认证，系统未曾提示你设置密码——而且 Azure 已经把 `sudo` 配置为不对 `azureuser` 请求密码。）

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
