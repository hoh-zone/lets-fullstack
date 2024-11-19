# MOVE共学营基础课程

# 速学150个Linux常用命令笔记

## Linux目录结构介绍
- **目录结构**：详细介绍`/`根目录下的各个子目录及用途。
- **系统文件或目录颜色的含义**：解释不同颜色代表的文件类型。
- **常用终端快捷键**：常用的快捷键如Ctrl+C, Ctrl+D等。
- **Tab键的妙用**：自动补全路径和命令。

### 实践代码
```bash
# 查看当前目录
pwd

# 列出当前目录内容
ls

# 切换到根目录
cd /

# 列出根目录下的所有文件和目录
ls -l /
```

## 文件权限与通配符
- **文件权限介绍**：rwx权限及其表示方法。
- **通配符介绍**：`*`, `?`, `[ ]`等通配符的使用。

### 实践代码
```bash
# 显示文件权限
ls -l

# 改变文件权限
chmod 755 myfile.txt

# 使用通配符
ls *.txt
```

## 帮助命令
- **man**：查看命令的手册页。
- **info**：提供更详细的帮助信息。
- **whatis**：快速查询命令的功能。

### 实践代码
```bash
# 查看ls命令的手册页
man ls

# 查看ls命令的info页面
info ls

# 查询ls命令的功能
whatis ls
```

## 文件和目录管理
- **touch**：创建空文件或更新时间戳。
- **mkdir**：创建目录。
- **rm**：删除文件。
- **rmdir**：删除空目录。
- **mv**：移动或重命名文件。
- **cp**：复制文件。
- **cd**：切换目录。
- **pwd**：显示当前工作目录。
- **ls**：列出目录内容。
- **tree**：以树状图展示目录结构。
- **stat**：显示文件状态信息。
- **rename**：批量重命名文件。
- **basename**：提取文件名。
- **dirname**：提取路径中的目录部分。
- **chattr** 和 **lsattr**：修改和查看文件属性。
- **file**：识别文件类型。
- **md5sum**：生成和校验文件的MD5值。

### 实践代码
```bash
# 创建一个空文件
touch myfile.txt

# 创建一个新目录
mkdir mydir

# 删除文件
rm myfile.txt

# 删除空目录
rmdir mydir

# 移动或重命名文件
mv oldname.txt newname.txt

# 复制文件
cp source.txt destination.txt

# 切换到新目录
cd /path/to/directory

# 显示当前目录
pwd

# 列出当前目录内容
ls

# 以树状图展示目录结构
tree

# 显示文件状态信息
stat myfile.txt

# 批量重命名文件
rename 's/old/new/' *.txt

# 提取文件名
basename /path/to/file.txt

# 提取路径中的目录部分
dirname /path/to/file.txt

# 修改文件属性
chattr +i myfile.txt

# 查看文件属性
lsattr myfile.txt

# 识别文件类型
file myfile.txt

# 生成和校验文件的MD5值
md5sum myfile.txt
```

## 查找文件
- **find**：查找文件或目录。
- **which**：查找可执行文件的位置。
- **whereis**：查找二进制文件、源代码和手册页。
- **locate**：通过数据库快速查找文件。

### 实践代码
```bash
# 查找当前目录下所有的.txt文件
find . -name "*.txt"

# 查找可执行文件的位置
which ls

# 查找二进制文件、源代码和手册页
whereis ls

# 通过数据库快速查找文件
locate myfile.txt
```

## 用户和组管理
- **chown**：改变文件的所有者。
- **chgrp**：改变文件的所属组。
- **chmod**：改变文件的权限。

### 实践代码
```bash
# 改变文件的所有者
chown user:group myfile.txt

# 改变文件的所属组
chgrp group myfile.txt

# 改变文件的权限
chmod 755 myfile.txt
```

## 文本处理
- **grep**：文本搜索工具。
- **egrep**：扩展正则表达式搜索。
- **cat**：查看文本内容。
- **more**：逐页阅读文本。
- **less**：分页查看文本内容。
- **head**：查看文件开头内容。
- **tail**：查看文件尾部内容。
- **tac**：反向显示文本内容。
- **nl**：统计文件行号。
- **wc**：统计文本字数信息。
- **split**：文件切割。
- **cut**：文本截取。
- **paste**：文件合并。
- **sort**：文本内容排序。
- **uniq**：去除重复行。
- **diff** 和 **patch**：比较差异并打补丁。
- **join**：连接两个文件。
- **tr**：字符转换。
- **sed**：流编辑器。
- **awk**：编程语言。

### 实践代码
```bash
# 搜索包含"hello"的行
grep "hello" myfile.txt

# 扩展正则表达式搜索
egrep "hello|world" myfile.txt

# 查看文本内容
cat myfile.txt

# 逐页阅读文本
more myfile.txt

# 分页查看文本内容
less myfile.txt

# 查看文件开头内容
head myfile.txt

# 查看文件尾部内容
tail myfile.txt

# 反向显示文本内容
tac myfile.txt

# 统计文件行号
nl myfile.txt

# 统计文本字数信息
wc -l myfile.txt

# 文件切割
split -b 10m largefile.txt part_

# 文本截取
cut -d' ' -f1 myfile.txt

# 文件合并
paste file1.txt file2.txt > combined.txt

# 文本内容排序
sort myfile.txt

# 去除重复行
uniq myfile.txt

# 比较差异
diff file1.txt file2.txt

# 应用补丁
patch < patchfile.patch

# 连接两个文件
join file1.txt file2.txt

# 字符转换
tr 'a-z' 'A-Z' < myfile.txt

# 流编辑器
sed 's/hello/world/g' myfile.txt

# awk编程语言
awk '{print $1}' myfile.txt
```

## 系统信息
- **uname**：显示系统信息。
- **hostname**：显示或设置主机名。
- **dmesg**：显示开机信息。
- **uptime**：查看系统负载。
- **free**：显示内存使用情况。
- **ulimit**：限制系统资源。
- **init**：切换系统运行级别。
- **service**：控制系统服务。
- **vmstat**：显示虚拟内存状态。
- **iostat**：监视系统输入输出设备和CPU的使用情况。
- **ipcs**：显示进程间通信设备状态。
- **ipcrm**：删除指定IPC资源。

### 实践代码
```bash
# 显示系统信息
uname -a

# 显示或设置主机名
hostname

# 显示开机信息
dmesg

# 查看系统负载
uptime

# 显示内存使用情况
free -h

# 限制系统资源
ulimit -a

# 切换系统运行级别
init 3

# 控制系统服务
service ssh status

# 显示虚拟内存状态
vmstat

# 监视系统输入输出设备和CPU的使用情况
iostat

# 显示进程间通信设备状态
ipcs

# 删除指定IPC资源
ipcrm -m 123456
```

## 网络相关命令
- **route**：显示并设置IP路由表。
- **ping**：网络连通测试。
- **traceroute**：追踪数据包传输路径。
- **ifconfig**：显示或设置网络设备参数。
- **ifup** 和 **ifdown**：激活禁用网络接口。
- **netstat**：查看网络相关信息。
- **ss**：显示活动套接字信息。
- **telnet**：远程登陆服务器。
- **ssh**：安全连接服务器。
- **ftp**：文件传输命令。
- **sftp**：交互式文件传输程序。
- **lftp**：下载工具。
- **wget**：网络下载工具。
- **scp**：远程文件拷贝。
- **curl**：远程数据传输工具。
- **host**：分析域名查询工具。
- **tcpdump**：数据抓包工具。
- **nc**：网络检测工具。

### 实践代码
```bash
# 显示并设置IP路由表
route -n

# 网络连通测试
ping www.example.com

# 追踪数据包传输路径
traceroute www.example.com

# 显示或设置网络设备参数
ifconfig

# 激活禁用网络接口
ifup eth0
ifdown eth0

# 查看网络相关信息
netstat -an

# 显示活动套接字信息
ss -tulwn

# 远程登陆服务器
telnet www.example.com 80

# 安全连接服务器
ssh user@remote_host

# 文件传输
ftp remote_host

# 交互式文件传输
sftp user@remote_host

# 下载工具
lftp

# 网络下载工具
wget http://example.com/file.zip

# 远程文件拷贝
scp user@remote_host:/path/to/file /local/path

# 远程数据传输工具
curl -O http://example.com/file.zip

# 分析域名查询
host www.example.com

# 数据抓包工具
tcpdump -i eth0

# 网络检测工具
nc -zv www.example.com 80
```

## 用户管理
- **useradd**：创建用户。
- **adduser**：创建用户（交互式）。
- **passwd**：修改用户密码。
- **userdel**：删除用户。
- **su**：切换用户。
- **sudo**：以其他身份来执行命令。
- **id**：显示用户ID信息。
- **usermod**：修改用户信息。
- **groups**：显示用户组。
- **groupadd**：创建用户组。
- **groupdel**：删除用户组。
- **whoami**：显示当前用户名。
- **who**：显示当前登录用户。
- **w**：显示当前登录用户及其活动。
- **last**：显示最近登录的用户。
- **users**：显示当前登录的用户列表。

### 实践代码
```bash
# 创建用户
useradd newuser

# 创建用户（交互式）
adduser newuser

# 修改用户密码
passwd newuser

# 删除用户
userdel newuser

# 切换用户
su - newuser

# 以其他身份来执行命令
sudo command

# 显示用户ID信息
id newuser

# 修改用户信息
usermod -c "New User" newuser

# 显示用户组
groups newuser

# 创建用户组
groupadd newgroup

# 删除用户组
groupdel newgroup

# 显示当前用户名
whoami

# 显示当前登录用户
who

# 显示当前登录用户及其活动
w

# 显示最近登录的用户
last

# 显示当前登录的用户列表
users
```

## 进程管理
- **top**：查看系统进程。
- **ps**：显示进程信息。
- **pstree**：显示进程树。
- **pgrep**：根据名称查找进程。
- **lsof**：列出打开的文件。
- **jobs**：显示后台作业。
- **bg** 和 **fg**：将作业放到后台或前台。
- **kill**：终止进程。
- **killall**：终止所有匹配的进程。
- **nice** 和 **renice**：设置进程优先级。
- **nohup**：忽略挂起信号运行命令。

### 实践代码
```bash
# 查看系统进程
top

# 显示进程信息
ps aux

# 显示进程树
pstree

# 根据名称查找进程
pgrep process_name

# 列出打开的文件
lsof

# 显示后台作业
jobs

# 将作业放到后台
bg %1

# 将作业放到前台
fg %1

# 终止进程
kill 12345

# 终止所有匹配的进程
killall process_name

# 设置进程优先级
nice -n 10 command
renice 10 -p 12345

# 忽略挂起信号运行命令
nohup command &
```

## 包管理
- **apt** 和 **apt-get**：包管理器。
- **export**：导出环境变量。
- **source**：读取并执行文件中的命令。
- **set** 和 **unset**：设置和取消环境变量。

### 实践代码
```bash
# 更新包列表
apt update

# 安装软件包
apt install package_name

# 卸载软件包
apt remove package_name

# 导出环境变量
export PATH=$PATH:/new/path

# 读取并执行文件中的命令
source script.sh

# 设置环境变量
set variable=value

# 取消环境变量
unset variable
```

## 终端操作
- **echo**：显示消息。
- **printf**：格式化输出。
- **clear**：清屏。
- **history**：显示历史命令。
- **login** 和 **logout**：登录和注销。
- **exit**：退出终端。

### 实践代码
```bash
# 显示消息
echo "Hello, World!"

# 格式化输出
printf "Name: %s\nAge: %d\n" "John" 30

# 清屏
clear

# 显示历史命令
history

# 登录
login

# 注销
logout

# 退出终端
exit
```

## 其他命令
- **xargs**：构建和执行命令行。
- **exec**：替换当前shell。
- **alias** 和 **unalias**：定义和取消别名。
- **type**：显示命令类型。
- **date**：显示或设置日期。
- **cal**：显示日历。
- **crontab**：定时任务。
- **at**：一次性定时任务。

### 实践代码
```bash
# 构建和执行命令行
echo "file1 file2" | xargs rm

# 替换当前shell
exec bash

# 定义别名
alias ll='ls -l'

# 取消别名
unalias ll

# 显示命令类型
type ls

# 显示或设置日期
date
date -s "2023-10-01 12:00:00"

# 显示日历
cal

# 编辑定时任务
crontab -e

# 添加一次性定时任务
echo "echo Hello, World!" | at now + 1 minute
```
