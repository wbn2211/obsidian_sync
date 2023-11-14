# 前言

> 我使用的系统是 Archlinux ，所以在一些系统的配置问题上会与 steam deck 不同，但是 steam deck 所搭载的 steamos 是基于 arch 的，所以大体是没有区别的（）

>  （叠个甲）本文主要侧重于使用 archlinux 的 hxdm，而且我也是新人玩家，对于 arch 的理解不是很深，文章中难免有问题

**本文更多的对自己的经验总结，不是教程！不是教程！不是教程！**

我最开始使用的 `LINUX` 是 Manjaro ，这个发行版也是基于 Arch 的。在从 Manjaro 换成 Archlinux 的这个过程中我经历了许多，这篇文章更多的是我在这个过程中学到的使用 Archlinux 这个系统过程中遇到问题的解决办法，可能对大家遇到的问题时有所启发

图 0.1 自己写文章时的 Archlinux 版本

---

# 一、对于 Archlinux 我是什么看法

首先我要表明我的立场，我非常不推荐，尤其是游戏玩家使用**一切**非 Windows 系统。

## 其一，从市场份额来看

截至2023年6月，全球桌面操作系统市场中， Windows 市场占有率为 **70.95%** ，远高于其他操作系统，位居第二名的是苹果公司 OS X ，其市占率为 16.5% ， Linux 、 ChromeOS 占比均为 2.8%。让一个游戏公司，为了 2.8% 的份额中一小部分的游戏玩家去更改、适配自己的游戏，这是不现实的。（说真的，这个 Unknown 是个啥啊，自己写的操作系统？）

![[StatCounter-os_combined-ww-monthly-202206-202306-bar.png]]

## 其二，从日常体验来看

不可否认，在我使用 Archlinux 的这半年里的体验，是要优于其他 linux 发行版的。在 Archlinux 下的 pacman 包管理器中收录的软件有很多，如果 pacman 中没有，也有 AUR （Arch 用户仓库）进行补充。办公使用 WPS 完全没有问题，看视频完全没问题， **但是！** 这是有前提的，前提是你花费很多的时间去查资料，去分析自己遇到的问题，把自己遇到的问题解构处理最终你才能获得一个相对较好的体验

## 其三，从游戏玩家来看

从 steam 发布 proton 之后， linux 的游戏环境得到了极大地改善，这点我们从 [ProtonDB | Gaming know-how from the Linux and Steam Deck community](https://www.protondb.com/) 便可以看出一二。但是从