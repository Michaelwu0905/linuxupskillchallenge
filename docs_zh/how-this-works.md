# 你大概应该先读这个：运作方式与常见问题

## 资源

* [课程网站](https://LinuxUpskillChallenge.org)
* [完整课程源码](https://github.com/livialima/linuxupskillchallenge)
* [视频课程与配套视频](https://www.youtube.com/@livia2lima/search?query=linuxupskillchallenge)
* [Lemmy 上的每月课程](https://programming.dev/c/linuxupskillchallenge)
* [Reddit 上的每月课程](https://www.reddit.com/r/linuxupskillchallenge/)
* [Discord 聊天](https://discord.gg/linux-upskill-challenge-682046666928685068)

## 运作方式

### 一句话概括

* 完全免费且开源
* 专注于实用技能
* 高度动手实践，且完全在命令行中完成
* 每个月的第一个星期一开始
* 持续 20 个工作日（周一至周五）
* 经常给出精心挑选的外部链接，对当天主题做进一步拓展
* 比 RHEL 或 Linux Foundation 的培训“正式”程度低得多

### 要求

* 在一个月内每节课投入 1–2 小时，但也可以按自己的节奏进行
* 一台基于云的 Ubuntu Linux 服务器（推荐），或者有办法创建/搭建你自己的本地 Linux 服务器。_- 如何搭建的完整说明在 “Day 0” 课程里。_
* 基本的计算机操作能力——不需要任何 Linux 前置知识，但你应该能够比较自如地操作自己的 Windows/Mac 机器，并懂得如何排查自己系统的问题。_- 这是一门只聚焦 Linux 的课程；访问那台 Linux 服务器所需的 Windows/Mac 设置说明虽有提供，但它们不是重点。_

## 常见问题解答 - FAQ

### 这门课程适合我吗？

这门课程主要面向两类人群：

1. 希望在行业中从事 Linux 相关工作的 Linux 用户，例如初级 Linux 系统管理员、DevOps 相关工作等，以及
2. 希望扩展知识、能够上手 Linux 服务器的 Windows 服务器管理员。

不过，还有很多其他人也很愉快地使用这门课程来**提升自己的 Linux 命令行技能**，或者**第一次学习 Linux**——这当然也完全没问题。

### 学完这门课我能通过 LPIC/RHCA/LFCS/Linux+ 认证吗？

**不能！这不是任何 Linux 认证考试的备考课程。** 它当然可以帮到你，但如果你志在拿证，请去参考更专门的认证培训。

### 我需要在哪里注册吗，还是只要每天读帖子跟着做就行？

不需要注册。跟着做并分享你的经验即可。

### 完成挑战后我会拿到证书吗？

目前没有证书。不过如果你愿意，可以在 [Lemmy](https://programming.dev/c/linuxupskillchallenge)、[Reddit](https://www.reddit.com/r/linuxupskillchallenge/) 或 [Discord](https://discord.gg/linux-upskill-challenge-682046666928685068) 上炫耀一番。

### 什么时候开始？

课程总是在**每个月的第一个星期一**开始。这门课程的一个关键特色是：材料被拆成 20 节小课，每个工作日一节，每月循环。

### 需要多长时间？我应该投入多少小时？

取决于你的经验和投入程度，预计每节课需要 1–2 小时。最初几天相当基础，可能只需几分钟，但通常会有一些 “Extension”（扩展）内容来增加一点难度。

### 我刚知道这个挑战，现在已经到第 X 天了。我该等下个月再开始吗？

只要你想等就等。这些材料[全年都可获取](https://github.com/livialima/linuxupskillchallenge)，所以如果你愿意，完全可以自己掌握节奏。

### 我真的需要一台云端服务器吗？

是的，如果你属于目标人群（见上文），那你绝对应该用云端服务器。这样一台服务器非常遥远，并且对整个互联网开放、随时可能被攻击，这种“真实感”很重要。学习如何搭建这样一台 VPS 对任何系统管理员来说也是一项实用技能。

**新功能！** 现在你可以跳过这些，直接使用我们的 [Killercoda 场景](https://killercoda.com/linux-upskill-challenge)。请注意这仍处于测试阶段，可能存在一些限制。

在 “Day 0” 课程里有针对几家服务商搭建合适服务器的说明。当然你也可以使用其他服务商，但请确保使用 Ubuntu LTS（最好是较新的版本），并使用公钥认证或者一个_长、强、唯一_的密码（我们也有相关说明）。

当然，你完全可以使用本地虚拟机、树莓派，甚至只用 WSL——这些都能很好地完成课程材料。只要记住你会错过什么就行。

### 但如果我没有信用卡（或者不想用信用卡）来搭建 AWS/Azure/GCP 服务器怎么办？

请阅读 [Day 0 - 创建你自己的本地服务器](00-Local-Server.md)。还有其他云服务商选项和不同的付款方式。但如果这些都不适合你，那就试着创建自己的本地虚拟机。

### 但如果我不想用云服务商呢？我家里有服务器/虚拟机。

那你就用自己的服务器/虚拟机。

### 你为什么非要推荐租用在线云服务器？！为什么不把虚拟机方案作为首选？！（也就是：这门课因为这个决定就是错的/不好的）

兄弟，冷静。如果这个要求让你如此反感，那这门课对你来说可能有点太基础了。跳过吧。

但如果你真的想知道背后的逻辑，也请考虑三件事：

1. 人们在本地资源上可能有各种限制。包括能否不受限制地使用个人电脑去安装 VirtualBox、硬件性能是否足以良好地运行虚拟化，甚至是否有电脑可用。一台非常轻量的云端服务器让你可以从任何访客设备（包括智能手机）上完成这个挑战。很多学生有 Azure 账号，可以用学校的电脑来访问它。大多数 VPS 提供商都会在新用户的前 1–2 个月提供免费虚拟机。使用云确实有风险，是的，但我们努力在解决这些风险的同时，不切断需要这个选项的人的路径。
2. 每家云服务商都有自己的文档、支持和足够大的用户群，能够回答新手的大部分问题。它们足够流行，有数百个 YouTube 视频和其他材料来讲解最基础的搭建问题，而且很多内容都被设计得简单易懂。而你自己搭建本地服务器或虚拟机时，情况并非如此。社区是存在的，是的，但文档通常更干巴巴，也更小众一些。
3. 如果你想获得完整的系统管理员体验，你终归要在远程服务器上工作。这就是事实。你可以试着在本地网络安全的高墙内，用你那台安全的小虚拟机来模拟这种感觉，但这里推荐的服务商有足够多的兜底机制，让你可以随便折腾虚拟机而不至于一夜之间烧掉额度。那些“云账单恐怖故事”通常涉及的都不是本挑战中涵盖的服务/产品。这里不是关键任务。不用的时候你随时可以把虚拟机关掉。

**太长不看（TL;DR）**：这是一门聚焦 Linux 的课程。花更多时间去争论_在哪里运行_的细节，而不是_如何使用_，偏离了这门课程的目的。[Day 0](00.md) 就是为了在这些最初的步骤中指导你，而它永远不会是完整的，所以请自行斟酌使用。

### 为什么用 Ubuntu，我可以用其他发行版吗？

这些笔记假定使用的是 Ubuntu Server LTS（最新版本），把其他发行版的说明/差异都包含进来会很混乱（至少目前如此）。如果你用 Debian 或其他基于 Debian 的发行版（Mint、Pop!OS、Kali），差别很小甚至没有，因为它们的结构相同。

但如果你选择基于 RedHat 的发行版（Fedora、CentOS、AlmaLinux）或 Arch、Gentoo、OpenSUSE 之类的发行版，那么你就得自己理解和应对各种差异（例如 apt 与 yum 与 pacman）。

如果这些名字对你来说毫无意义，那你还不该去挑发行版。先去读 [Linux Journey](https://linuxjourney.com/lesson/linux-history) 的第一课吧。

### 我已经在用[我自己喜欢的 Linux 发行版]了，我该如何参与？

大多数课程使用的命令其实并不限于 Ubuntu。所以你仍然可以用自己的发行版从挑战中受益，也可以用自己的 Linux 经验去回答别人的问题，从而做出贡献。

### 不用的时候我应该停止（stop）还是终止（terminate）我的服务器？

如果使用免费套餐的 VPS，这门课程的负载不会超过任何阈值。你可以在挑战期间让它一直运行，但最好盯着点（也就是：别忘了它，否则服务商就会开始收费）。

### 我注意到有内核更新，但没人说要重启。

那就重启它。这是少数几个你需要重启服务器的场合之一，放手去做吧。
命令是 `sudo reboot now`

### 我还有问题/疑问！我该怎么办？！

欢迎在 [Lemmy](https://programming.dev/c/linuxupskillchallenge)、[Reddit](https://www.reddit.com/r/linuxupskillchallenge) 提问或留言，或者到 [Discord 服务器](https://discord.gg/linux-upskill-challenge-682046666928685068) 聊天。

如果你有意愿、也有条件（也就是有一个 GitHub 账号）为材料做贡献，可以直接向源码仓库[提交 issue](https://github.com/livialima/linuxupskillchallenge/issues/new/choose)。

## 致谢

了不起的 [Steve Brorens](https://snori74.blogspot.com/2020/06/succession-planning-for.html) 是 Linux Upskill Challenge 的创始人和总设计师。这过去是一门付费课程，但自 2020 年起，由于他的慷慨，它变得免费且完全开源。遗憾的是，[他已去世](https://www.reddit.com/r/linuxupskillchallenge/comments/mki3uw/rest_in_peace_snori74/)，但在此之前他确保了课程在他离开后仍能继续运行。
我们想念你，snori。

目前由 [Livia Lima](https://bio.link/livialima) 维护这些材料。可以在 [Mastodon](https://fosstodon.org/@livialima) 或 [LinkedIn](https://www.linkedin.com/in/livialima/) 上向她致意。
