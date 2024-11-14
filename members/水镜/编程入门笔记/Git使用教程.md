# **简介**
本文主要内容：  
1.介绍Git的概念  
2.详细演示Git环境的配置   
3.列出Git的常用命令  
4.在一定程度上演示如何在VS Code上使用Git管理GitHub上的仓库  
Git官网：[https://git-scm.com/](https://git-scm.com/)  
GitHub官网：[https://github.com/](https://github.com/)  
VS Code官网：[https://code.visualstudio.com/](https://code.visualstudio.com/)

---

# **一.Git的概述**
---
Git 是一个**分布式版本控制**系统，用于管理项目中的代码变化，特别适合多人协作开发。它的主要功能包括：

1. **版本控制**：Git 可以记录代码的每一次变动，使你可以查看、比较并恢复到之前的任意版本。
    
2. **分支和合并**：Git 允许创建分支以开发不同的功能或修复问题。分支上的改动可以独立进行，最后再将它们合并到主分支。
    
3. **分布式**：与传统的版本控制系统不同，Git 是分布式的。每个开发者都有完整的项目历史，可以离线进行代码管理和提交。
    
4. **协作开发**：Git 很适合团队合作，支持多人并行开发。当开发者提交代码后，可以通过 pull request 合并到主项目中，确保代码的连续性和质量。
  
## 1.Git的核心概念
- **Repository (仓库)**：存储项目的文件和其历史记录的地方。可以是本地仓库或远程仓库（如 GitHub 上的仓库）。
- **Commit (提交)**：一次代码变动的快照，包括改动的具体内容和提交说明。
- **Branch (分支)**：并行开发的通道。每个分支都是代码历史的独立线条，可以独立于其他分支工作。
- **Merge (合并)**：将一个分支上的改动合并到另一个分支。
- **Pull (拉取)**：从远程仓库获取最新的更改并合并到本地分支。
- **Push (推送)**：将本地仓库的更改上传到远程仓库。

## 2.Git的常用命令
- git init：初始化一个新的 Git 仓库。
- git clone：克隆远程仓库到本地。
- git status：查看当前工作区的状态（有哪些改动）。
- git add：将改动添加到暂存区。
- git commit -m "消息"：提交暂存区的改动，并添加描述信息。
- git push：将本地提交推送到远程仓库。
- git pull：从远程仓库拉取更新并合并到本地分支。
- git branch：查看所有分支，或创建、删除分支。
- git checkout：切换到另一个分支。  
通过 Git，开发者能够更好地管理代码版本，尤其是在复杂项目中，它可以极大地提高效率并减少冲突。

---

# **二.配置Git环境**
---
## 1.下载Git
网址：[https://git-scm.com/downloads](https://git-scm.com/downloads)
![](/images/git-images/git.1.png)
![](/images/git-images/git.2.png)

---

## 2.安装Git
安装过程有**许多**步骤，**一般来说**全部默认即可，一路**next**直到**install**结束  
但是可以选择一下使用哪个**编辑器**  
下面的图是对安装过程各个步骤的解释  
1.可自选**路径**
![](/images/git-images/git.3.png)
2.图中标注了选项的**含义**
![](/images/git-images/git.4.png)
3.这个页面是询问是否希望在Windows的开始菜单，创建一个名为“Git”的文件夹，存放Git的快捷方式
![](/images/git-images/git.5.png)

### 2.1.选择编辑器
**4.这里需要选择一个默认编辑器  
注意：不是给你下载选的编辑器，只是告诉Git需要文本编辑时默认打开哪个  
不论你选择vim还是VS Code作为默认编辑器，都需要自己下载  
一般来说Git会内置一个vim编辑器，不过功能很少  
我已经下载了VS Code编辑器，之后的演示基本都在VS Code上进行  
VS Code编辑器使用Git主要用VS Code打开文件夹，进入资源管理器操作，当然也可终端使用命令**  
~~至于Vim编辑器，我没用过并不怎么清楚~~

### 2.2.Vim编辑器和VS Code编辑器对比
#### 1. Vim 编辑器：
- **特点**：
    
    - **轻量级**：Vim 是一个非常轻量级的文本编辑器，速度快且占用资源少。
    - **命令行界面**：运行在终端中，非常适合那些喜欢使用键盘操作的人。
    - **键盘驱动**：Vim 的操作主要依赖于快捷键，不使用鼠标。这使得它在熟练使用后非常高效，但初学者需要一定的学习成本。
    - **跨平台**：可以在任何系统上使用，包括 Windows、Linux、macOS。
  
- **适用人群**：
    
    - 熟悉命令行操作，喜欢使用键盘而不依赖鼠标的用户。
    - 需要快速轻量的编辑器来编辑简单的文件（如 Git 提交消息）。

- **适合场景**：
    
    - 如果你在终端环境下工作较多，并且已经习惯或愿意学习 Vim 的快捷键，Vim 是一个非常高效的工具。
    - 你只需要一个简洁、快速的编辑器来修改 Git 的提交信息或进行简单的代码编辑。
  
#### 2.VS Code编辑器：
- **特点**：
    
    - **图形界面**：VS Code 是一个现代化的图形化编辑器，提供了丰富的界面和强大的功能。
    - **插件丰富**：VS Code 有大量的插件可供安装，支持多种编程语言、Git 集成、调试工具等。
    - **直观易用**：对于初学者和熟悉图形界面操作的用户，VS Code 更加直观，使用起来更方便。
    - **集成 Git**：VS Code 有内置的 Git 支持，提供了友好的界面来处理 Git 操作（如提交、查看历史、冲突解决等）。
  
- **适用人群**：
    
    - 喜欢使用功能丰富的 IDE 或 GUI 编辑器的用户。
    - 需要更强大的代码编辑、调试和扩展功能。
    - 喜欢鼠标操作或者还不太熟悉命令行操作的用户。

- **适合场景**：
    
    - 你更注重编程效率，喜欢通过扩展插件和图形化界面处理 Git。
    - 你需要更多的工具支持，如代码自动补全、调试、扩展库等功能。

#### **3.编辑器总结**
 - 如果你**熟悉命令行**，需要一个轻量级、高效的编辑器，**Vim** 是不错的选择。
 - 如果你更喜欢**图形化界面**，希望使用一个功能丰富、易于扩展的编辑器，**VS Code** 可能更适合你，尤其是如果你在 Git 操作中经常需要进行代码修改或调试。  
   
这是默认的Vim编辑器
![](/images/git-images/git.6.png)
**我选择使用VS Code编辑器，根据你的需求选择**
![](/images/git-images/git.7.png)
5.
![](/images/git-images/git.8.png)
6.
![](/images/git-images/git.9.png)

### 2.3.SSH介绍
SSH（**Secure Shell**）是一种用于通过不安全的网络安全登录到远程计算机的协议。它主要用于在两个系统之间建立加密的连接，以便安全地执行命令行、传输文件和进行系统管理等操作。SSH 通过加密技术，保证了传输的数据不被窃听或篡改，通常用于服务器管理和远程开发工作。

#### SSH 的主要功能：
- **远程登录**：可以在本地计算机上通过终端控制远程服务器。
- **文件传输**：通过 scp 或 sftp 等方式在本地和远程机器之间安全地传输文件。
- **端口转发**：通过 SSH 隧道实现的端口转发功能，可以把本地端口重定向到远程机器上的端口，用于保护其他通信协议的安全。

#### OpenSSH 是什么？
**OpenSSH** 是 SSH 协议的一个开源实现，广泛应用于各类操作系统中（特别是类 Unix 系统，如 Linux 和 macOS）。它不仅支持 SSH 协议本身，还包括一些相关的工具，例如：

- ssh：用于远程登录。
- scp 和 sftp：用于安全地传输文件。
- ssh-agent 和 ssh-add：用于管理 SSH 密钥和自动登录。
- sshd：SSH 服务器程序，允许远程登录到本地系统。

OpenSSH 是目前最常用的 SSH 实现之一，由于其开源和安全性，它在服务器管理和远程开发中被广泛使用。

在你的 Git 安装过程中，选择使用 **OpenSSH** 意味着 Git 将使用 SSH 协议来执行安全的远程操作，比如在 Git 仓库中通过 SSH 进行拉取或推送操作。

图中有两个选择：
1. **Use bundled OpenSSH**（使用 Git 附带的 OpenSSH）：这意味着 Git 会使用 Git 自带的 ssh.exe，也就是你不需要单独安装 SSH 程序，直接使用 Git 包含的版本。
    
2. **Use external OpenSSH**（使用外部的 OpenSSH）：这选项意味着你已经在系统中安装了 OpenSSH，Git 将使用系统中已有的 ssh.exe，而不是安装 Git 自己的版本。这个选择适用于你已经有外部的 OpenSSH 安装并且想用系统默认的 SSH 配置。
一般选择**默认**即可
  
7.![](/images/git-images/git.10.png)8.![](/images/git-images/git.11.png)
9.![](/images/git-images/git.12.png)10.![](/images/git-images/git.14.png)
11.![](/images/git-images/git.15.png)12.![](/images/git-images/git.16.png)
13.
![](/images/git-images/git.13.png)
14.
![](/images/git-images/git.18.png)
15..**安装完成**![](/images/git-images/git.19.png)

---

## 3.设置用户签名
**Git首次安装必须设置用户签名，否则无法提交代码**  
鼠标**右键**点击桌面，打开**Open Git Bash Here**  
（**没看到就是在更多选项**）
![](/images/git-images/git.20.png)
可以用命令查看版本：
```
git --version
```
如果觉得字体小，可以**Ctrl+鼠标滚轮**放大
```
git config --global user.name 
git config --global user.email 
```
(用户名和邮箱任意设置即可，不会去查验邮箱是否真实)
![](/images/git-images/git.21.png)
上述操作后，C盘的用户的用户下会生成一个.gitconfig文件，里面有你设置的用户名和邮箱
![](/images/git-images/git.22.png)

---

# **三.编辑器常用命令**

---

## Vim 编辑器常用命令
### 1. 模式切换

- i：进入插入模式（开始编辑文本）。
- Esc：退出插入模式，回到普通模式。
- :q：退出 Vim。
- :w：保存文件。
- :wq：保存并退出。
- :q!：强制退出（不保存修改）。
- :x：保存并退出（与 :wq 类似）。

### 2. 文件操作

- vim filename：打开文件，若文件不存在则新建文件。
- :e filename：打开其他文件。
- :w filename：另存为指定文件名。

### 3. 移动光标

- h：向左移动一个字符。
- j：向下移动一行。
- k：向上移动一行。
- l：向右移动一个字符。
- gg：移动到文件开头。
- G：移动到文件末尾。
- w：移动到下一个单词的开头。
- b：移动到上一个单词的开头。

### 4. 文本编辑

- x：删除光标下的字符。
- dd：删除当前行。
- yy：复制当前行。
- p：粘贴。
- u：撤销上一步操作。
- Ctrl + r：重做上一步操作。

### 5. 查找和替换

- /keyword：查找 keyword。
- n：跳到下一个匹配项。
- N：跳到上一个匹配项。
- :%s/old/new/g：全局替换 old 为 new。
- :n,m s/old/new/g：从第 n 行到第 m 行替换 old 为 new。

---

## VS Code 编辑器常用命令

### 1. 基础命令

- Ctrl + P / Cmd + P：快速打开文件（输入文件名）。
- Ctrl + N / Cmd + N：新建文件。
- Ctrl + S / Cmd + S：保存文件。
- Ctrl + Shift + S / Cmd + Shift + S：另存为。
- Ctrl + W / Cmd + W：关闭当前文件。
- Ctrl + Shift + P / Cmd + Shift + P：打开命令面板。

### 2. 导航

- Ctrl + Tab / Cmd + Tab：切换打开的文件。
- Ctrl + G / Cmd + G：跳转到指定行号。
- Ctrl + Shift + O / Cmd + Shift + O：按符号（函数/类名）跳转。
- Ctrl + T / Cmd + T：搜索并跳转到符号。

### 3. 编辑

- Ctrl + Z / Cmd + Z：撤销。
- Ctrl + Shift + Z / Cmd + Shift + Z：重做。
- Ctrl + X / Cmd + X：剪切。
- Ctrl + C / Cmd + C：复制。
- Ctrl + V / Cmd + V：粘贴。
- Ctrl + / / Cmd + /：注释/取消注释当前行。
- Alt + Up / Option + Up：上移当前行。
- Alt + Down / Option + Down：下移当前行。

### 4. 多光标编辑

- Alt + Click / Option + Click：添加光标。
- Ctrl + Alt + Down / Cmd + Option + Down：向下添加光标。
- Ctrl + Alt + Up / Cmd + Option + Up：向上添加光标。

### 5. 代码格式化和调试

- Shift + Alt + F / Shift + Option + F：格式化代码。
- F5：启动/继续调试。
- F9：设置/取消断点。
- F10：逐过程调试。
- F11：逐语句调试。

### 6. 搜索和替换

- Ctrl + F / Cmd + F：查找。
- Ctrl + H / Cmd + H：替换。
- Ctrl + Shift + F / Cmd + Shift + F：全局搜索。

## 总结

- **Vim** 的命令主要围绕键盘快捷键，操作高效但学习曲线较陡。
- **VS Code** 则更偏向图形化操作，并提供命令面板，既支持鼠标操作也支持丰富的键盘快捷键，更加适合现代开发者的多任务操作。

---

# **四.Git常用命令**

---

## 1. 基本 Git 操作

### 1.1. 初始化仓库

- git init：初始化一个新的 Git 仓库。

### 1.2. 克隆仓库

- git clone [url]：从远程仓库克隆项目。

### 1.3. 查看状态

- git status：查看当前文件状态，包括未跟踪的文件、修改文件、暂存文件等。

### 1.4. 添加文件到暂存区

- git add [filename]：将单个文件添加到暂存区。
- git add .：将当前目录下所有更改添加到暂存区。

### 1.5. 提交更改

- git commit -m "[message]"：提交暂存区中的更改，并附加提交信息。
- git commit -a -m "[message]"：将已跟踪文件的更改自动暂存并提交（不包括新文件）。

### 1.6. 查看提交历史

- git log：查看提交历史。
- git log --oneline：以简短的形式查看提交历史。

### 1.7. 查看差异

- git diff：查看工作区和暂存区的文件差异。
- git diff --staged：查看已暂存文件的差异。

---

## 2. 分支操作

### 2.1. 查看分支

- git branch：查看本地分支列表。

### 2.2. 创建新分支

- git branch [branch-name]：创建一个新的分支。

### 2.3. 切换分支

- git checkout [branch-name]：切换到指定分支。
- git switch [branch-name]：切换分支的更现代命令。

### 2.4. 创建并切换分支

- git checkout -b [branch-name]：创建并切换到新分支。
- git switch -c [branch-name]：新版本的等效命令。

### 2.5. 合并分支

- git merge [branch-name]：将指定分支合并到当前分支。

### 2.6. 删除分支

- git branch -d [branch-name]：删除分支（若该分支的更改已被合并）。
- git branch -D [branch-name]：强制删除分支（即使未合并）。

---

## 3. 远程操作

### 3.1. 查看远程仓库

- git remote -v：查看远程仓库地址。

### 3.2. 添加远程仓库

- git remote add [name] [url]：添加远程仓库。

### 3.3. 推送到远程仓库

- git push [remote] [branch]：将本地分支推送到远程仓库。
- git push -u [remote] [branch]：设置默认推送的上游分支，并推送。

### 3.4. 拉取远程仓库的更改

- git pull：从远程仓库拉取并合并更改。

### 3.5. 从远程仓库获取更新

- git fetch：从远程仓库获取更改，但不自动合并。

---

## 4. 撤销更改

### 4.1. 取消文件暂存

- git reset HEAD [filename]：将文件从暂存区移除，但保留工作区的更改。

### 4.2. 撤销文件修改

- git checkout -- [filename]：撤销工作区的修改，恢复到上一次提交的状态。

### 4.3. 重置到特定提交

- git reset --hard [commit]：重置当前分支到指定的提交，并丢弃之后的更改。

---

## 5. 标签操作

### 5.1. 创建标签

- git tag [tag-name]：创建一个轻量标签。
- git tag -a [tag-name] -m "[message]"：创建带注释的标签。

### 5.2. 查看标签

- git tag：列出所有标签。

### 5.3. 推送标签到远程仓库

- git push origin [tag-name]：推送单个标签。
- git push origin --tags：推送所有标签。

---

## 6. 其他有用命令

### 6.1. 清理未跟踪的文件

- git clean -f：删除未跟踪的文件。

### 6.2. 查看全局配置

- git config --list：查看所有 Git 配置信息。

### 6.3. 设置全局用户名和邮箱

- git config --global user.name "[name]"：设置用户名。
- git config --global user.email "[email]"：设置邮箱。

---

# 五.Git Bash使用示范

---

## 1.初始化本地库
### 1.1.创建文件，打开Git Bash
![](/images/git-images/git.23.png)
### 1.2.使用命令git init
```
git init
```
![](/images/git-images/git.24.png)

---

## 2.查看本地库状态
使用命令：
```
git status
```
![](/images/git-images/git.25.png)

---

## 3.创建项目
### 3.1.使用vim创建文件
![](/images/git-images/git.26.png)
![](/images/git-images/git.27.png)
![](/images/git-images/git.28.png)
**我还是更喜欢在VS Code中使用Git  
后续操作都在VS Code中进行  
在VS Code中的终端使用命令与在这里的Git Bash一样  
而且VS Code中有对于Git命令的图形化操作**

---

# **六.VS Code中使用Git**

---

## 1.安装插件
### 1.markdownlint 插件
![](/images/git-images/git.29.png)
#### 功能介绍

- **自动检测格式问题**：Markdownlint 可以自动检查 Markdown 文件中的格式问题，确保文档符合标准规范。它会提供即时反馈，帮助你在编辑时快速识别和修复潜在的错误。
- **自定义规则**：你可以根据项目需求配置自定义的检查规则，以适应不同的文档风格和要求。
- **集成到工作流中**：Markdownlint 与 VS Code 紧密集成，提供实时反馈，让你在撰写文档时无缝管理格式，提升文档质量。

### 2.Git Graph 插件
![](/images/git-images/git.30.png)
#### 功能介绍

- **可视化 Git 历史**：Git Graph 提供直观的图形界面，展示 Git 仓库的提交历史、分支、合并情况，帮助你快速理解代码的演变和分支结构。
- **便捷操作**：通过图形化界面，你可以方便地创建和切换分支、提交更改、查看提交差异、解决冲突等，无需输入命令行。
- **增强的代码审查体验**：通过可视化展示，Git Graph 使得团队成员可以更轻松地进行代码审查和协作，提高团队开发效率。

---

## 2.使用VS Code创建项目
**注意：需要先创建一个文件用作Git仓库**  
**VS Code上图形化界面使用Git在源代码管理**  

**快捷键：Ctrl+Shift+G**

![](/images/git-images/git.63.png)
**初始化仓库后源代码管理旁边三个点里面有对应的Git 命令相同的操作**
![](/images/git-images/git.65.png)
### 2.1.使用VS Code打开文件夹
![](/images/git-images/git.66.png)
### 2.1.打开终端
快捷键：（反引号一般在键盘左上角，特殊原因这里无法打出）
```
Crtl+反引号
```
使用命令初始化仓库：（去源代码管理点击初始化仓库也行）
```
git init
```
![](/images/git-images/git.31.png)
### 2.2.新建文件
![](/images/git-images/git.32.png)

### 2.3.提交到暂存区并添加到本地库
#### 方法一(使用终端操作)
#### 1.提交到暂存区
在**终端**输入命令
```
git add hello.txt # 添加单个文件 
git add .         # 添加当前目录下所有文件
```
#### 2.添加到本地库
在**终端**输入命令
```
git commit -m "first commit" hello.txt
```
**注意：这里的first commit是指这个提交的代码的称呼**
![](/images/git-images/git.33.png)
#### 方法二(使用源代码管理)
**快捷键:Ctrl Shitf G**  
也可在左侧栏点击打开
#### 1.提交到暂存区
![](/images/git-images/git.34.png)
#### 2.添加到本地库
**注意：提交上面的框框里要输入提交的代码的称呼，不然提交不成功**
![](/images/git-images/git.35.png)
**这些提交可以理解为一个版本，并且会生成一个版本号（哈希值）  
你可以使用命令任意更改当前项目是哪一个版本**

### 2.4.修改文件
**直接修改对应的文件就行了，修改完再暂存提交**
![](/images/git-images/git.36.png)![](/images/git-images/git.37.png)

### 2.5.切换到不同的提交
你每提交一次，都会生成一个哈希值，也可以理解为一个版本对应一个版本号
#### 1.查看哈希值
使用命令：
```
git reflog #追踪本地HEAD引用的所有变动记录
git log    #查看本地项目的提交历史
```
两个命令任选一个，这里推荐第一个，它默认只显示哈希值的前7位  
使用这种缩写的哈希值已经够了，第二个命令显示完全的哈希值
#### 2.补充介绍分页器
当你在命令行运行 **git log**或**git reflog** 时，Git 会进入一种**分页器（pager）**的显示模式，通常是 **less 分页器**。这种模式允许你逐页查看长输出内容，如 Git 提交记录 (log)。由于提交记录可能会非常长，分页器可以方便地滚动和查看历史记录。

具体特性：
分页显示：git log 的输出通过分页器按页显示，默认一次显示一个屏幕大小的内容，而不是全部输出到终端。

导航：在 less 分页器中，你可以使用以下键进行导航：

- **向上滚动**：按 k 或方向键上。
- **向下滚动**：按 j 或方向键下。
- **翻页**：按 空格键 向下翻页，按 b 向上翻页。
- **跳到末尾**：按 G。
- **跳到开头**：按 g。
- **退出分页器**：你按下 q 后，才能退出 less 分页器，回到普通的命令行界面。这是 less 的退出命令。

为什么使用分页器？
当输出的信息非常多时，直接输出到命令行会导致信息快速滚动，无法看清或逐一阅读。而 less 允许你控制滚动，按页查看长输出。

常见提示：
如果不想进入分页器，可以在 git log 命令后加上 --oneline 参数，这样每条提交记录只显示一行，通常不会超过终端的可视区域。
```
git log --oneline
```
你也可以通过 GIT_PAGER 环境变量或者使用 git log --no-pager 禁用分页器：
```
git --no-pager log
```
这种分页器模式非常常见，除了 git log，其他长输出的命令（如 man 命令）也会进入 less 或类似的分页模式。
#### 3.命令： **git reset 哈希值**
- **作用**：git reset <hash> 用于将当前分支的 HEAD（指向当前分支最新提交的指针）重置为指定的提交。
- **状态变化**：这会改变分支的历史记录（对于非共享分支），并且根据所用的选项（如 --soft、--mixed 或 --hard），会影响索引和工作目录的状态：
    - **--soft**：仅重置 HEAD，索引和工作目录保持不变。
    - **--mixed**（默认）：重置 HEAD 和索引，工作目录保持不变。
    - **--hard**：重置 HEAD、索引和工作目录，将所有更改丢弃。

![](/images/git-images/git.38.png)
![](/images/git-images/git.39.png)
### 2.6.使用分支
可以选择在**终端**使用**命令**创建分支  
也可以使用**源代码管理**里的图形界面
使用的相关命令可见上文 
![](/images/git-images/git.40.png)
![](/images/git-images/git.64.png)
### 2.7.合并分支
#### 2.7.1.在新建的分支里的文件做出修改并提交
**注意：合并时要到你想合并到的那个分支下，而不是在你修改内容的分支下
如图上面搜索栏，点master合并并没有效果**
![](/images/git-images/git.41.png)
#### 2.7.1.返回需要合并到的分支进行合并
可以使用命令
```
git checkout 分支名
```
![](/images/git-images/git.42.png)
选择你需要的合并的分支就能完成合并了
![](/images/git-images/git.43.png)

---

# 七.使用代码托管平台（GitHub）

---

GitHub官网：[https://github.com/](https://github.com/)
## 1.创建远程仓库
![](/images/git-images/git.44.png)
![](/images/git-images/git.45.png)
## 2.添加文件到远程存储库
**注意：在VS Code中的源代码管理中的图形界面拉取或推送需要先添加远程存储库  
这需要你登陆你的GitHub账号，点击添加远程存储库，会自动提示你登录  
当然克隆不用登陆，接下来我会演示图形界面推送，和终端中用命令拉取**
![](/images/git-images/git.46.png)
**在上图拉取、推送里选择推送，然后选择你的仓库，就能推送成功  
在你对项目进行修改后，暂存提交，然后推送，就能更新你的GitHub仓库了  
如果你是在源代码管理里提交，会自动弹出一个同步的按钮，就是把你的修改更新到GitHub仓库  
如果你选择终端使用命令也可以完成这些操作**
![](/images/git-images/git.47.png)
![](/images/git-images/git.48.png)

---

## 3.从远程存储库库克隆文件到本地
**注意：克隆文件不需要登陆**
**先创建一个存储项目的文件，再到仓库中复制Https地址**
![](/images/git-images/git.49.png)
**使用命令克隆**
```
git clone 地址
```
![](/images/git-images/git.50.png)![](/images/git-images/git.51.png)

---

## 4.团队内协作
### 4.1.邀请协作的人
点击add people后，输入你需要邀请的人的**用户名**，就会生成一个**邀请函(网址)**
![](/images/git-images/git.52.png)
将这个**邀请函**复制，**发给你需要邀请的人**  
**当然被邀请的人GitHub绑定的邮箱会收到一份邀请函，也可确认**
![](/images/git-images/git.53.png)
然后被邀请的人把你给的邀请函输入到浏览器中，就有一个**需要确认的是否加入这个项目**

![](/images/git-images/git.54.png)
被邀请人同意后，就能直接修改这个仓库，push不再需要权限
![](/images/git-images/git.55.png)

---

## 5.跨团队协作
### 5.1.fork项目
就是把别人的仓库复制一份到自己账号下
![](/images/git-images/git.56.png)
### 5.2.做出修改
### 5.3.发出pull请求
就是让别人合并你修改的部分
![](/images/git-images/git.57.png)
![](/images/git-images/git.58.png)
![](/images/git-images/git.59.png)
### 5.4.仓库管理者同意pull请求
仓库管理者会看到一个pull request
![](/images/git-images/git.60.png)
点击Merge pull request就能成功合并
![](/images/git-images/git.61.png)
合并成功后内容做出修改，并且贡献者中会多出你的用户名
![](/images/git-images/git.62.png)

---

# 八.完结

---

**使用VS Code管理Git项目是非常方便的，喜欢使用命令的话  
用VS Code提供的终端也是一样的，本文演示的地方可能一部分是用命令  
一部分是图形界面操作，可能看起来较为混乱，目的是想将两者都介绍一下  
其实专注于一者就能完成所有Git的操作，当然也可两者结合使用**
