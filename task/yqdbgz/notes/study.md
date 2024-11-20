# 1、Windows DOS 命令 - 学习笔记

## 1 批处理编程初体验

### 1-1 什么是批处理程序？

批处理编程（Batch programming）是微软操作系统自带的脚本语言，可以直接运行，无需配置额外环境。批处理文件通常以 `.bat` 后缀结尾，通过 `cmd.exe` 执行。

打开命令提示符的方法：
- 按 `Windows + R` 键，打开“运行”对话框。
- 输入 `cmd` 并按回车键。

### 1-2 如何编辑批处理文件

批处理文件可以使用任何文本编辑器来编辑，例如系统自带的 Notepad，并保存为 `.bat` 后缀的文件。

### 1-3 批处理程序可以做什么？

通过批处理文件，你可以使用一系列内置命令实现自动化操作，例如：
- 根据指定规则删除文件。
- 创建新文件、日志等。
- 甚至可以批量创建计算机病毒（请谨慎操作）。

### 1-4 一个简单的批处理程序

以下是一个输出“Hello World”的简单示例：

```batch
@echo off
echo "Hello World"
pause
```

注：pause 命令用于等待用户输入，防止命令窗口立即关闭。

### 1-5 命令分类

内部命令

直接内置于 `cmd.exe` 中的命令：

- `ipconfig` - 查看网络配置。
- `cls` - 清屏。

外部命令

需要依赖外部程序的命令：

- `java`、`python` 等。

## 2 批处理运算操作

### 2-1 算术运算
在批处理中，`set /a` 命令可以进行加、减、乘、除等基本算术运算，便于实现简单的计算需求。

**示例**：计算两个数字的和
```batch
@echo off
set /a result=5+3
echo 结果为：%result%
pause
```

### 2-2 重定向操作
重定向符号 `>` 和 `>>` 可以将命令输出写入文件中，`>` 会覆盖文件内容，而 `>>` 则将新内容追加至文件末尾。

**示例**：将 `dir` 命令的结果保存到文件
```batch
@echo off
dir > 文件列表.txt
echo 文件列表已保存至 文件列表.txt
pause
```
说明：执行上述命令后，当前目录下会生成一个名为 文件列表.txt 的文件，文件中包含了 dir 命令的输出内容。

### 2-3 多命令运算
通过 `&` 符号可以在一行中连续执行多个命令，这在需要多步操作时非常方便。

**示例**：显示文件夹内容并清屏
```batch
@echo off
dir & cls
pause
```
说明：执行上述命令后，首先会显示当前目录的文件和文件夹列表，然后清除屏幕，返回一个空白的命令提示符窗口。

### 2-4 管道操作
管道符 `|` 将前一命令的输出作为后一命令的输入，便于对命令结果进行进一步筛选和处理。

**示例**：显示 `dir` 命令输出中的包含 "txt" 的文件
```batch
@echo off
dir | find "txt"
pause
```
说明：执行上述命令后，将显示当前目录下所有文件和文件夹的列表，但只会输出名称中包含 “txt” 的项目。这种方法非常适合快速查找特定类型的文件。

## 3 基本命令

### 3-1 基本命令格式介绍
DOS 命令的基本格式为 `命令 参数`。大多数命令支持通过 `/` 或 `-` 来提供参数，以调整执行效果。例如，`dir /p` 将列出当前目录中的文件并按页显示，非常适合浏览较长的目录列表。

**示例**：按页显示当前目录的内容
```batch
@echo off
dir /p
pause
```
说明：执行上述命令后，将逐页显示当前目录中的文件和文件夹列表，每页内容显示完后等待用户按键继续。这对于查看文件较多的目录特别有用。

### 3-2 批处理文件接受参数
批处理文件可以通过 `%1`、`%2` 等变量接收外部传入的参数，方便实现更灵活的操作。

**示例**：输出传入的第一个参数
```batch
@echo off
echo 第一个参数是：%1
pause
```

说明：执行此批处理文件时，可以在文件名后面输入一个参数值，批处理会将其显示。例如运行 test.bat Hello，将输出 第一个参数是：Hello。

### 3-3 注释符介绍
在批处理中，可以使用 `REM` 或 `::` 来添加注释，帮助提高脚本的可读性和维护性。`REM` 和 `::` 后的内容不会被执行。

**示例**：添加注释
```batch
@echo off
REM 这是一行注释
:: 这也是一行注释
echo 批处理文件示例
pause
```
说明：REM 和 :: 均可用于编写注释，REM 是传统注释符，而 :: 仅在批处理中有效，两者功能相似。注释帮助理解批处理文件的功能和逻辑。

### 3-4 炫酷命令提示符窗口
通过 `color` 命令可以更改命令提示符窗口的颜色，例如 `color 0a` 将背景变为黑色、文本变为绿色。

**示例**：更改命令提示符颜色
```batch
@echo off
color 0a
echo 命令提示符颜色已更改
pause
```
说明：执行该命令后，命令窗口的背景将变为黑色，文字为绿色。这种效果可以让批处理文件的输出更加醒目，适合在演示或测试时使用。

### 3-5 时间相关命令
`date` 和 `time` 命令可以获取或设置系统的日期和时间，方便记录操作时间。

**示例**：显示当前日期和时间
```batch
@echo off
echo 当前日期：%date%
echo 当前时间：%time%
pause
```
说明：%date% 和 %time% 是系统内置变量，用于显示当前系统的日期和时间，适合在批处理文件中进行时间戳记录。

### 3-6 启动命令
`start` 命令可以用来启动外部程序或打开文件，适合在批处理中调用其他应用程序。

**示例**：启动计算器
```batch
@echo off
start calc
pause
```
说明：执行该命令后将启动 Windows 计算器。这在批处理文件中用于启动其他应用程序或打开文件时非常方便。

### 3-7 调用其他 bat 文件
在一个批处理文件中可以使用 `call` 命令来调用另一个批处理文件，并在执行完成后返回到主批处理文件继续运行。

**示例**：调用另一个批处理文件
```batch
@echo off
call another_script.bat
pause
```
说明：call 命令用于调用其他批处理文件并在完成后返回执行。这样可以将多个批处理文件组合在一起，适合需要分步骤执行的复杂任务。

### 3-8 任务列表查看命令
`tasklist` 命令用于查看当前系统的任务列表，包括运行的应用程序和后台进程。

**示例**：查看任务列表
```batch
@echo off
tasklist
pause
```
说明：执行该命令后将列出当前系统中的所有进程，包括进程名称、PID（进程 ID）和内存使用情况。这在系统资源管理和故障排查时非常有用。

### 3-9 任务终止命令
使用 `taskkill` 命令可以终止指定的任务，适合管理系统资源或关闭无响应的程序。

**示例**：关闭记事本程序
```batch
@echo off
taskkill /im notepad.exe /f
pause
```
说明：/im 指定要关闭的进程名称，/f 强制终止任务。此命令会关闭所有正在运行的记事本程序，适用于需要手动关闭特定进程的情况。

### 3-10 文件夹结构命令 tree
`tree` 命令用于显示当前目录的目录结构树，直观地展示文件夹的层级关系。

**示例**：查看目录结构
```batch
@echo off
tree
pause
```
说明：执行此命令后，将以树状图的形式显示当前目录及其所有子目录和文件的结构，适合快速了解文件夹的嵌套情况和内容布局。

### 3-11 关机命令
使用 `shutdown` 命令可以实现系统的关机、重启或注销操作，适合用于批处理文件中进行计划任务或远程控制。

**示例**：系统一分钟后关机
```batch
@echo off
shutdown /s /t 60
pause
```
说明：/s 表示关机，/t 指定延迟时间（以秒为单位）。执行该命令后，系统将在 60 秒后自动关机，适合用于需要定时关机的情况。

### 3-12 计划任务命令 at
`at` 命令用于设置计划任务，使得指定的任务在特定时间自动运行。注意：此命令需要在管理员权限下运行。

**示例**：在晚上8点打开记事本
```batch
@echo off
at 20:00 notepad.exe
pause
```
说明：该命令会在指定的时间（20:00）启动记事本程序。在使用此命令前，需要确保系统已启用任务调度功能。适用于需要定期执行的任务。
### 3-13 环境变量
通过 `set` 命令可以查看或设置系统的环境变量，如 `PATH`、`TEMP` 等，这对程序的运行和系统配置非常重要。

**示例**：查看 `PATH` 环境变量
```batch
@echo off
set PATH
pause
```
说明：执行此命令后，将输出当前系统的 PATH 环境变量内容，显示包含的所有路径。环境变量对程序的查找和执行至关重要，可以通过 set VARIABLE_NAME=value 的方式设置新变量或修改现有变量。

## 4 目录和文件操作

### 4-1 目录浏览命令 dir
`dir` 命令用于列出当前目录中的所有文件和文件夹，可以使用多种参数进行筛选。

**示例**：列出当前目录中的所有文件和文件夹
```batch
@echo off
dir
pause
```
说明：执行此命令后，将显示当前目录下的所有文件和文件夹的列表，可以方便地查看文件的基本信息。

### 4-2 目录新建与删除命令
使用 `mkdir` 命令可以创建新目录，而 `rmdir` 命令则用于删除目录。

**示例**：创建新目录和删除目录
```batch
@echo off
mkdir NewFolder
rmdir NewFolder
pause
```
说明：mkdir NewFolder 将在当前目录下创建一个名为 NewFolder 的新文件夹，rmdir NewFolder 将删除该文件夹。注意，删除的目录必须为空。

### 4-3 目录切换命令 cd
`cd` 命令用于切换当前工作目录，可以通过路径参数访问不同的目录。

**示例**：切换到上级目录
```batch
@echo off
cd ..
pause
```
说明：执行此命令后，将返回到当前目录的上一级目录。可以通过 cd 路径 切换到指定目录，例如 cd C:\Users\YourName\Documents。

### 4-4 目录重命名命令 ren
`ren` 命令用于重命名文件或目录。

**示例**：重命名目录
```batch
@echo off
mkdir OldFolder
ren OldFolder NewFolder
pause
```
说明：执行上述命令后，将首先创建一个名为 OldFolder 的目录，然后将其重命名为 NewFolder。请注意，重命名时，目标名称不能与当前目录中的其他文件或文件夹重复。

### 4-5 目录拷贝命令 copy
`copy` 命令用于复制文件，可以将文件复制到同一目录或其他目录，支持多种参数以实现不同的功能。

**基本示例**：复制文件
```batch
@echo off
copy example.txt example_copy.txt
pause
```
说明：执行该命令后，将复制 example.txt 文件并创建一个名为 example_copy.txt 的副本。

**示例**：复制所有文本文件到指定目录
```batch
@echo off
copy *.txt D:\Backup\
pause
```
说明：该命令将当前目录下所有以 .txt 结尾的文件复制到 D:\Backup\ 目录。

**示例**：在复制时覆盖已存在的文件
```batch
@echo off
copy /y example.txt example_copy.txt
pause
```
说明：/y 参数用于强制覆盖目标文件，而无需提示用户确认。

**示例**：显示复制过程中详细信息
```batch
@echo off
copy /v example.txt example_copy.txt
pause
```
说明：/v 参数用于验证新文件的内容与原文件是否一致，确保复制的准确性。

**示例**：将多个文件复制到目标目录
```batch
@echo off
copy file1.txt + file2.txt D:\Backup\merged.txt
pause
```
说明：该命令将 file1.txt 和 file2.txt 合并为一个文件 merged.txt，并将其复制到 D:\Backup\ 目录。

### 4-6 文件删除命令 del
`del` 命令用于删除指定的文件，可以通过多种参数进行灵活操作。

**基本示例**：删除单个文件
```batch
@echo off
del example_copy.txt
pause
```
说明：执行该命令后，将删除名为 example_copy.txt 的文件。请谨慎使用此命令，因为删除的文件无法恢复。

**示例**：删除多个文件
```batch
@echo off
del *.txt
pause
```
说明：该命令将删除当前目录下所有以 .txt 结尾的文件。

**示例**：强制删除文件而不提示确认
```batch
@echo off
del /f example_copy.txt
pause
```
说明：/f 参数用于强制删除只读文件，无论文件的属性如何。

**示例**：删除所有文件并不显示确认提示
```batch
@echo off
del /q *.log
pause
```
说明：/q 参数用于安静模式，删除文件时不显示确认提示。该命令将删除当前目录下所有 .log 文件。

**示例**：使用通配符删除特定类型文件
```batch
@echo off
del C:\Users\YourName\Documents\*.tmp
pause
```
说明：该命令将删除 C:\Users\YourName\Documents\ 目录下所有以 .tmp 结尾的临时文件。

### 4-7 文件剪切命令 move
`move` 命令用于剪切并移动文件或目录，可以将文件从一个位置移动到另一个位置。

**基本示例**：移动单个文件
```batch
@echo off
move example.txt D:\Documents\
pause
```
说明：执行该命令后，将 example.txt 文件从当前目录移动到 D:\Documents\ 目录。

**示例**：移动并重命名文件
```batch
@echo off
move example.txt example_new.txt
pause
```
说明：该命令将 example.txt 移动到同一目录并重命名为 example_new.txt。

**示例**：移动目录
```batch
@echo off
move OldFolder D:\NewFolder\
pause
```
说明：执行此命令将 OldFolder 目录及其内容移动到 D:\NewFolder\ 目录。

**示例**：强制移动文件并覆盖目标文件
```batch
@echo off
move /y example.txt D:\Documents\
pause
```
说明：/y 参数用于在目标文件已存在时不提示用户，而是直接覆盖它。该命令将 example.txt 移动到 D:\Documents\ 目录，若目标文件存在，则会被覆盖。

## 5 用户和网络操作

### 5-1 用户操作命令
使用 `net user` 命令可以管理本地用户账户，如创建、删除用户等。

**示例**：查看当前用户列表
```batch
@echo off
net user
pause
```
说明：执行此命令后，将显示计算机上所有用户账户的列表。

### 5-2 用户组操作命令
使用 net localgroup 命令可以管理本地用户组。

**示例**：查看用户组列表
```batch
@echo off
net localgroup
pause
```
说明：该命令将列出计算机上的所有本地用户组。

### 5-3 主机联通性检测命令 ping
ping 命令用于检测网络连接，检查主机是否可以到达。
**示例**：检测与百度的连接
```batch
@echo off
ping www.baidu.com
pause
```
说明：执行此命令后，将向 www.baidu.com 发送数据包，并显示响应时间及数据包丢失率。

### 5-4 网络连接命令 telnet
telnet 命令用于连接到远程主机，可以测试特定端口的连接。

**示例**：连接到指定主机的 80 端口
```batch
@echo off
telnet www.example.com 80
pause
```
说明：执行此命令后，将尝试连接到 www.example.com 的 80 端口，适合测试 HTTP 连接。

### 5-5 网络路由信息命令
使用 `tracert` 命令可以跟踪数据包到达目标主机的路径，并显示经过的路由器。

**基本示例**：跟踪到指定网站的路径
```batch
@echo off
tracert www.baidu.com
pause
```
说明：执行此命令后，将显示从本地计算机到 www.baidu.com 的数据包经过的每一个路由器的 IP 地址和响应时间。这有助于网络故障排除，了解数据包的传输路径。

**示例**：跟踪到特定 IP 地址的路径
```batch
@echo off
tracert 192.168.1.1
pause
```
说明：该命令将跟踪数据包到达 192.168.1.1 的路径，通常用于检测局域网中的设备。

**示例**：限制最大跳数
```batch
@echo off
tracert -h 5 www.baidu.com
pause
```
说明：-h 参数用于设置最大跳数，此命令将跟踪到 www.baidu.com 的路径，最多只经过 5 个路由器。

**示例**：输出到文件
```batch
@echo off
tracert www.baidu.com > tracert_result.txt
pause
```
说明：该命令将跟踪的结果输出到 tracert_result.txt 文件中，便于后续查看和分析。

### 5-6 网络适配器命令 ipconfig
`ipconfig` 命令用于显示和管理计算机的网络适配器配置信息，常用于获取本地 IP 地址、子网掩码和默认网关等信息。

**基本示例**：查看网络配置信息
```batch
@echo off
ipconfig
pause
```
说明：执行此命令后，将显示当前计算机所有网络适配器的配置信息，包括 IPv4 和 IPv6 地址、子网掩码以及默认网关等。

**示例**：查看详细的配置信息
```batch
@echo off
ipconfig /all
pause
```
说明：/all 参数将显示所有网络适配器的详细配置信息，包括物理地址（MAC 地址）、DHCP 状态、DNS 服务器等。

**示例**：释放 DHCP 地址
```batch
@echo off
ipconfig /release
pause
```
说明：该命令将释放当前网络适配器的 DHCP 地址，通常在网络故障排除时使用。


**示例**：更新 DHCP 地址
```batch
@echo off
ipconfig /renew
pause
```
说明：/renew 参数用于请求新的 DHCP 地址，适用于当计算机无法连接到网络时。

**示例**：显示特定适配器的 IP 配置
```batch
@echo off
ipconfig | find "IPv4"
pause
```
说明：该命令将通过管道操作符 | 和 find 命令筛选出包含 IPv4 的行，仅显示 IP 地址的信息。

### 5-7 ARP信息命令
`arp` 命令用于查看和管理 ARP（地址解析协议）缓存，ARP 缓存存储了 IP 地址与其对应的物理地址（MAC 地址）的映射信息。这对于网络故障排除和网络配置非常有用。

**基本示例**：查看 ARP 缓存
```batch
@echo off
arp -a
pause
```
说明：执行该命令后，将列出本地计算机的 ARP 缓存，包括 IP 地址、物理地址（MAC 地址）和类型（动态或静态）。

**示例**：清空 ARP 缓存
```batch
@echo off
arp -d *
pause
```
说明：-d 参数用于删除 ARP 缓存中的条目，* 表示删除所有条目。清空缓存后，系统在下次访问时将重新构建 ARP 缓存。

**示例**：添加静态 ARP 条目
```batch
@echo off
arp -s 192.168.1.10 00-1A-2B-3C-4D-5E
pause
```
说明：-s 参数用于手动添加静态 ARP 条目，将 IP 地址 192.168.1.10 与物理地址 00-1A-2B-3C-4D-5E 关联。此项配置将一直保持，直到计算机重启。

**示例**：删除特定的 ARP 条目
```batch
@echo off
arp -d 192.168.1.10
pause
```
说明：该命令将删除与 192.168.1.10 相关的 ARP 条目。这在更新网络设备或故障排除时非常有用。

## 6 条件判断与控制结构

### 6-1 if-else 结构
在批处理脚本中，`if` 语句用于执行条件判断，允许根据条件执行不同的命令。

**示例**：检查文件是否存在
```batch
@echo off
set "fileName=test.txt"

if exist "%fileName%" (
    echo File "%fileName%" exists.
) else (
    echo File "%fileName%" does not exist.
)
pause
```
说明：使用 if exist 判断指定文件是否存在，根据结果执行不同的输出。

### 6-2 判断文件是否存在 exists

if exist 语句用于检查指定文件或目录是否存在。

**示例**：检查目录是否存在
```batch
@echo off
set "dirName=MyFolder"

if exist "%dirName%" (
    echo Directory "%dirName%" exists.
) else (
    echo Directory "%dirName%" does not exist.
)
pause
```

说明：该命令检查名为 MyFolder 的目录是否存在，并输出相应信息。

### 6-3 文件判断删除

可以通过 if exist 语句判断文件是否存在并进行删除。

**示例**：删除指定文件
```batch
@echo off
set "fileName=delete_me.txt"

if exist "%fileName%" (
    del "%fileName%"
    echo File "%fileName%" has been deleted.
) else (
    echo File "%fileName%" does not exist, cannot delete.
)
pause
```
说明：在判断文件是否存在的基础上，如果存在则使用 del 命令删除文件，并输出相应信息。

## 7 循环与遍历操作

### 7-1 循环遍历文件夹名称
使用 `for` 命令可以遍历指定目录中的所有子文件夹。这在需要批量处理多个文件夹时非常有用。

**基本示例**：遍历当前目录下的所有文件夹
```batch
@echo off
for /d %%F in (*) do (
    echo Folder: %%F
)
pause
```
说明：执行此命令后，将列出当前目录下的所有文件夹名称。%%F 是循环变量，表示每个找到的文件夹的名称。

**示例**：遍历指定目录下的文件夹
```batch
@echo off
for /d %%F in (D:\MyFolders\*) do (
    echo Folder: %%F
)
pause
```
说明：该命令将遍历 D:\MyFolders\ 目录下的所有文件夹，并输出其名称。

**示例**：处理文件夹时执行其他操作
```batch
@echo off
for /d %%F in (*) do (
    echo Processing folder: %%F
    cd %%F
    rem 在此处添加其他操作
    cd ..
)
pause
```
说明：该命令将在遍历每个文件夹时切换到该文件夹，并可以在其中执行其他命令（如处理文件）。cd .. 用于返回到上层目录。

注意：在批处理文件中使用 %% 符号来表示循环变量，而在命令行直接输入时，应使用 % 符号。

### 7-2 遍历文件夹下的文件
使用 `for` 命令可以遍历指定文件夹中的所有文件，非常适合批量文件操作。

**基本示例**：遍历当前目录下的所有文件
```batch
@echo off
for %%F in (*) do (
    echo File: %%F
)
pause
```
说明：该命令将列出当前目录下的所有文件名称，%%F 是循环变量，代表每个文件的名称。

**示例**：遍历指定目录下的所有文件
```batch
@echo off
for %%F in (D:\MyFiles\*) do (
    echo File: %%F
)
pause
```
说明：此命令将遍历 D:\MyFiles\ 目录中的所有文件，并输出每个文件的名称。

**示例**：筛选特定类型的文件（如 .txt 文件）
```batch
@echo off
for %%F in (*.txt) do (
    echo Text File: %%F
)
pause
```
说明：此命令将仅遍历当前目录中的 .txt 文件，并输出其文件名。

**示例**：对每个文件执行操作
```batch
@echo off
for %%F in (*.txt) do (
    echo Processing file: %%F
    type %%F
    rem 在此处添加其他操作
)
pause
```
说明：该命令将在遍历到的每个 .txt 文件上执行 type 命令（显示文件内容）。可以在其中添加其他命令，以批量处理文件。

注意：在批处理文件中使用 %% 符号表示循环变量，而在命令行直接输入时，应使用 % 符号。

### 7-3 遍历数字操作
使用 `for /l` 命令可以遍历一系列数字，非常适合需要循环固定次数的情况。

**基本示例**：输出从 1 到 5 的数字
```batch
@echo off
for /l %%N in (1,1,5) do (
    echo Number: %%N
)
pause
```
说明：for /l %%N in (start, step, end) 用于定义一个数值序列，其中 start 是起始值，step 是步长，end 是结束值。此示例输出从 1 到 5 的数字，每次增加 1。

**示例**：输出从 10 到 50，每次增加 10
```batch
@echo off
for /l %%N in (10,10,50) do (
    echo Number: %%N
)
pause
```

说明：此命令将从 10 开始，每次增加 10，输出结果为 10、20、30、40 和 50。

示例：输出从 5 到 1 的倒序数字
```batch
@echo off
for /l %%N in (5,-1,1) do (
    echo Number: %%N
)
pause
```
说明：此命令将从 5 开始，每次减 1，输出结果为 5、4、3、2 和 1。

注意：在批处理文件中使用 %% 符号表示循环变量，而在命令行直接输入时，应使用 % 符号。

### 7-4 遍历文件内容操作
使用 `for /f` 命令可以逐行遍历文件内容，适用于读取和处理文本文件中的每一行数据。

**基本示例**：读取 `example.txt` 文件中的每一行
```batch
@echo off
for /f "delims=" %%L in (example.txt) do (
    echo Line: %%L
)
pause
```
说明：for /f "delims=" %%L in (filename) 用于逐行读取文件中的内容。delims= 参数表示不使用分隔符，以便读取整行内容。

**示例**：读取文件并按空格分隔每个单词
```batch
@echo off
for /f "tokens=1,2 delims= " %%A in (example.txt) do (
    echo First Word: %%A, Second Word: %%B
)
pause
```
说明：tokens=1,2 用于将每行按空格分隔成多个部分，%%A 表示第一部分，%%B 表示第二部分。

**示例**：读取文件并忽略空行与注释行
```batch
@echo off
for /f "usebackq tokens=* eol=#" %%L in ("example.txt") do (
    echo Line: %%L
)
pause
```
说明：usebackq 允许文件名使用引号，eol=# 设置注释行起始符号为 #。此命令将忽略以 # 开头的行和空行。

注意：在批处理文件中使用 %% 符号表示循环变量，而在命令行直接输入时，应使用 % 符号。

## 8 目录重复新建操作

### 8-1 目录重复新建代码分析
在批处理脚本中，可能需要确保某个目录不存在后再新建，避免重复创建。

**示例**：检查并创建目录
```batch
@echo off
set "dirName=NewFolder"

if not exist "%dirName%" (
    mkdir "%dirName%"
    echo Folder "%dirName%" has been created.
) else (
    echo Folder "%dirName%" already exists.
)
pause
```
说明：if not exist 用于判断目录是否存在。如果 dirName 指定的文件夹不存在，则使用 mkdir 创建该文件夹；否则，输出该文件夹已存在的信息。

**示例**：批量创建多个文件夹，避免重复
```batch
@echo off
for %%D in (Folder1 Folder2 Folder3) do (
    if not exist "%%D" (
        mkdir "%%D"
        echo Folder "%%D" has been created.
    ) else (
        echo Folder "%%D" already exists.
    )
)
pause
```
说明：此命令将依次检查 Folder1、Folder2 和 Folder3 是否存在，如果不存在则创建，已存在则输出信息。for 循环用于批量处理多个文件夹。

**示例**：基于日期创建文件夹
```batch
@echo off
set "dateFolder=%date:/=-%"

if not exist "%dateFolder%" (
    mkdir "%dateFolder%"
    echo Folder "%dateFolder%" has been created.
) else (
    echo Folder "%dateFolder%" already exists.
)
pause
```

说明：此命令将以当前日期命名创建文件夹，例如 2023-12-31，避免重复创建每日文件夹。

## 9 计算机信息展示与交互操作

### 9-1 计算机信息展示
使用批处理命令可以显示计算机的基本信息，包括系统信息、IP 配置等内容。

**示例**：显示系统信息
```batch
@echo off
systeminfo
pause
```
说明：systeminfo 命令可以显示详细的系统信息，包括操作系统版本、内存、网络配置、安装日期等。

**示例**：显示 IP 配置信息
```batch
@echo off
ipconfig
pause
```
说明：ipconfig 命令显示网络适配器的 IP 地址、子网掩码、默认网关等网络配置信息，便于快速查看计算机的网络配置。
### 9-2 交互操作介绍
批处理脚本可以与用户进行简单的交互，例如提示用户输入信息并根据输入执行相应操作。

**示例**：让用户输入名称并输出欢迎信息
```batch
@echo off
set /p name=Please enter your name: 
echo Welcome, %name%!
pause
```
说明：set /p 命令用于从用户输入获取数据，并将输入内容存储在变量 name 中，随后输出欢迎信息。

**示例**：让用户选择继续或退出

```batch
@echo off
choice /m "Do you want to continue?"
if %errorlevel%==1 (
    echo You chose to continue.
) else (
    echo You chose to exit.
)
pause
```
说明：choice /m 命令创建一个选择提示，%errorlevel% 用于判断用户的选择（1 表示继续，2 表示退出）。该示例根据用户的选择执行不同的操作。

### 9-3 计划执行操作
使用 `timeout` 命令可以设置批处理脚本的延迟执行，从而模拟简单的定时任务。

**示例**：延迟 10 秒后执行命令
```batch
@echo off
echo Waiting for 10 seconds...
timeout /t 10
echo 10 seconds have passed.
pause
```
说明：timeout /t 10 命令将脚本暂停 10 秒后继续执行，适合设置短暂的时间延迟。可以使用 /nobreak 参数防止用户按键打断延迟过程。

**示例**：设置特定时间执行命令
```batch
@echo off
echo The command will run at a specific time...
at 12:00 echo This is a scheduled task.
pause
```
说明：at 命令用于设置在特定时间执行某一任务（此命令在部分 Windows 版本可能不再支持，建议使用 schtasks 替代）。

### 9-4 Bat 批处理脚本转 Exe 程序介绍
可以通过第三方工具将 `.bat` 文件转换为 `.exe` 可执行程序，使其便于分发和运行，并保护脚本内容。

**常见工具**：
1. **Bat to Exe Converter**：简单易用的图形界面工具，适合快速将 `.bat` 文件转换为 `.exe` 文件。
2. **Advanced BAT to EXE Converter**：提供丰富的选项，包括设置图标、加密脚本内容、隐藏运行窗口等。

**使用优势**：
- 将 `.bat` 文件转换为 `.exe` 可执行文件后，脚本的源代码将不再直接暴露，适合需要保护内容的场合。
- 转换后的文件便于在用户计算机上直接运行，无需依赖批处理环境。

**注意**：转换为 `.exe` 后的文件可能会丧失部分批处理的灵活性，适用于分发和执行频率较高的脚本。

# 2、速学150个Linux常用命令 - 学习笔记

## 基础知识介绍

### 获取Linux环境的几种常见方式
- **VMware虚拟机安装Linux操作系统**：适合本地测试和开发，提供模拟的Linux环境。
- **终端工具MobaXterm的使用**：一体化的终端工具，支持多种协议（SSH、SFTP等），便于远程连接Linux系统。
- **文件传输工具WinSCP的使用**：图形化的文件传输工具，适用于Windows和Linux系统之间的文件传输。

### Linux目录结构介绍
- 根目录 `/`：系统根目录，所有文件和目录的起始点。
- `/bin`：基本二进制可执行文件，如常用命令`ls`、`cat`等。
- `/etc`：系统配置文件目录。
- `/home`：普通用户的主目录。
- `/var`：日志文件和动态数据文件存放的目录。
- `/tmp`：临时文件目录。
- `/usr`：包含用户应用程序和文件。

### Linux系统文件或目录颜色的含义
- **蓝色**：目录
- **绿色**：可执行文件
- **红色**：压缩文件
- **浅蓝色**：链接文件
- **黄色**：设备文件

### Linux系统常用终端快捷键
- **Ctrl + C**：终止当前命令执行。
- **Ctrl + Z**：将当前命令放入后台并暂停（使用`fg`恢复）。
- **Ctrl + D**：退出终端或结束输入。
- **Ctrl + L**：清屏，相当于`clear`命令。
- **Ctrl + A**：将光标移动到行首。
- **Ctrl + E**：将光标移动到行尾。
- **Ctrl + U**：删除光标前的所有内容。
- **Ctrl + K**：删除光标后的所有内容。
- **Ctrl + W**：删除光标前的一个单词。
- **Ctrl + Y**：粘贴（恢复最后一次被删除的文本）。
- **Ctrl + R**：反向搜索历史命令。
- **Ctrl + P**：显示上一条历史命令。
- **Ctrl + N**：显示下一条历史命令。
- **Alt + .**：粘贴上一个命令的最后一个参数。
- **Tab**：自动补全命令、文件或目录名。

- **Shift + PgUp**：向上滚动终端内容。
- **Shift + PgDn**：向下滚动终端内容。
- **!!**：执行上一条命令。
- **!n**：执行历史记录中第`n`条命令（使用`history`查看编号）。

### Tab键的妙用
在 Linux 终端中，**Tab 键**有以下几个常用的用途：

1. **命令或文件名自动补全**：
- 输入命令或文件名的开头部分后，按 `Tab` 键，系统会自动补全（如果该部分是唯一的）。
- 如果有多个可能的补全项，按两次 `Tab`，系统会列出所有匹配项供选择。

示例：
```bash
# 输入 "cd Do" 后按 Tab，系统会自动补全目录名 "Documents"（如果唯一）
cd Do<Tab>  # 自动补全为 "cd Documents"
```
2. 路径补全：
- 在输入文件或目录路径时，Tab 键会尝试自动补全路径。
- 若路径中有多层嵌套目录，Tab 可以逐层补全。
```bash
# 输入 "cd /ho" 后按 Tab，系统会补全为 "/home"。
cd /ho<Tab>  # 自动补全为 "cd /home"
```
3.	查看命令选项（部分命令支持）：
- 输入部分命令名后按 Tab，可能会显示该命令的所有选项。
示例：
```bash
# 输入 "git " 后按两次 Tab，系统会列出所有 Git 命令。
git <Tab><Tab>
```
这些快捷功能可以大大提高命令行操作的效率，减少输入错误。

### 文件权限介绍

在 Linux 系统中，文件权限用于控制谁可以访问或操作文件。权限分为 **读取 (r)**、**写入 (w)** 和 **执行 (x)** 三种，每一种权限适用于不同的用户角色。掌握文件权限的管理方式是确保系统安全性和资源合理访问的重要组成部分。

#### 文件权限类型
- **读取 (r)**：允许查看文件内容或列出目录内容。
- **写入 (w)**：允许修改文件内容、创建或删除文件、修改目录内容等。
- **执行 (x)**：允许运行文件（对于可执行文件）或进入目录。

#### 用户分类
权限可以为不同类别的用户设置：
- **所有者 (u)**：通常是文件的创建者，可以对其设置完全的读、写、执行权限。
- **同组用户 (g)**：与所有者同属一个用户组的用户，可以根据权限设定对文件进行访问和操作。
- **其他用户 (o)**：系统中其他非该文件所有者及其组的用户，权限一般更为严格，通常只允许最低限度的访问权限。

#### 权限表示方式
文件权限可以通过字符或数字形式表示。

1. **字符形式**：
- 文件权限通常用 10 个字符表示，第一个字符表示文件类型，`-` 表示普通文件，`d` 表示目录，`l` 表示链接文件。
- 后续 9 个字符分成三组，每组 3 个字符，依次表示所有者、同组用户、其他用户的权限。每组中 `r` 表示读取，`w` 表示写入，`x` 表示执行。

示例：
```bash
drwxr-xr-x
```
- `d` 表示目录。
- `rwx` 表示所有者拥有读、写、执行权限。
- `r-x` 表示同组用户拥有读、执行权限。
- `r-x` 表示其他用户拥有读、执行权限。

2. **数字形式**：
- 权限也可以通过八进制数字表示，其中 `r=4`、`w=2`、`x=1`。将数字相加得到相应的权限组合。
- 每个用户角色拥有一个三位数字，表示所有者、同组用户和其他用户的权限。

示例：
- `755`：所有者拥有读、写、执行权限 (`rwx = 4+2+1 = 7`)，同组用户和其他用户拥有读、执行权限 (`r-x = 4+0+1 = 5`)。
- `644`：所有者拥有读、写权限 (`rw- = 4+2+0 = 6`)，同组用户和其他用户拥有读取权限 (`r-- = 4+0+0 = 4`)。

#### 修改权限的命令
在 Linux 中，使用 `chmod` 命令可以修改文件或目录的权限。

- **数字形式设置权限**：
```bash
chmod 755 filename   # 设置文件为所有者 rwx，同组和其他用户 r-x
chmod 644 filename   # 设置文件为所有者 rw，同组和其他用户 r
```
- **字符形式设置权限**：
    - u 表示所有者，g 表示同组用户，o 表示其他用户，a 表示全部用户。
    - +添加权限，- 移除权限，= 指定权限。
    ```bash
    chmod u+x filename     # 给所有者添加执行权限
    chmod g-w filename     # 移除同组用户的写权限
    chmod o=r filename     # 将其他用户权限设置为只读
    ```
### 通配符介绍
- `*`：匹配任意字符。
- `?`：匹配单个字符。
- `[abc]`：匹配其中一个字符。
- `[a-z]`：匹配字符范围。

---

## 常用命令用法及说明

### 帮助命令
- **man**：显示命令的手册页，如`man ls`。
- **info**：显示命令的GNU info文档，如`info ls`。
- **whatis**：显示命令的简短描述，如`whatis ls`。

### 文件和目录操作
- **touch**：创建空文件或修改文件的时间戳，如`touch newfile.txt`。
- **mkdir**：创建目录，如`mkdir newdir`。
- **rm**：删除文件或目录，如`rm file.txt`，`rm -r dir`。
- **rmdir**：删除空目录，如`rmdir emptydir`。
- **mv**：移动或重命名文件或目录，如`mv oldname newname`，`mv file.txt /newdir/`。
- **cp**：复制文件或目录，如`cp file.txt /newdir/`，`cp -r dir /newdir/`。
- **cd**：切换目录，如`cd /newdir`。
- **pwd**：显示当前工作目录。
- **ls**：列出目录内容，如`ls -l`显示详细信息。
- **tree**：以树状结构显示目录内容，如`tree`。
- **stat**：显示文件或文件系统的状态信息，如`stat file.txt`。
- **rename**：批量重命名文件，如`rename 's/old/new/' *.txt`。
- **basename**：从完整路径中提取文件名，如`basename /path/to/file.txt`。
- **dirname**：从完整路径中提取目录部分，如`dirname /path/to/file.txt`。
- **chattr/lsattr**：修改/查看文件属性，如`chattr +i file.txt`，`lsattr file.txt`。
- **file**：识别文件类型，如`file file.txt`。
- **md5sum**：生成和校验文件的md5值，如`md5sum file.txt`。

### 查找命令
- **find**：查找目录或文件，如`find / -name file.txt`。
- **which**：查找命令的位置，如`which ls`。
- **whereis**：查找命令、源代码和手册页的位置，如`whereis ls`。
- **locate**：查找符合条件的文档，如`locate file.txt`（需先运行`updatedb`更新数据库）。

### 文件权限和用户管理
- **chown**：改变文件所属用户或组，如`chown user:group file.txt`。
- **chgrp**：改变文件或目录所属组，如`chgrp group file.txt`。
- **chmod**：改变用户对文件或目录的权限，如`chmod u+x file.txt`，`chmod 755 file.txt`。

### 文本处理
- **grep**：文本搜索工具，如`grep 'pattern' file.txt`。
- **egrep**：文件内查找指定字符串命令（同`grep -E`），如`egrep 'pattern' file.txt`。
- **cat**：查看文本内容，如`cat file.txt`。
- **more**：逐页阅读文本，如`more file.txt`。
- **less**：分页查看文本内容，如`less file.txt`。
- **head**：查看文件开头内容，如`head -n 10 file.txt`。
- **tail**：查看文本尾部内容，如`tail -n 10 file.txt`。
- **tac**：反向显示文本内容，如`tac file.txt`。
- **nl**：统计文件行号，如`nl file.txt`。
- **wc**：统计文本字数信息，如`wc -l file.txt`。
- **split**：文件切割，如`split -l 100 file.txt part_`。
- **cut**：文本截取，如`cut -d: -f1 /etc/passwd`。
- **paste**：文件合并，如`paste file1.txt file2.txt`。
- **sort**：文本内容排序，如`sort file.txt`。
- **uniq**：去除重复行，如`uniq file.txt`。
- **diff/patch**：比较差异/打补丁，如`diff file1.txt file2.txt`，`patch file1.txt < patchfile`。
- **join**：连接两个文件，如`join file1.txt file2.txt`。
- **tr**：字符转换，如`tr 'a-z' 'A-Z' < file.txt`。
- **sed**：流编辑器，如`sed 's/old/new/' file.txt`。
- **awk**：编程语言，用于文本处理，如`awk '{print $1}' file.txt`。

### 系统监控和管理
- **du**：显示目录或文件大小，如`du -sh /dir`。
- **df**：磁盘使用情况，如`df -h`。
- **sync**：数据同步，如`sync`。
- **mount/umount**：挂载/卸载文件系统，如`mount /dev/sda1 /mnt`，`umount /mnt`。
- **dd**：拷备及转换文件，如`dd if=/dev/zero of=file.txt bs=1M count=1`。
- **tar**：打包解压文件，如`tar -czvf archive.tar.gz /dir`，`tar -xzvf archive.tar.gz`。
- **zip/unzip**：压缩/解压文件，如`zip archive.zip file.txt`，`unzip archive.zip`。
- **gzip/gunzip**：压缩/解压文件，如`gzip file.txt`，`gunzip file.txt.gz`。
- **uname**：显示系统信息，如`uname -a`。
- **hostname**：显示或设置主机名，如`hostname`，`hostname newhostname`。
- **dmesg**：显示开机信息，如`dmesg | less`。
- **uptime**：查看系统负载，如`uptime`。
- **free**：显示内存使用情况，如`free -h`。
- **ulimit**：限制系统资源，如`ulimit -n 2048`。
- **init**：切换系统运行级别，如`init 3`。
- **service**：控制系统服务，如`service httpd start`。
- **vmstat**：显示虚拟内存状态，如`vmstat 1`（每秒更新一次）。
- **iostat**：监视系统输入输出设备和CPU的使用情况，如`iostat -x 1`（详细模式，每秒更新一次）。
- **ipcs**：显示进程间通信设备状态，如`ipcs -a`（显示所有IPC信息）。
- **ipcrm**：删除指定ipc资源，如`ipcrm -m shm_id`（删除消息队列）。
- **route**：显示并设置IP路由表，如`route -n`（以数字形式显示路由表）。

### 网络工具

- **ping**：网络连通测试命令，如`ping www.example.com`。
- **traceroute**：追踪数据包传输路径命令，如`traceroute www.example.com`。
- **ifconfig**：显示或设置网络设备参数命令，如`ifconfig eth0 192.168.1.10`（设置IP地址）。
- **ifup_ifdown**：激活或禁用网络接口命令，如`ifup eth0`，`ifdown eth0`。
- **netstat**：查看网络相关信息命令，如`netstat -tuln`（显示监听中的TCP和UDP端口）。
- **ss**：显示活动套接字信息命令，如`ss -tuln`（与netstat类似，但更快）。
- **telnet**：远程登陆服务器命令，如`telnet host port`。
- **ssh**：安全连接服务器命令，如`ssh user@host`。
- **ftp**：文件传输命令，如`ftp ftp.example.com`。
- **sftp**：交互式文件传输程序，如`sftp user@host`。
- **lftp**：下载工具，支持多种协议，如`lftp ftp://ftp.example.com`。
- **wget**：网络下载工具，如`wget http://example.com/file.zip`。
- **scp**：远程文件拷贝命令，如`scp user@remote:/path/to/file /local/path`。
- **curl**：远程数据传输工具，支持多种协议，如`curl -O http://example.com/file.zip`。
- **host**：分析域名查询工具，如`host www.example.com`。
- **tcpdump**：数据抓包工具，如`tcpdump -i eth0 port 80`（抓取80端口的数据包）。
- **nc**：网络检测工具，如`nc -zv host port`（扫描端口）。

### 用户和组管理

- **useradd**：创建用户命令，如`useradd username`。
- **adduser**：用户相关命令（某些Linux发行版中useradd的别名）。
- **passwd**：修改用户密码命令，如`passwd username`。
- **userdel**：删除用户命令，如`userdel username`。
- **su**：切换用户命令，如`su - username`。
- **sudo**：以其他身份来执行命令，如`sudo command`。
- **id**：显示用户id信息命令，如`id username`。
- **usermod**：修改用户信息命令，如`usermod -aG groupname username`（添加用户到组）。
- **groups**：显示用户所属的组。
- **groupadd**：用户组相关命令，用于创建新组，如`groupadd groupname`。
- **groupdel**：用户组相关命令，用于删除组，如`groupdel groupname`。

### 用户信息

- **whoami**：显示当前用户名。
- **who**：显示当前登录的用户信息。
- **w**：显示当前登录用户及其活动。
- **last**：显示最近登录的用户信息。
- **users**：显示当前登录的用户列表。

### 进程管理

- **top**：实时显示系统进程信息。
- **ps**：进程管理命令，如`ps aux`（显示所有进程）。
- **pstree**：以树状图显示进程信息。
- **pgrep**：查找与指定条件匹配的进程ID。
- **lsof**：列出打开的文件（包括网络套接字），如`lsof -i :80`（列出使用80端口的进程）。
- **jobs_bg_fg**：管理后台作业（bg将作业放入后台，fg将作业调回前台）。
- **kill**：终止进程，如`kill pid`。
- **killall**：根据进程名终止所有匹配的进程。
- **nice_renice**：调整进程的优先级，如`nice -n 10 command`（以低优先级运行命令），`renice 5 -p pid`（调整已运行进程的优先级）。
- **nohup**：使进程在用户注销后继续运行，如`nohup command &`。

### 包管理

- **apt**：Debian及其衍生版（如Ubuntu）的包管理器，如`apt update`，`apt install package`。
- **apt-get**：apt的旧版本命令，功能类似。

### 环境变量和终端操作

- **export**：设置或显示环境变量，如`export VAR_NAME=value`。
- **source**：读取并执行指定文件中的命令，如`source ~/.bashrc`。
- **set_unset**：设置或取消环境变量（set用于显示和设置环境变量，unset用于取消环境变量）。
- **echo**：输出字符串或变量的值到终端。
- **printf**：格式化输出字符串到终端。
- **clear**：清除终端屏幕。
- **history**：显示命令历史记录。
- **login_logout**：登录和注销命令（login用于登录，logout用于注销）。
- **exit**：退出当前shell或终端会话。

### 命令相关

- **xargs**：构建并执行命令行，如`echo "file1 file2" | xargs cat`。
- **exec**：用指定命令替换当前shell进程，如`exec ls`。
- **alias_unalias**：设置或取消命令别名，如`alias ll='ls -l'`，`unalias ll`。
- **type**：显示命令的类型（如内置命令、外部命令等）。

### 时间相关

- **date**：显示或设置系统日期和时间，如`date`，`date -s "2023-04-01 12:00:00"`。
- **cal**：显示日历，如`cal 2023`。
- **crontab**：编辑用户的cron作业表，用于定时执行任务。
- **at_atq_atrm**：at命令用于在指定时间执行一次性任务，atq显示待执行的任务，atrm删除已安排的任务。
- **time**：测量命令的执行时间，如`time ls`。
- **watch**：周期性地执行命令并全屏显示结果，如`watch -n 2 ls`（每2秒执行一次ls）。

### 小工具

- **bc**：任意精度计算器语言，如`echo "scale=2; 3/1" | bc`（计算3除以1并保留两位小数）。
- **ln**：创建硬链接或符号链接，如`ln file link`（创建硬链接），`ln -s file symlink`（创建符号链接）。
- **shutdown_halt_poweroff_reboot**：系统关机、停机、断电或重启命令，如`shutdown -h now`（立即关机），`halt`（停机，某些系统中已弃用），`poweroff`（断电），`reboot`（重启）。

# 3、VS Code 零基础学习笔记

## 1. 安装和认识界面

- **下载 VS Code**： [VS Code 官网](https://code.visualstudio.com/)
- **安装过程**：选择系统对应的安装包并完成安装。
- **界面介绍**：
  - **侧边栏**：包含资源管理器、搜索、源代码管理、调试、扩展等工具。
  - **编辑区**：用于代码编写，支持多文件多标签打开。
  - **状态栏**：显示文件编码、语言模式、行列号、Git 分支等状态信息。
  - **终端窗口**：内嵌终端，便于直接运行代码和管理项目。

## 2. 更改语言 & 了解菜单内容

- **语言切换**：
  - 进入设置（`File > Preferences > Settings`），选择语言选项。
  - 也可通过安装语言包进行界面语言切换，如中文扩展包。
- **菜单内容**：
  - **文件 (File)**：创建新文件、打开文件夹、保存项目。
  - **编辑 (Edit)**：查找、替换、格式化代码。
  - **视图 (View)**：控制界面显示内容（例如侧边栏、调试窗口）。
  - **终端 (Terminal)**：打开/关闭集成终端，支持多终端管理。

## 3. 交互式演练场

- 使用 `Help > Interactive Playground` 进入 VS Code 的交互式学习场景。
- 该模块提供基础功能演练，如代码片段、快速修复、多光标等操作。

## 4. 我所倾向的 VS Code 基础配置

- **主题**：选择护眼的主题（如“Solarized Dark”或“Monokai”）。
- **字体**：推荐字体设置 `Fira Code` 或 `Cascadia Code`，并启用连字功能。
- **自动保存**：进入 `File > Preferences > Settings` 中开启“Auto Save”选项，减少忘记保存的风险。
- **代码格式化**：设置默认格式化工具（如 Prettier），保持代码整洁。
- **快捷键**：熟悉常用快捷键，如 `Ctrl + P` (快速打开文件)、`Ctrl + Shift + P` (命令面板)。

## 5. 前端开发效率利器 Emmet 的使用和配置

- **Emmet** 是内置在 VS Code 中的快速 HTML/CSS 编写工具。
- **配置**：
  - 进入设置 (Settings)，搜索“Emmet”，进行偏好配置。
  - 如想为 JSX 启用 Emmet，需在 `settings.json` 中添加：
    ```json
    "emmet.includeLanguages": {
        "javascript": "javascriptreact"
    }
    ```
- **常用 Emmet 缩写**：
  
  - `div.container>ul>li.item*5` → 自动生成包含 5 个 `li` 的 `div` 和 `ul` 结构。

## 6. 插件 - Live Server

- **安装方法**：打开扩展 (Extensions) 面板，搜索 `Live Server` 并安装。
- **功能**：实时预览 HTML 页面，更改代码后会自动刷新浏览器。
- **使用**：右键 HTML 文件并选择“Open with Live Server”。

## 7. 从源代码编译属于自己的 VS Code

- 从 GitHub 官方仓库克隆 VS Code 源代码。
- 使用 Node.js 和 Yarn 进行项目依赖安装与打包。
- **步骤简述**：
  1. 克隆仓库 `git clone https://github.com/microsoft/vscode.git`
  2. 进入目录并运行 `yarn` 安装依赖。
  3. 使用 `yarn watch` 进行构建，完成后运行 `yarn run electron` 启动。

## 8. Emmet 缩写的展开上限

- Emmet 默认展开上限为 100 个元素，可在设置中调整 `emmet.variables.max_repeat` 值。

## 9. 灵活运用代码片段，代码输入效率翻倍

- **使用代码片段**：VS Code 提供多种预设代码片段。
- **自定义代码片段**：
  - 进入 `File > Preferences > User Snippets` 创建自定义代码片段。
  - 定义格式如下：
    ```json
    "Print to console": {
      "prefix": "log",
      "body": ["console.log('$1');"],
      "description": "Log output to console"
    }
    ```

## 10. 必须掌握的多光标功能

- **多光标添加**：
  - `Alt + Click` (Windows) 或 `Option + Click` (Mac) 可添加多光标。
  - 使用 `Ctrl + D` 快速选中多个相同单词。
- **多行编辑**：按住 `Shift + Alt + Down/Up` 创建多行光标，实现多行同步编辑。

## 11. 鼠标操作的技巧

- **快速选择相同词**：双击单词，并按 `Ctrl + D` (Win) 或 `Cmd + D` (Mac) 继续选择相同单词。
- **代码折叠**：点击代码行号左侧的小箭头可折叠/展开代码块。
- **快速关闭标签**：在标签上点击鼠标中键，快速关闭该标签。

通过以上内容的学习和设置，相信大家可以更高效地使用 VS Code！

# 4、Git 入门到精通全套教程 - 学习笔记

## 目录

1. [Git 官网介绍](#git-官网介绍)
2. [概述](#概述)
   - [版本控制介绍](#版本控制介绍)
   - [分布式版本控制 VS 集中式版本控制](#分布式版本控制-vs-集中式版本控制)
   - [发展历史](#发展历史)
   - [Git 工作机制与代码托管平台](#git-工作机制与代码托管平台)
3. [Git 安装](#git-安装)
4. [Git 基本命令](#git-基本命令)
   - [配置用户信息](#配置用户信息)
   - [初始化仓库](#初始化仓库)
   - [查看仓库状态](#查看仓库状态)
   - [暂存、提交与版本管理](#暂存-提交与版本管理)
5. [分支管理](#分支管理)
   - [分支的创建与切换](#分支的创建与切换)
   - [合并分支与解决冲突](#合并分支与解决冲突)
6. [团队协作](#团队协作)
7. [GitHub 集成](#github-集成)
8. [IDEA 集成](#idea-集成)
9. [码云与 GitLab](#码云与-gitlab)
10. [总结](#总结)

---

## Git 官网介绍

Git 是一款免费的分布式版本控制系统，支持在本地和远程同步版本变更。它最初由 Linus Torvalds 创建，适合各类协作项目的管理。Git 的官方网站为 [https://git-scm.com](https://git-scm.com)。

---

## 概述

### 版本控制介绍

版本控制系统（VCS）可以记录文件随时间的变化历史，使团队成员能够回溯项目任意版本，特别是在多人协作时有助于管理代码变化。

### 分布式版本控制 VS 集中式版本控制

- **集中式版本控制**：依赖中央服务器存储所有代码版本，用户必须连入服务器才能协作。
- **分布式版本控制**：每个开发者拥有完整的仓库副本，可以在本地管理、更新和回退版本。

### 发展历史

Git 由 Linus Torvalds 于 2005 年发布，随着开源软件的发展，Git 逐渐成为开源社区的标准。

### Git 工作机制与代码托管平台

Git 使用快照记录文件，支持快速创建和管理分支。代码托管平台（如 GitHub、Gitee、GitLab）提供便捷的仓库托管、协作功能。

---

## Git 安装

1. 在官网下载安装：[https://git-scm.com/downloads](https://git-scm.com/downloads)
2. 使用命令行验证安装：

   ```bash
   git --version
   ```

3. 配置用户信息：

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

---

## Git 基本命令

### 配置用户信息

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

可通过 `--global` 参数设置全局用户名和邮箱。

### 初始化仓库

在项目根目录下初始化 Git 仓库：

```bash
git init
```

初始化后，Git 会创建一个 `.git` 文件夹，用于存储本地库的所有信息。

### 查看仓库状态

查看当前工作区与暂存区状态，包括文件的改动、添加、删除等：

```bash
git status
```

### 暂存、提交与版本管理

1. 添加文件到暂存区：

   ```bash
   git add <filename>
   git add .  # 添加所有改动
   ```

2. 提交到本地库：

   ```bash
   git commit -m "提交描述信息"
   ```

3. 查看提交日志：

   ```bash
   git log  # 显示详细的提交日志
   git log --oneline  # 简略显示
   ```

4. 查看提交的差异：

   ```bash
   git diff  # 显示工作区与暂存区的差异
   git diff --staged  # 显示暂存区与本地库的差异
   ```

---

## 分支管理

### 分支的创建与切换

分支使得开发多个功能独立进行，避免主分支的代码冲突和不稳定。

1. 查看当前分支：

   ```bash
   git branch
   ```

2. 创建分支：

   ```bash
   git branch <branch-name>
   ```

3. 切换分支：

   ```bash
   git checkout <branch-name>
   ```

4. 创建并切换新分支：

   ```bash
   git checkout -b <branch-name>
   ```

### 合并分支与解决冲突

1. 合并分支：

   切换到主分支并合并：

   ```bash
   git checkout main
   git merge <branch-name>
   ```

2. 解决冲突：

   Git 会标记冲突位置，手动编辑并解决冲突后：

   ```bash
   git add <filename>
   git commit -m "解决冲突描述"
   ```

---

## 团队协作

Git 提供分布式版本控制，适用于不同场景的协作。

### 团队内协作

1. 创建远程仓库并推送：

   ```bash
   git remote add origin <repository-url>
   git push -u origin main
   ```

2. 拉取远程仓库更新：

   ```bash
   git pull origin main
   ```

### 跨团队协作

1. Fork 项目：在 GitHub 上 fork 他人的项目，建立自己版本的副本。
2. 提交 Pull Request：在自己的项目仓库修改后，发起 Pull Request 请求，将代码合并回原始项目。

---

## GitHub 集成

1. 创建远程仓库并设置别名：

   ```bash
   git remote add origin <repository-url>
   ```

2. 推送代码：

   ```bash
   git push -u origin main
   ```

3. 克隆远程仓库：

   ```bash
   git clone <repository-url>
   ```

4. SSH 免密登录：

   ```bash
   ssh-keygen -t rsa -C "your.email@example.com"
   ```

   将生成的公钥添加到 GitHub 账户中。

---

## IDEA 集成

1. 设置 Git：在 IDEA 设置中指定 Git 安装路径。
2. 创建本地仓库：在 IDEA 中点击 `Git > Enable Version Control Integration` 以初始化本地仓库。
3. 添加和提交：右键文件或项目，选择 `Git > Commit` 提交变更。
4. 分支管理：在 IDEA 的 Git 工具窗口中可以创建、切换、合并分支。
5. 推送与拉取：在 IDEA 中可以方便地将项目推送到远程仓库或拉取更新。

---

## 码云与 GitLab

### 码云

1. 注册并创建远程仓库：Gitee 是国内常用的代码托管平台。
2. IDEA 集成 Gitee：在 IDEA 中通过 `VCS > Gitee` 集成管理。

### GitLab

1. 安装 GitLab：GitLab 支持自建服务器，适合企业内部使用。
2. 创建仓库并设置访问权限：管理员可以为用户和团队分配仓库权限，满足内网环境下的协作需求。