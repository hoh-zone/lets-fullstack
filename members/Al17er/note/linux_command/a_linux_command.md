## man
- 用法：man + 命令
- 用途：当我们不知道一个命令的使用方法可以使用man获取该命令的使用说明书。
- 案例：man rm

![alt text](image.png)

## info
- 用法：info + 命令
- 用途: 获取命令帮助信息
- 案例：info rm

![alt text](image-1.png)

## whatis
- 用法：whatis + 命令
- 用途: 获取命令帮助信息(精简版)
- 案例：whatis man

![alt text](image-2.png)

## touch 
- 用法: touch + 文件名
- 用途: 创建文件
- 案例: touch Al17er

![alt text](image-3.png)

## mkdir
- 用法: mkdir + 目录名
- 用途: 创建文件夹
- 案例: mkdir Al17er

![alt text](image-4.png)

## rm
- 用法: rm + 文件名
- 用途: 删除文件或目录
- 案例: rm -rf Al17er

![alt text](image-5.png)


## rmdir
- 用法: rmdir + 目录名
- 用途: 删除空目录
- 案例: rmdir Al17er

![alt text](image-6.png)

## mv
- 用法: mv 源文件 重命名后文件
- 用途: 重命名文件或文件夹
- 案例: mv test Al17er

![alt text](image-7.png)

## cp
- 用法: cp 源文件 目的文件
- 用途: 复制文件或文件夹
- 案例: cp -r Al17er test

![alt text](image-8.png)

## cd 
- 用法: cd 目录路径
- 用途: 改变路径
- 案例: cd Al17er

![alt text](image-9.png)

## pwd 
- 用法: pwd
- 用途: 查看当前所在路径
- 案例: pwd

![alt text](image-10.png)

## ls
- 用法: ls 目录路径
- 用途: 列出目录文件
- 案例: ls

![alt text](image-11.png)

## tree
- 用法: tree
- 用途: 查看目录结构
- 案例: tree /opt

![alt text](image-12.png)


## stat
- 用法: stat 文件名
- 用途: 查看当前文件属性
- 案例: stat test

![alt text](image-13.png)

## rename
- 用法: rename 's/old/new/' files
- 用途: 批量重命名文件
- 案例: rename 's/h/a/' *.h

![alt text](image-15.png)


## basename
- 用法: basename /path/to/somefile.txt
- 用途: 从给定的文件名或路径中提取出基本文件名
- 案例: basename 1.h .h

![alt text](image-16.png)


## dirname
- 用法: dirname /root/move
- 用途: 提取命令中的目录部分
- 案例: dirname /root/move

![alt text](image-17.png)

## file
- 用法: file 文件名
- 用途: 判断文件类型
- 案例: file /dev/sda

 ![alt text](image-18.png)

## md5sum 
- 用法: md5sum 文件名
- 用途: 计算文件md5值
- 案例: md5sum 1.h

![alt text](image-19.png)

## find 
- 用法: find 
- 用途: 查找文件
- 案例: find /root/ -name 1.h

![alt text](image-20.png)

## which
- 用法: which + 命令
- 用途: 搜索命令所在路径
- 案例: which ls

![alt text](image-21.png)


## whereis
- 用法: whereis + 命令
- 用途: 定位命令所在文件
- 案例: whereis ls

![alt text](image-22.png)

## locat 
- 用法:locat string
- 用途:快速查找包含指定字符的文件
- 案例:locat 1.h

![alt text](image-23.png)

## chown 
- 用法: chown 用户:组 文件
- 用途: 改变文件或目录的所有者和组。
- 案例: chown root:root 1.h

![alt text](image-24.png)

## chgrp
- 用法: chgrp 组 文件
- 用途: 改变文件或目录的所属组。
- 案例: chgrp alter 1.h

![alt text](image-25.png)

## chmod
- 用法: chmod 模式 文件
- 用途: 改变文件或目录的访问权限。
- 案例: chmod 755 1.h

![alt text](image-26.png)

## grep
- 用法: grep string
- 用途: 在文件中搜索与给定模式匹配的行，并将这些行打印到标准输出。
- 案例: ls -l /etc |grep ssh

![alt text](image-27.png)


## egrep
- 用法: egrep '正则' string
- 用途: grep 的一个变体，它默认使用扩展正则表达式
- 案例: ls -l /etc |egrep ssh

![alt text](image-28.png)


## cat
- 用法: cat 文件名
- 用途: 查看文件内容
- 案例: cat 1.h

![alt text](image-29.png)

## more
- 用法: more 文件
- 用途: 按页显示文本内容
- 案例: more 1.h

![alt text](image-30.png)

## less
- 用法: less 文件
- 用途: 分页展示文本内容
- 案例: less 1.h

![alt text](image-31.png)


## head
- 用法: head 文件名
- 用途: 显示文件前几行
- 案例: head -n 5 1.h

![alt text](image-32.png)

## tail 
- 用法: tail 文件名
- 用途: 显示文件后几行
- 案例: tail -n 5 1.h

![alt text](image-33.png)

## tac
- 用法: tac 文件名
- 用途: 从后往前输出文本内容
- 案例: tac 1.h

![alt text](image-34.png)

## nl
- 用法: nl 文件名
- 用途: 统计文本行数
- 案例: nl 1.h

![alt text](image-35.png)

## wc
- 用法: wc 文件名
- 用途: 统计文件字数
- 案例: wc 1.h

![alt text](image-36.png)


## splt
- 用法: split 输入文件 输出文件
- 用途: 将一个大文件分割成多个小文件。可以按行数、字节数或大小来分割文件。
- 案例: split -l 3 1.h part1_

![alt text](image-37.png)


## cut
- 用法: cut 文件名
- 用途: 从文件的每一行中提取部分内容。可以基于字符、字段或字节来选择要提取的部分。
- 案例: cut -c1-5 1.h

![alt text](image-38.png)

## paste
- 用法: paste 文件1 文件2
- 用途: 将多个文件的内容按行合并，并使用制表符或其他指定的分隔符进行分隔。
- 案例: paste -d '|' 1.h 2.h

![alt text](image-39.png)


## groupadd
- 用法: groupadd 组名称
- 用途: 添加用户组
- 案例: groupadd test

![alt text](image-40.png)


## groupdel
- 用法: groupdel 组名称
- 用途: 删除用户组
- 案例: groupdel test

![alt text](image-41.png)

## sort
- 用法: sort 文件名
- 用途: 对文本文件中的行进行排序。默认升序。
- 案例: sort 1.h

![alt text](image-42.png)


## unip
- 用法: uniq 文件名
- 用途: 去重复
- 案例: uniq 1.h

![alt text](image-43.png)

## diff 
- 用法: diff 文件1 文件2
- 用途: 比较2个文件差异
- 案例: diff 1.h 2.h

![alt text](image-44.png)


## patch
- 用法: patch 原文件 < 补丁文件
- 用途: 根据 diff 生成的补丁文件对文件进行修改。patch 可以应用或回滚文件的变化。
- 案例: 这个命令用不到，有请下一位

## join
- 用法: join 文件1 文件2
- 用途: 将两个文件基于共同字段（通常是第一列）进行连接，并输出匹配的行。
- 案例: join 1.h 2.h

![alt text](image-45.png)

## tr 
- 用法: tr 字符集1 字符集2
- 用途: 用于字符的转换或删除。tr 可以将一组字符转换为另一组字符，或者删除某些字符。
- 案例: tr '[:lower:]' '[:upper:]' < 1.h

![alt text](image-46.png)


## sed
- 用法: sed '正则' 文件
- 用途: 用于对输入流（文件或管道）进行基本的文本转换。
- 案例: sed '1,5d' 1.h

![alt text](image-47.png)

## awk
- 用法: awk '正则' 文件名
- 用途: 处理文本文件中的数据，进行复杂的模式匹配、字段操作、数学运算等。
- 案例: awk -F, '{print $1}' 1.h

![alt text](image-48.png)


## usermod
- 用法: usermod 用户名
- 用途: 用于修改现有用户的属性。可以更改用户的登录名、主目录、默认 shell、用户组等。
- 案例: usermod -l haha heihei

![alt text](image-49.png)


## groups
- 用法: groups 用户名
- 用途: 显示一个或多个用户所属的所有组
- 案例: groups root

![alt text](image-50.png)


## awk
- 用法: awk '正则' 文件名
- 用途: 处理文本文件中的数据，进行复杂的模式匹配、字段操作、数学运算等。
- 案例: awk '{print $1}' 1.h

![alt text](image-51.png)


## du
- 用法: du 文件|目录
- 用途: 显示文件和目录的磁盘使用情况。
- 案例: du -h 1.h

![alt text](image-52.png)


## df
- 用法: df 文件系统
- 用途: 显示文件系统的磁盘空间使用情况。
- 案例: df -h /root

![alt text](image-53.png)


## sync
- 用法: sync
- 用途: 将内存中的所有未写入数据（脏页）同步到磁盘。
- 案例: sync

![alt text](image-54.png)

## mount
- 用法: mount 磁盘 挂载目录
- 用途: 挂载磁盘
- 案例: mount /dev/sda /opt

## umount
- 用法: umount 挂载目录
- 用途: 取消挂载
- 案例: umount /opt

## dd
- 用法: dd
- 用途: 用于从一个文件或设备复制数据到另一个文件或设备。
- 案例: dd if=1.h of=dd.h

![alt text](image-55.png)

## tar
- 用法: tar 压缩包
- 用途: 解压或压缩文件
- 案例: tar -cvf 11.tar 1.h

![alt text](image-56.png)


## zip_unzip
- 用法: zip|unzip 压缩包名
- 用途: 解压或压缩文件
- 案例: unzip 1.zip

![alt text](image-57.png)


## gzip_gunzip
- 用法: gzip|gunzip 压缩包名
- 用途: 解压或压缩文件
- 案例: gzip 1.h

![alt text](image-58.png)


## uname
- 用法: uname 
- 用途: 查看系统信息
- 案例: uname -a

![alt text](image-59.png)


## hostname
- 用法:hostname
- 用途:查看主机名
- 案例: hostname

![alt text](image-60.png)

## dmesg
- 用法: dmesg
- 用途: 显示或控制内核环形缓冲区中的消息。
- 案例: dmesg

![alt text](image-61.png)


## 
- 用法:uptime
- 用途:查看系统资源使用情况
- 案例:uptime

![alt text](image-62.png)


## free
- 用法: free
- 用途: 查看内存使用情况
- 案例: free -m

![alt text](image-63.png)


## ulimit
- 用法: ulimit
- 用途: 用于控制 shell 启动进程可用的系统资源。
- 案例: 这个命令可不敢随便用，有请下一位。

## init
- 用法: init 3|5|6|0
- 用途: 切换系统运行级别
- 案例: 0：关机 3：图形 5:最小化 6:重启

## service
- 用法: service 服务名 指令
- 用途: 操作系统服务运行
- 案例: service frpc status

![alt text](image-64.png)


## vmstat
- 用法: vmstat
- 用途: 显示虚拟内存状态
- 案例: vmstat

![alt text](image-65.png)


## iostat
- 用法: iostat
- 用途: 监视系统输入输出设备和CPU的使用情况命令
- 案例: iostat

![alt text](image-66.png)


## ipcs
- 用法: ipcs
- 用途: 显示进程间通信设备状态命令
- 案例: ipcs

![alt text](image-67.png)


## ipcrm
- 用法: ipcrm
- 用途: 删除指定ipc资源
- 案例: 这个命令可不敢乱删，有请下一位。

## route
- 用法: route
- 用途: 查看路由表
- 案例: route

![alt text](image-68.png)

## ping
- 用法: ping ip
- 用途: 测试icmp
- 案例: ping www.baidu.com

![alt text](image-69.png)


## traceroute
- 用法: traceroute ip
- 用途: 路由追踪，用于网络排错。
- 案例: traceroute www.baidu.com

![alt text](image-70.png)

## ifconfig
- 用法: ifconfig
- 用途: 查看本机网络配置。
- 案例: ifconfig

![alt text](image-71.png)


## ifup
- 用法: ifup 接口
- 用途: 启用网络接口
- 案例: ifup eth0

## ifdown
- 用法: ifdown 接口
- 用途: 关闭网络接口
- 案例: ifdown eth0

## netstat
- 用法: netstat 
- 用途: 查看端口开放情况
- 案例: netstat -ano

![alt text](image-72.png)


## ss
- 用法: ss
- 用途: 显示活动套接字信息命令
- 案例: ss

![alt text](image-73.png)

## telnet
- 用法: telnet ip
- 用途: 远程连接服务器，常用来测试端口开放情况
- 案例: telnet www.baidu.com 80

![alt text](image-74.png)


## ssh
- 用法: ssh 用户名@ip
- 用途: 远程登录服务器
- 案例: ssh root@127.0.0.1:3223

![alt text](image-75.png)


## ftp
- 用法: ftp ip
- 用途: 连接目标ftp服务
- 案例: ftp 127.0.0.1

![alt text](image-76.png)


## sftp
- 用法: sftp ip
- 用途: 加密文件传输
- 案例: 使用crt连接

![alt text](image-77.png)


## lftp
- 用法: lftp ftp://用户名:密码@ftp.xx.com
- 用途: 功能强大的文件传输程序
- 案例: 不常用，了解即可。

## wget
- 用法: wget + url地址
- 用途: 下载文件到本地。
- 案例: wget www.baidu.com

![alt text](image-78.png)


## scp
- 用法: scp 源文件 目标文件
- 用途: 远程拷贝文件
- 案例: 不常用命令。

## curl
- 用法: curl url
- 用途: 向目标地址发起http请求。
- 案例: curl www.baidu.com

![alt text](image-79.png)


## host
- 用法: host 域名
- 用途: 用于执行 DNS 查询的命令行工具。可以用来查询域名.
- 案例: host www.baidu.com 114.114.114.114

![alt text](image-80.png)


## tcpdump
- 用法: tcpdump
- 用途: 抓包网络请求数据包。
- 案例: tcpdump -i wlp2s0

![alt text](image-81.png)


## nc
- 用法: nc 主机 端口
- 用途: 常用于创建 TCP 或 UDP 连接，监听端口，传输文件，进行端口扫描等。
- 案例: nc -l -p 1233

![alt text](image-82.png)


## useradd
- 用法: useradd 用户名
- 用途: 添加用户
- 案例: useradd test

![alt text](image-83.png)


## adduser
- 用法: adder 用户名
- 用途: 创建用户
- 案例: adduser test123

![alt text](image-84.png)


## passwd
- 用法: passwd 用户名
- 用途: 为用户添加或修改密码
- 案例: passwd test

![alt text](image-85.png)


## userdel
- 用法: userdel 用户名
- 用途: 删除用户
- 案例: userdel test

![alt text](image-86.png)


## su
- 用法: su 用户名
- 用途: 切换用户
- 案例: su alter

![alt text](image-87.png)


## sudo
- 用法: sudo 命令
- 用途: 以超级用户权限执行命令
- 案例: sudo whereis ls

![alt text](image-88.png)

## id
- 用法: id
- 用途: 查看当前用户信息
- 案例: id

![alt text](image-89.png)


## whoami
- 用法: whoami
- 用途: 查看当前登录用户
- 案例: whoami

![alt text](image-90.png)

## who
- 用法: who
- 用途: 查看当前在线用户
- 案例: who

![alt text](image-91.png)



## w
- 用法: w
- 用途: 查看当前在线用户
- 案例: w

![alt text](image-92.png)


## last
- 用法: last
- 用途: 显示最近登录用户日志
- 案例: last

![alt text](image-93.png)


## users
- 用法:users
- 用途: 查看当前用户信息
- 案例: users

![alt text](image-94.png)

## top
- 用法: top
- 用途: 查看系统资源占用情况
- 案例: top

![alt text](image-95.png)


## ps
- 用法: ps 
- 用途: 查看当前系统运行进程信息
- 案例: ps -ef

![alt text](image-96.png)

## pstree
- 用法: pstree
- 用途: 以进程树方式显示当前系统运行进程。
- 案例: pstree

![alt text](image-97.png)

## pgrep
- 用法: pgrep 进程名
- 用途: 获取当前进程id
- 案例: pgrep frp

![alt text](image-98.png)


## lsof
- 用法:lsof
- 用途: 列出所有进程打开的文件
- 案例: lsof

![alt text](image-99.png)

## jobs
- 用法:jobs
- 用途:查看后台进程
- 案例:jobs

![alt text](image-100.png)


## bg
- 用法: bg
- 用途: 将前台进程转至后台运行
- 案例: bg

## fg
- 用法: fg
- 用途: 将后台进程转至前台运行
- 案例: fg

## kill
- 用法:kill 进程名
- 用途:关闭进程
- 案例:kill -9 frp

## killall
- 用法: killall 进程名
- 用途: 关闭所有同进程名的进程
- 案例: killall -9 frp

## nice
- 用法: nice 命令
- 用途: 用于启动一个新进程，并为其设置一个不同的调度优先级。
- 案例: nice free

![alt text](image-101.png)

## renice
- 用法: renice 优先级 进程号
- 用途: 用于改变已运行进程的调度优先级。
- 案例: renice 5 -p 2981

## nohup
- 用法: nohup 命令
- 用途: 运行命令并挂在后台
- 案例: nohup ls

![alt text](image-102.png)

## apt
- 用法: apt 操作 报包
- 用途: 包管理器
- 案例: apt install vim

![alt text](image-103.png)


## apt-get 
- 用法: apt-get 操作 包名
- 用途: 包管理器，apt的全命令
- 案例: apt-get install vim

![alt text](image-104.png)


## export
- 用法:export 变量名
- 用途:用于设置环境变量
- 案例:export aaa=123

![alt text](image-105.png)


## source
- 用法:source 文件
- 用途:立即加载文件变量
- 案例:source ~/.cargo/env

![alt text](image-106.png)


## set|unset
- 用法:set|unset 变量名=123
- 用途:设置或取消环境变量
- 案例:set aaa=123 | unset aaa

![alt text](image-107.png)


## echo
- 用法:echo string
- 用途:输出文本
- 案例:echo "123"

![alt text](image-108.png)


## printf
- 用法: printf string
- 用途: 不接换行符打印文本
- 案例: printf aaaa

![alt text](image-109.png)


## clear
- 用法: clear
- 用途: 清屏
- 案例: clear

![alt text](image-110.png)


## history
- 用法: history
- 用途: 查看历史记录
- 案例: history

![alt text](image-111.png)



## login_logout
- 用法:login_logout
- 用途:登录|登出

## exit
- 用法: exit
- 用途: 退出并关闭终端

## xargs
- 用法: xargs 命令
- 用途: 强大的命令行工具，用于从标准输入构建和执行命令。
- 案例: ls | xargs echo 

![alt text](image-112.png)

## exec
- 用法: exec 命令
- 用途: 执行完当前命令后关闭终端
- 案例: exec ls

![alt text](image-113.png)


## alias_unalias
- 用法: alias_unalias 别名="执行操作"
- 用途: 设置别名操作命令
- 案例: alias lp="ls -l"

![alt text](image-114.png)


## type
- 用法: type 命令
- 用途: 用于显示给定命令的类型。它可以告诉你一个命令是内置命令、外部命令（可执行文件）、函数还是别名。
- 案例: type ls

![alt text](image-115.png)

## date
- 用法:date
- 用途:显示时间
- 案例:date

![alt text](image-116.png)


## cal 
- 用法: cal 日期
- 用途: 命令用于显示当前月份的日历或指定月份/年份的日历。
- 案例: ubuntu未找到该命令

## crontab
- 用法:crontab 
- 用途: 设置定时任务
- 案例: crontab -l

![alt text](image-117.png)


## at
- 用法: at 时间
- 用途: 设置一次性计划任务
- 案例: echo "echo Hello, World!" | at now + 1 minutes

![alt text](image-118.png)


## atq
- 用法: atq
- 用途: 列出所有已安排的任务。
- 案例: atq

![alt text](image-119.png)

 
## atrm
- 用法: atrm 任务号
- 用途: 用于删除已安排的 at 任务。
- 案例: atrm 2

![alt text](image-120.png)


## time 
- 用法: time 命令
- 用途: 测量命令执行时间
- 案例: time ls

![alt text](image-121.png)


## watch
- 用法: watch 命令
- 用途: 每隔一段时间执行一次命令
- 案例: watch -n 2 ls

![alt text](image-122.png)


## bc 
- 用法: bc 
- 用途: 任意精度计算器语言。它可以处理非常大的数字，并且支持基本的算术运算、变量定义、条件语句等。
- 案例: echo "2 + 2" | bc

![alt text](image-123.png)


## ln
- 用法: ln 源文件 目的路径
- 用途: 创建软连接
- 案例: ln -s 1.h 9.h

![alt text](image-124.png)

## shutdown
- 用法: shutdown
- 用途: 关机


## halt
- 用法: halt
- 用途: 用于关闭系统。它会停止所有运行中的进程，并将系统置于一个可以安全断电的状态。

## poweroff
- 用法: poweroff
- 用途: 关机

## reboot
- 用法: reboot
- 用途: 重启
