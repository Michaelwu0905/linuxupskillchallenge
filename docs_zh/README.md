<div align="center" width="100%">
  <h1>Linux Upskill Challenge（Linux 技能提升挑战）</h1>
  <h3>Linux 服务器管理入门</h3>
  <a href="https://linuxupskillchallenge.org/"><img alt="Website" src="https://img.shields.io/website?url=https%3A%2F%2Flinuxupskillchallenge.org&style=for-the-badge&label=LinuxUpskillChallenge.org"></a>
  <a href="https://programming.dev/c/linuxupskillchallenge"><img alt="Lemmy subscribers" src="https://img.shields.io/lemmy/linuxupskillchallenge%40programming.dev?style=for-the-badge&logo=lemmy&logoColor=white&label=lemmy"></a>
  <a href="https://www.reddit.com/r/linuxupskillchallenge/"><img alt="Subreddit subscribers" src="https://img.shields.io/reddit/subreddit-subscribers/linuxupskillchallenge?style=for-the-badge&logo=reddit&logoColor=white&label=reddit"></a>
  <a href="https://discord.gg/linux-upskill-challenge-682046666928685068"><img alt="Discord" src="https://img.shields.io/discord/682046666928685068?label=discord&logo=discord&logoColor=white&style=for-the-badge" /></a></br>
  <img alt="GitHub last commit (branch)" src="https://img.shields.io/github/last-commit/livialima/linuxupskillchallenge/master?style=for-the-badge&logo=github&logoColor=white">
  <img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/livialima/linuxupskillchallenge?style=for-the-badge">
  <img alt="GitHub watchers" src="https://img.shields.io/github/watchers/livialima/linuxupskillchallenge?style=for-the-badge">
  <img alt="GitHub forks" src="https://img.shields.io/github/forks/livialima/linuxupskillchallenge?style=for-the-badge">
  <a href="https://github.com/sponsors/livialima"><img alt="GitHub Sponsors" src="https://img.shields.io/github/sponsors/livialima?style=for-the-badge&logo=githubsponsors"></a>
</div>

> 这是 [Linux Upskill Challenge](https://github.com/livialima/linuxupskillchallenge) 的中文翻译版本，英文原文位于仓库的 `docs/` 目录。所有链接、命令和代码示例均保留原文；只有叙述性文字被翻译成中文。

**Linux Upskill Challenge 是免费且开源的——而且永远如此。**
如果它帮到了你，而你也愿意支持它的维护工作，可以在这里支持：[捐赠](https://www.buymeacoffee.com/livialima) 或 [赞助](https://github.com/sponsors/livialima)。

所有核心学习材料全年可访问。无需订阅、无需注册——除了你的时间，不花你一分钱！

*如果你发现任何错别字或“失效链接”，只需[提一个 issue](https://github.com/livialima/linuxupskillchallenge/issues/new/choose)。*

* [课程网站](https://LinuxUpskillChallenge.org)
* [完整课程源码](https://github.com/livialima/linuxupskillchallenge)
* [配套视频播放列表](https://www.youtube.com/@livia2lima/search?query=linuxupskillchallenge)
* [Lemmy 上的每月课程](https://programming.dev/c/linuxupskillchallenge)
* [Reddit 上的每月课程](https://www.reddit.com/r/linuxupskillchallenge/)
* [Discord 聊天](https://discord.gg/linux-upskill-challenge-682046666928685068)

## 请先读这个！
[运作方式与常见问题](how-this-works.md)

## 目录

* [第 0 天](00.md) - **创建你自己的服务器**：如何在 AWS、Azure、Google Cloud、Digital Ocean 和本地服务器上搭建你的实验环境
* [第 1 天](01.md) - **了解你的服务器**：从 `ssh` 登录开始，以及一些简单命令，例如 `ls`、`uptime`、`free`、`df -h`、`uname -a`。进阶内容包括使用公钥实现免密码登录以及 `ssh` 配置文件。
* [第 2 天](02.md) - **基础导航**：基本导航、“man”手册页、文件层级结构
* [第 3 天](03.md) - **权力之旅！**：使用 `sudo`、`uptime`、时区、修改主机名
* [第 4 天](04.md) - **安装软件、探索文件结构**：使用 'apt' 查找和安装软件。用 `mc` 探索文件系统。查看 `/etc/passwd`、`/etc/ssh/sshd_config` 和 `/var/log/auth.log` 的内容
* [第 5 天](05.md) - **More or less……**：使用 `more`、`less` 并在其中导航。点文件、历史记录、Tab 补全，以及使用 `nano` 文本编辑器
* [第 6 天](06.md) - **用 “vim” 编辑**：学习 `vim` 的最小必要知识，也通过 `vimtutor` 来学
* [第 7 天](07.md) - **服务器及其服务**：安装 Apache2、停止与启动、修改内容、阅读日志
* [第 8 天](08.md) - **大名鼎鼎的 “grep” 与其他文本处理器**：动手实践 `grep`、`cat`、`more`、`less`、`cut`、`awk`、`tail` 等文本工具——当然还有管道。（另外也向 `awk` 和 `sed` 打个招呼）
* [第 9 天](09.md) - **深入网络**：用 `ss` 查看开放端口，顺带提一下 `netstat`，安装 `nmap` 并测试。安装 `ufw`、配置、启用并测试等。讨论作为系统管理员的安全责任。
* [第 10 天](10.md) - **任务调度**：涵盖 `cron`、`at` 和 systemd 定时器
* [第 11 天](11.md) - **查找东西……**：用 `locate`、`find`、`grep`、`which` 查找
* [第 12 天](12.md) - **传输文件**：SFTP 技术、客户端，以及上传和下载
* [第 13 天](13.md) - **用户与组**：使用 `adduser`、`visudo` 设置一个受限制的“助手”账号来管理我们的主机
* [第 14 天](14.md) - **谁有权限？**：权限、用户、组（扩展部分涉及 ACL 和 SELinux）
* [第 15 天](15.md) - **深入软件仓库……**：更详细地了解仓库、如何启用 “Multiverse”、PPA 在 Ubuntu 中的作用、从它们中启用并安装软件
* [第 16 天](16.md) - **归档与压缩**：理解并使用 `tar` 和 `gzip`
* [第 17 天](17.md) - **从源码构建**：从源码安装。相关讨论，使用 `wget` 获取 tarball，用 `tar` 解包，然后 configure、make 和 install。讨论安全与维护问题。
* [第 18 天](18.md) - **日志、监控与故障排查**：日志管理与轮转，`logrotate`
* [第 19 天](19.md) - **Inode、符号链接与其他快捷方式**：Inode、硬链接、符号链接与 `stat`
* [第 20 天](20.md) - **脚本编程**：理解 Linux 中脚本如何工作、shebang、权限和 `$PATH`。基于我们一直在做的日志过滤写几个简单的示例脚本。还有供进一步探索的资源。
* [第 21 天](21.md) - **接下来做什么？**：以一些建议为课程收尾。

**感谢你成为这个社区的一员，Linux 玩得开心！**
