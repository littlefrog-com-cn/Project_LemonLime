<img src="pics/icon.png" align=right />

# Project_LemonLime (Beta)

为了 OI 比赛而生的基于 Lemon 的轻量评测系统

A tiny judging environment for OI contest based on Project_LemonPlus

**现已支持 Linux，Windows，以及 macOS**

|系统名称|打包状态|
|:--:|:--:|
|Windows|![Windows](https://github.com/iotang/Project_LemonLime/workflows/Windows/badge.svg)|
|Ubuntu|![Ubuntu](https://github.com/iotang/Project_LemonLime/workflows/Ubuntu/badge.svg)|
|macOS|![MacOS](https://github.com/iotang/Project_LemonLime/workflows/MacOS/badge.svg)|

已在这些系统测试：

|系统名称|版本号|位数|DE / WM|
|:--:|:--:|:--:|:--:|
|Windows|7|32, 64|Untitled|
|Windows|10|64|Untitled|
|Manjaro|18.1.5|64|KDE|
|Arch|2020-2-22|64|KDE|
|Ubuntu|18.04.4|64|GNOME 3|
|NOI Linux (Ubuntu) *|14.04|32|GNOME 2|
|Linux Mint|19.3|64|Cinnamon|
|Deepin|15.11|64|DDE|
|Debian|10.3.0|64|LXQt|
|Fedora|31-1.9|64|XFCE|
|openSUSE|Leap 15.1|64|iceWM|


# 特色

**Lemon 绿了！**

## 功能追加

- 题目类型支持：传统题，提交答案题，交互题（仅 C++），通信题。
   - 交互题支持详情
      - 交互库路径：交互使用的头文件。
      - 交互库名称：选手引用头文件的名称。
      - 接口实现路径：实现接口的源文件（grader.cpp）。
   - 通信题支持详情（测试阶段）
      - 源文件列表：选手的所有要写的程序。
      - 接口文件列表：所有要用到的接口文件。
- 统计：对比赛分数数据进行分析的栏目，还需要很多的更新。
- 整理文件：使所有的选手的子文件夹内外都有答案文件，并且删除大部分无用文件。支持在这之前备份文件。
- 帮助 > 指南
- 重新排列题目顺序的支持
- 窗口下方新增提示栏
- 移除了自定义测试
- 移除了多线程评测

## 评测改进

- 任意选手的任意题目评测
- 可以控制的最大重新评测次数
- Subtask Skip
- 子任务依赖
- 支持选择子文件夹还是非子文件夹
- 选手名单上的成绩将会有背景颜色，随着分数变化而变化。导出的 HTML 文件也有颜色。配色方案大体来自 IOI。
- 各种评测结果在评测时界面、结果查看界面和 HTML 也有了易于区分的不同的颜色。
- 默认的栈空间设置为和内存限制相同。

## 用户体验

- 支持高 DPI
- 自带的实数比较模式判断了 ``nan`` 和 ``inf``。来自某出题人的提醒
- 如果你在某个点得分了，那么在测试时的窗口会显示获得的分数、使用的时间和空间。
- 一键评测所有出现 找不到文件/编译问题 的记录
- 手动保存比赛、打开比赛目录（在 `文件` 菜单栏中）
- 重命名比赛
- 自动添加试题的时候每个点的分数不再是下取整(总分/数据点个数)。
- 减小了导出 HTM 的体积，并且给 HTML 添加了更多跳转。
- 默认空间限制和比较模式调整
- 图标和启动横幅
- 更友好的界面



# 构建

## 下载源码

### 下载的东西太大了？

`git clone` 的时候，使用 `--depth 1` 可以使下载下来的文件大小减少很多（因为默认情况下它会把所有历史记录全部下载下来）。

### 如果 Github 还是太慢…

你也许可以到 ``码云（Gitee）`` 去下载。

在很多地区，从 ``码云`` 下载的速度是从 ``Github`` 下载的速度的 100 倍。

[这个仓库在码云下的复制](https://gitee.com/iotang/Project_LemonLime)

## Windows

去 `Releases` 下载可执行文件就可以了。

当然如果你装有 Qt 5，也可以下载源码编译。

> **提示：**
> 
> 在很多地方，下载 Qt 的时间 + 安装 Qt 的时间 + 下载 LemonLime 源代码的时间 + 编译的时间 < 从 Github 上下载可执行文件的时间。
> 
> 并且由于作者很鸽而很少给 Windows 平台打包，为了总是使用最新版的 LemonLime，推荐用源代码编译。
>
> 下载 Qt 请考虑一个快速的国内镜像。

## Linux 

### Arch Linux 系

已在这些系统测试：

|系统名称|版本号|位数|DE / WM|
|:--:|:--:|:--:|:--:|
|Arch|2020-2-22|64|KDE|
|Manjaro|18.1.5|64|KDE|

```bash
## 迅速安装 ##
yay -S lemon-lime # 版本可能过旧
yay -S lemon-lime-git 
# 感谢 @ayalhw 的支持。

## 使用 qmake ##
sudo pacman -S gcc make qt5-base # 依赖环境
cd 源代码的目录
g++ watcher_unix.cpp -o watcher_unix -O2
qmake lemon.pro
make # 获得可执行文件 lemon

## 使用 QtCreator ##
sudo pacman -S qtcreator
```

### Debian | Ubuntu 系

已在这些系统测试：

|系统名称|版本号|位数|DE / WM|
|:--:|:--:|:--:|:--:|
|Ubuntu|18.04.4|64|GNOME 3|
|Linux Mint|19.3|64|Cinnamon|
|Deepin|15.11|64|DDE|
|Debian|10.3.0|64|LXQt|

```bash
## 使用 qmake ##
sudo apt install qt5-default build-essential # 依赖环境
cd 源代码的目录
g++ watcher_unix.cpp -o watcher_unix -O2
qmake lemon.pro
make # 获得可执行文件 lemon

## 使用 QtCreator ##
sudo apt install qtcreator
```

#### * NOI Linux

已在这些系统测试：

|系统名称|版本号|位数|DE / WM|
|:--:|:--:|:--:|:--:|
|NOI Linux (Ubuntu) *|14.04|32|GNOME 2|

NOI Linux 是 Ubuntu 14.04 的换皮，所以用 apt 安装的 Qt 版本只能到 5.2。

在 qmake 前你需要：
- 删除 `lemon.ui` 里面的 `<property name="tabBarAutoHide">...` 开始的 3 行。因为 Qt 5.2 里面还没有这个特性！
- 删除 `lemon.pro` 的 `unix:QMAKE_LFLAGS += -no-pie` 那一行。
- 把代码中所有 `asprintf` 换成 `sprintf`。

或者
- 在 Qt 官网上找一个更高版本（比如 5.9）的 Qt 安装。


*arbiter 退出了群聊。*

### Fedora 系

已在这些系统测试：

|系统名称|版本号|位数|DE / WM|
|:--:|:--:|:--:|:--:|
|Fedora|31-1.9|64|XFCE|

```bash
## 使用 qmake ##
sudo yum install g++ make qt5 # 依赖环境
cd 源代码的目录
g++ watcher_unix.cpp -o watcher_unix -O2
qmake-qt5 lemon.pro
make # 获得可执行文件 lemon
```

### openSUSE 系

已在这些系统测试：

|系统名称|版本号|位数|DE / WM|
|:--:|:--:|:--:|:--:|
|openSUSE|Leap 15.1|64|iceWM|

```bash
## 使用 QtCreator ##
sudo zypper install --type pattern devel_basis
sudo zypper install libqt5-creator
```

## macOS

在没有 macOS 机子的情况下写 macOS 支持是一件非常滑稽的事。

请使用 ``watcher_macos.cpp`` 编译 ``watcher_unix``，否则内存限制会出问题。

```bash
g++ watcher_macos.cpp -o watcher_unix -O2
```

