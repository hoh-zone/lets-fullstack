# MOVE共学营基础课程之Windows DOS命令\批处理脚本笔记

视频教程地址：
[https://www.bilibili.com/video/BV1Qv411q7bN)


# Windows DOS命令与批处理脚本学习笔记

## 批处理初体验
- **概念**：.bat文件是包含一系列DOS命令的文本文件。
- **创建和运行**：
  - 创建一个简单的批处理文件`hello.bat`，内容如下：
    ```batch
    @echo off
    echo Hello, World!
    pause
    ```

## 批处理运算操作
### 算术运算
- 使用`set /a`进行基本算术操作：
  ```batch
  set /a result=5+3
  echo %result%
  ```

### 重定向操作
- 将输出重定向到文件或另一个命令：
  ```batch
  dir > output.txt
  type output.txt
  ```

### 多名命令运算
- 在一行中执行多个命令，用`&`分隔：
  ```batch
  echo First Command & echo Second Command
  ```

### 管道操作
- 通过`|`将前一个命令的输出作为后一个命令的输入：
  ```batch
  dir | find "txt"
  ```

## 基本命令格式介绍
- `echo`显示消息或变量值：
  ```batch
  echo The current date is: %date%
  ```
- `pause`暂停程序等待用户按键继续：
  ```batch
  pause
  ```
- `rem`添加注释以说明代码：
  ```batch
  rem This is a comment
  ```

## 文件和目录管理
### 目录浏览
- `dir`列出当前目录下的文件及子目录：
  ```batch
  dir
  ```

### 目录新建与删除
- `mkdir`创建新目录：
  ```batch
  mkdir new_folder
  ```
- `rmdir`删除空目录：
  ```batch
  rmdir new_folder
  ```

### 目录切换
- `cd`改变当前工作目录：
  ```batch
  cd C:\path\to\directory
  ```

### 目录重命名
- `ren`重命名文件或目录：
  ```batch
  ren old_name new_name
  ```

### 文件拷贝
- `copy`复制文件：
  ```batch
  copy file.txt C:\destination\
  ```

### 文件删除
- `del`删除文件：
  ```batch
  del file.txt
  ```

### 文件剪切
- `move`移动文件：
  ```batch
  move file.txt C:\new_location\
  ```

### 显示目录结构
- `tree`展示目录结构树：
  ```batch
  tree
  ```

## 系统相关命令
### 时间相关
- `time`查看/设置系统时间：
  ```batch
  time
  ```
- `date`查看/设置系统日期：
  ```batch
  date
  ```

### 启动命令
- `start`启动一个新的窗口并执行指定程序或命令：
  ```batch
  start notepad
  ```

### 调用其他bat文件
- `call`调用其他批处理文件：
  ```batch
  call other_script.bat
  ```

### 任务列表查看
- `tasklist`显示所有正在运行的任务：
  ```batch
  tasklist
  ```

### 任务终止
- `taskkill`终止特定进程（例如结束notepad进程）：
  ```batch
  taskkill /IM notepad.exe /F
  ```

### 关机命令
- `shutdown`关闭计算机：
  ```batch
  shutdown -s -t 0
  ```

### 计划任务
- `at`安排计划任务（例如在明天早上8点运行脚本）：
  ```batch
  at 08:00 /every:M,T,W,Th,F,S,S "C:\path\to\script.bat"
  ```

## 网络相关命令
### 主机联通性检测
- `ping`检测主机连接状态：
  ```batch
  ping www.example.com
  ```

### 网络连接
- `telnet`测试远程主机上的端口是否开放：
  ```batch
  telnet www.example.com 80
  ```

### 网络路由信息
- `tracert`跟踪数据包到达目的地所经过的路由：
  ```batch
  tracert www.example.com
  ```

### 网络适配器信息
- `ipconfig`显示IP配置信息：
  ```batch
  ipconfig
  ```

### ARP信息
- `arp`显示和修改ARP缓存表：
  ```batch
  arp -a
  ```

## 条件判断与循环
### if-else 结构
- `if`基于条件执行不同的命令：
  ```batch
  if exist "file.txt" (
      echo File exists.
  ) else (
      echo File does not exist.
  )
  ```

### 循环遍历文件夹名称
- `for`遍历指定目录下的所有.txt文件：
  ```batch
  for %%f in (*.txt) do (
      echo Processing %%f
  )
  ```
