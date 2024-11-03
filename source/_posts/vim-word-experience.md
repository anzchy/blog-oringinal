---
title: 在微软 word 软件中实现 vim 的浏览体验
date: 2024-11-03 23:28:32
categories:
- 编程
- 自学
tags:
---

## 1、我为什么创建这个脚本

最近，我在学习麻省理工学院教授的一个课程： [Missing Semester of Your CS Education](https://missing.csail.mit.edu/)，这是面向非程序员的一门课（不需要编程），用于提升我们的计算机素养（computer literacy）——通常上编程课，老师默认学生都会这些技能，因而不教，但实际上我们绝大部分人都没有系统研究过这些东西。我发现 Vim 确实是程序员和文本编辑者的“瑞士军刀”（虽然我现在还不是一个真正的程序员，但在人工智能的帮助下，我正在逐步迈向这个目标）。

Vim 在Mac 终端中编辑代码时功能非常强大，你几乎不需要用鼠标（用了鼠标反而大大降低效率）。对于其他软件，比如浏览器应用程序、Visual Studio Code，开发者们都创造了优秀的工具或插件，使其具备类似 Vim 的按键绑定和使用体验。

**Chrome 和 Edge 软件**：`Vimium` 的 Chrome 扩展非常棒。

**Visual Studio Code**：`vim` 插件提供了与终端中相同的原生 Vim 体验。

**Google Doc**：我推荐一个 `Vim for Google Doc` 的付费 Chrome 插件，它真的很出色。

但对我来说，我在工作中经常使用 Microsoft Word 。而Microsoft 和 Vim 编辑器是不同的，因为它是一个富文本编辑器，你不能仅通过按某个 `i` 或 `v` 键来切换到 `插入` / `普通` / `命令行` / `可视` 模式。在 Microsoft Word 中，似乎只有 `插入` 模式。

庆幸的是，Word 有大量的键盘快捷键可以帮助我们在词、行、段落和页面之间导航，因而我想将一些类似 Vim 的体验（不可能将所有的功能体验都引入）带入到 Word。我直观的想法是寻找互联网上可用的解决方案，我询问了 ChatGPT 和 Google，但没有找到什么有用的东西，Libre Office 有一个插件可以实现类似的体验，但与 Word 的兼容性真的不太高。所以这就是我为什么需要从头开始，构建我自己的重映射脚本。

## 2、如何构建键盘映射

首先，我们需要在 Microsoft Word 中找到原始的键盘快捷键，你可以参考微软官网的 [Word 快捷键说明](https://support.microsoft.com/zh-cn/office/word-%E4%B8%AD%E7%9A%84%E9%94%AE%E7%9B%98%E5%BF%AB%E6%8D%B7%E6%96%B9%E5%BC%8F-95ef89dd-7142-4b50-afb2-f762f663ceb2#PickTab=macOS)，其中有大量的快捷键供我们使用，你会发现所有的导航都是通过组合 `上/下/左/右箭头` + `Control/Option/Command` 键来实现的。但这并不是特别友好，特别是对程序员来说。

正如 [vimbook](https://www.truth.sk/vim/vimbook-OPL.pdf) 第 7 页所说：

> 返回到命令模式后，你可以使用以下键进行移动：h（左），j（下），k（上），l（右）。起初，这些命令似乎是随意选择的。毕竟，谁会想到用 l 来表示右呢？但实际上，这些选择是有很好的理由的：移动光标是你在编辑器中最常做的事情，而这些键正好位于你右手的主页行。换句话说，这些命令被放置在你可以最快输入的地方。
>
> 注意：
>
> 你也可以使用箭头键移动光标。但如果这样做，你的编辑速度会大大降低——因为按箭头键时，你必须把手从文本键移动到箭头键。考虑到你可能每小时要这样做数百次，这会消耗大量时间。如果你想高效编辑，请使用 h、j、k 和 l。

因此，一个好的策略是找出一种方法，将四个箭头键重新映射到 h、j、k 和 l。以下是重映射表。

| 操作                   | 当前键盘快捷键             | 新的映射快捷键 |
| ---------------------- | -------------------------- | -------------- |
| 左移一个字符           | left arrow                 | control+h      |
| 右移一个字符           | right arrow                | control+l      |
| 上移一行               | up arrow                   | control+k      |
| 下移一行               | down arrow                 | control+j      |
| 左移一个字词           | option + left arrow        | option+h       |
| 右移一个字词           | option + right arrow       | option+l       |
| 上移一个段落           | command + up arrow         | command+k      |
| 下移一个段落           | command + down arrow       | command+j      |
| 将光标移至当前行的开头 | command + left arrow       | command+h      |
| 将光标移至当前行的末尾 | command + right arrow      | command+l      |
| 将光标移动到文档的开头 | command + Fn + left arrow  | command+6      |
| 将光标移动到文档的结尾 | command + Fn + right arrow | command+4      |
| 向上滚动一个屏幕       | Fn + up arrow              | option+k       |
| 向下滚动一个屏幕       | Fn + down arrow            | option+j       |

我的重映射逻辑如下：

- 使用 `control + h/j/k/l` 来导航 `一个字符`（左和右）或 `一行`（上下）
- 使用 `command + h/j/k/l` 键来导航 `开头/结尾`（左右）或 `一个段落`（上下）
- 使用 `option + h/j/k/l` 键来导航 `一个字词`（左右）或 `一屏`（上下）

通过反复试验，找到一个适合运行脚本的应用程序是 Karabiner-Elements（我使用的是 15.3.0 版本），我给 ChatGPT 写了一个提示，最终它为我写了一个可用的脚本。

以上是我的重映射策略逻辑，当然你可以根据自己的想法进行修改。

## 3、如何使用这个脚本

1. 首先，下载[百度网盘链接](https://pan.baidu.com/s/1AkvLgygM9rmxDobhc1CwuA?pwd=s9dj)（提取码：s9dj）中的 `word-remapping-karabiner.json` 文件，用 Sublime Text 或 Notepad++ 打开它。

2. 下载并打开 Karabiner-Elements 应用程序：

- 在 Karabiner-Elements 窗口中，转到“复杂修改”选项卡。
- 点击 `add your own rule`。将 `word-remapping-karabiner.json` 的全部内容复制到编辑器中。
- 保存你的脚本，如果没有出现错误，那么应用程序会立即激活重映射。

## 4、温馨提示：

1. 如果应用程序弹窗说你的驱动程序过时，你需要重新启动你的 Mac。

2. 我没有在 Windows 系统上测试过。但相同的逻辑也适用。
