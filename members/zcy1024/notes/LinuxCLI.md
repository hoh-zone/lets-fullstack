# LinuxCLI

一切皆文件！

## 文件权限

### 权限类型

- `r(readable)` => 可读
- `w(writable)` => 可写
- `x(executable)` => 如果文件拥有该权限，则该文件可执行；如果目录拥有该权限，则可以切换目录
- `-` => 无权限

### 权限组别

在查看一个文件/目录权限的时候，通常会以这种形式展示：`drwxr-xr-x`<br>除开第一个字母（后面会解释它的含义），可以将剩下的以三个一组，一共分为三组，从左到右依次表示：

- 该文件/目录的所有者`Owner`对该文件/目录的权限
- 该文件/目录的所属组`Group`对该文件/目录的权限
- 不被上述两点包含的其他用户`Others`对该文件/目录的权限

## 常用通配符

- `*` => 匹配**0**个或**多**个字符串
- `?` => 严格匹配**1**个字符
- `[abcd]` => 匹配`abcd`4个字符当中的**任意1个**
- `[a-z]` => 匹配`abcd...xyz`这26个字符当中的**任意一个**<br>`[1-9]`等匹配规则也是同理
- `[!abc]` => 除了`abc`这3个字符外，可以匹配**任意一个**<br>`[^abc]`效果等价，根据个人写法习惯选择即可

## man

### 作用

查看帮助手册

### 帮助手册章节内容简介

第一章：`shell commands` => `ls, cp, mv...`等常用的命令

第二章：`system calls` => `open, close, read, write...`等系统调用

第三章：`library calls` => `fopen, fclose, fread, fwrite...`等库函数

第四章：`special files` => 设备文件的说明，通常指的是`/dev`目录下的文件

第五章：`file formats and conventions` => 配置文件相关的说明文档，例如：`/etc/passwd`

第六章：`games` => 游戏相关

第七章：`miscellaneous` => 惯例与协议相关

第八章：`system administration commands` => 系统管理员会使用到的命令，通常只开放给`root`用户/权限

第九章：`kernel routines` => 系统内核相关

### 案例

- `man man` => 查看`man`命令的帮助手册<br>`man ls` => 查看`ls`命令的帮助手册<br>......

- `man -f sleep` => 查看`sleep`命令的简要说明，会得到两条信息：

- - `sleep(1)...` => 第一章中`sleep`命令的简要信息
  - `sleep(3)...` => 第三章中`sleep`命令的简要信息

  因为`shell`命令中存在`sleep`（位于帮助手册的第一章），库函数中也存在`sleep`（位于帮助手册的第三章）

  直接`man sleep`默认打开的是第一章（按照章节从上往下，第一个存在该命令）的帮助手册

  使用`man 3 sleep`可以指定打开第三章有关`sleep`函数的帮助手册

- `man -w ls` => 查看`ls`命令的帮助手册在磁盘当中的位置

- `man -k disk` => 查看所有跟字符串`disk`相关的帮助手册的简要说明，用于突然记不起具体命令但是记得其中某一部分拼写的情况<br>这里的相关不只是命令/函数名中包含，也包括描述

## info

### 作用

用来阅读`info`格式的文档，查看帮助信息

相较于`man`，`info`所展示的帮助文档信息会更加详细全面，其中甚至不乏超链接，可以像浏览网页一样去查看，但缺点也是太过详细全面，操作繁琐，使用起来没有`man`那么便捷，大多数情况下用`man`命令查看就够用了。

### 案例

- `info ls` => 查看`ls`命令的帮助文档
- `info -w ls` => 查看`ls`命令的帮助手册`(info格式)`在磁盘当中的位置

## whatit

### 作用

查询一个命令执行什么功能

从观感上就是将`man`命令查询到的各个章节的开头提取出来，某种程度上等同于`man -f`

### 案例

`whatis sleep` => 会发现，得到的结果跟`man -f sleep`一致

## touch

### 作用

1. 改变已有文件的时间戳属性（用户必须是文件所有者，或者拥有写该文件的权限）
2. 创建一个新的空文件

文件的时间属性如何查看会在后面介绍，这里只需要知道时间属性中的两个：访问时间`Access`和修改时间`Modify`

### 案例

- `touch file_name` => 以当下时间为时间戳新建一个空文件，该文件名为`file_name`
- `touch file1 file2 file3` => 同时创建三个新文件，依次命名为`file1, file2, file3`，数量可以增加，中间用空格隔开
- `touch file{1..3}` => 同时创建三个新文件，依次命名为`file1, file2, file3`，在创建文件命名有规律（连续的字符）时的一种快捷方式
- `touch exist_file` => 已存在的文件`exist_file`的所有时间属性都更新为当下时间
- `touch -a exist_file` => 已存在的文件`exist_file`的访问时间`Access`更新为当下时间
- `touch -m exist_file` => 已存在的文件`exist_file`的修改时间`Modify`更新为当下时间
- `touch -c nofile` or `touch --no-create nofile` => 仅用来修改已有文件的时间戳，即使`nofile`不存在也不会新建
- `touch today_file -r yesterday_file` => 将访问和修改时间从`yesterday_file`复制到`today_file`
- `touch -d "tomorrow" file` => 将`file`的访问和修改时间更改为明天
- `touch -t 2501011000.33 file` => 将`file`的访问和修改时间更改为`2025-01-01 10:00:33`，修改为任意时间同理更改格式即可

## mkdir

### 作用

创建目录

默认状态下，如果想要创建的目录已存在，则提示已存在，而不会继续创建，与文件重名也不行

### 案例

- `mkdir dir1` => 在当前目录下，新建一个名为`dir1`的目录
- `mkdir dir2 dir3` => 在当前目录下，新建两个目录，分别名为`dir2, dir3`，数量可以增加，中间用空格隔开
- `mkdir dir{4..7}` => 与前文`touch file{1..3}`同理
- `mkdir -p dir8/dir9` => 递归创建，先在当前目录下创建`dir8`目录，再在`dir8`目录下创建`dir9`
- `mkdir -p dir8/dir10/dir11` => 递归创建，由于`dir8`目录已存在，所以直接进到`dir8`目录下创建`dir10`，此时在`dir8`目录下应该有同级的两个目录，分别是`dir9`和`dir10`，最后在`dir10`目录下创建`dir11`
- `mkdir -m 700 dir1/dir12` => 在`dir1`目录下新建目录`dir12`，同时将`dir12`的权限设置为`700`
- - `700`权限是指：所有者可读可写可执行（切换目录），所属组和其他用户都没有读、写、执行（切换目录）的权限，相关内容后续展开
- `mkdir -v dir{13..15}` => 显示目录的创建过程

## rm

### 作用

删除文件或目录

**注意：**Linux没有自带的回收站，删除需谨慎，尤其是`rm -rf /*`

### 案例

- `rm file` => 删除当前目录下的`file`文件
- `rm -r dir` or `rm -R dir` => 删除当前目录下的`dir`目录，其子目录也将被递归删除
- `rm nofile` => 尝试删除一个不存在的文件会出现警告，添加`-f`即`rm -f nofile`将忽略不存在的文件，不会出现警告
- `rm -rf *` => 删除当前目录下的所有文件
- `rm -i file1 file2 file3` => 删除当前目录下的三个文件，分别是`file1, file2, file3`，但由于添加了`-i`，所以每删除一个文件前都会询问，需要手动输入`y`来确认删除，输入`n`来拒绝删除即保留该文件
- `rm -ir dir1 dir2 dir3` => 同理，需要一个个手动确认，只不过添加了`-r`，所以要删除的是目录
- `rm file{1..3}` => 删除当前目录下的`file1, file2, file3`这三个文件

## rmdir

### 作用

删除**空**目录，否则将报错

由于一切皆文件，所以空目录也是占磁盘空间的，当磁盘空间爆满，到了需要删空目录来解放空间的时候，如果系统只支持`rm`命令来删除，还需要在删除前进行一番判断，徒增工作量降低效率，而`rmdir`则可以一步到位，空的删除，不空的保留

### 案例

- `rmdir empty_dir` => 删除当前目录下的空目录`empty_dir`

- `rmdir -p empty1/empty2/empty3` => 递归删除多重目录<br>**注意：**此命令要求`empty3`是个空目录，在删除`empty3`后`empty2`成为空目录，在删除`empty2`后`empty1`是个空目录，否则将报错

  ```bash
  # 递归创建三个目录
  mkdir -p dir1/dir2/dir3
  
  # 进到dir1目录下创建test文件，再返回到上级目录
  cd dir1
  touch test
  cd ..
  
  # 尝试递归删除
  rmdir -p dir1/dir2/dir3
  # 警告信息：
  # rmdir: dir1: Directory not empty
  
  # 此时进到dir1目录查看
  cd dir1
  ls
  # 将发现只有一个test文件，而dir2和dir3已经被删除
  ```

- `rm -v dir` => 显示指令执行的过程<br>可以尝试将上述代码的递归删除更改为`rmdir -pv dir1/dir2/dir3`，你将更清晰直观得感受到删除过程以及报错的位置与逻辑

## mv

### 作用

1. 移动文件
2. 重命名文件

### 案例

- `mv file dir` => 将当前目录下的`file`文件移动至当前目录的`dir`目录下
- `mv file new_file` => 将当前目录下的`file`文件重命名为`new_file`<br>**注意：**如果`new_file`是一个已存在的文件，那么`file`将覆盖掉`new_file`
- `mv dir1 dir2` => 将`dir1`目录移动到`dir2`中，如果`dir2`不存在则重命名
- `mv -i file1 file2` => 如果`file2`不存在则直接重命名，如果存在这个文件，那么将询问是否将其覆盖
- `mv -i file1 dir/file2` => 如果`dir`目录下不存在`file2`文件，则将`file1`文件移动到`dir`目录下并且重命名为`file2`<br>如果`dir`目录下存在`file2`文件，那么将询问是否将其覆盖
- `mv -f file1 dir/file2` => 强制操作，即使`dir`目录下存在`file2`文件，也会在不经询问的前提下将`file1`转移过去并覆盖<br>**注意：**单就这一点而言，是否添加`-f`没有影响，因为不加`-f`而直接`mv file1 dir/file2`也将不经询问直接覆盖
- `mv -b file1 file2` => 如果`file2`文件已存在，则在覆盖前会将其备份，备份的内容放在文件`file2~`中
- `mv -u file1 file2` => 如果`file2`不存在，则直接重命名<br>如果`file2`已存在，那么只有当`file1`文件更（第四声）新的时候（从时间属性上来说），才会覆盖`file2`文件，否则将忽略此条命令，并且也没有任何警告或报错
- `mv * ../` => 将当前目录下的所有内容都转移到上级目录
- `mv dir1/* dir2` => 将`dir1`目录下的所有内容都转移到`dir2`目录下

## cp

### 作用

复制文件或目录，如果目标文件已存在，将直接覆盖（与使用`-f`等价）

### 案例

- `cp file1 file2` => 将`file1`文件复制一份放到`file2`中
- `cp -r dir1 dir2` => 递归复制，将目录`dir1`复制一份放到`dir2`目录中，其下的所有内容也将一并被复制
- `cp -i file1 file2` => 如果`file2`已存在，则会提醒让你确认是否执行覆盖操作，即将`file1`的内容覆盖掉原本`file2`的内容
- `cp -b file1 file2` => 如果`file2`已存在，则会先将其备份为`file2~`
- `cp -a dir1 dir2` => 保留链接、文件属性的前提下复制目录下的所有内容

## cd

### 作用

改变目录，从一个目录进入到另一个目录

### 特殊目录

- `~` => 用户的家目录
- `.` => 当前目录
- `..` => 当前目录的上一级目录
- `/` => 根目录
- `-` => 上一次所处的目录

### 路径

- 绝对路径：起始路径为根目录`/`
- 相对路径：起始路径不为根目录`/`

### 案例

- `cd dir` or `cd ./dir` => 进入当前目录下的`dir`目录
- `cd ../..` => 切换到当前目录的上两级目录
- `cd` or `cd ~` => 切换到家目录
- `cd -` => 切换到上一次所在的目录

## pwd

### 作用

打印当前路径（绝对路径）防止迷路

### 案例

`pwd` => 屏幕上将打印你当前所处位置的绝对路径

## ls

### 作用

显示指定目录下有哪些文件/目录及其具体的属性信息

### 案例

- `ls` => 查看当前目录下有哪些文件/目录（不包括以`.`开头的隐藏内容）
- `ls -a` => 查看当前目录下有哪些文件/目录（包括以`.`开头的隐藏内容），相较于`ls`会多显示：
- - `.` => 当前目录
  - `..` => 上一级目录
  - 以`.`开头的隐藏文件/目录
- `ls -l` => 以长格式列出当前目录下的文件/目录信息，包括各权限，所属组，创建时间等等
- `ls /` => 查看根目录`/`下的所有文件/目录
- `ls -lR` => 递归列出当前目录下以及其所有子目录下的文件/目录的信息，以长格式形式列出
- `ls -l f*` => 查看当前目录下所有以`f`开头的文件/目录的长格式信息
- `ls -r` => 将文件以相反的次序显示（默认是以字典序升序，加了`-r`后变为降序）
- `ls -t` => 根据最后修改的时间来排序显示（新的文件最先显示）
- `ls -ltr` => 以长格式列出信息，并且以最后修改的时间的倒序（旧的文件先显示）进行显示
- `ls -A` => 除了不列举`.`以及`..`之外，效果等同`-a`
- `ls -S` => 按照文件大小排序
- `ls -F` => 在列出的文件名后根据其文件类型增加一个符号，例如：
- - 可执行加`*`
  - 目录加`/`
  - ......
- `ls -h` => 以人类可读的形式显示数字大小
- `ls -lh` => 列出当前目录下文件/目录的详细信息，并且显示的数字将以人类更易读的形式进行单位转换（K, M, G...）

## tree

### 作用

以树状形式列出目录下的内容

### 案例

- `tree` => 树状显示当前目录下的文件和目录
- `tree -a` => 树状显示当前目录下的文件和目录，包括以`.`开头的隐藏文件/目录
- `tree -d` => 只树状显示当前目录下的目录
- `tree -L 2` => 树状显示当前目录下2个层级内的文件和目录
- `tree -p` => 除了显示文件/目录名之外，增加权限信息
- `tree -t` => 按更改时间进行排序
- `tree -r` => 反向排序
- `tree -f` => 显示完整的相对路径

## stat

### 作用

显示文件或文件系统的详细信息

文件信息：文件名、大小、块的大小、IO块的大小、文件类型、设备号、链接数、文件权限、用户名、用户组、**时间属性**等等

文件系统信息：文件系统ID、文件名最大长度、文件系统类型、块大小、总空间、可用空间等等

### 时间属性

- `atime: access time` => 访问时间<br>读取文件`(more/less/cat/tail/...)`、修改文件`(vim/nano/...)`时改变
- `mtime: modify time` => 修改时间<br>修改文件`(vim/nano/...)`时改变
- `ctime: change time` => 状态改变时间<br>修改文件`(vim/nano/...)`、文件属性变化`(chmod/chown/...)`时改变

**注意：**上述括号内的命令后续会提到，这里不展开

### 案例

- `stat file` => 查看`file`文件的信息
- `stat -f file` => 查看`file`文件所在文件系统信息
- `stat -t file` => 以简洁方式输出信息<br>将关键内容以空格隔开，放到一行以字符串的形式输出

## rename

### 作用

用字符串替换的方式**批量**改变具有一定规则的文件名，这也是与`mv`区别的地方

### 语法

`rename 's/old-name/new-name/' files`

- `old-name` => 原字符串，即文件名中需要替换的字符串
- `new-name` => 目标字符串，即需要替换成为的字符串
- `files` => 指定要改变文件名的文件列表

### 案例

- `rename 's/.txt/.doc/' file.txt` => 将`file.txt`中的`.txt`替换为`.doc`，此时通过`ls`查看文件，会发现`file.txt`不见了，取而代之的是`file.doc`
- `rename -n 's/file/file0/' file*` => 将所有与`file*`匹配的文件名中的`file`替换为`file0`<br>由于添加了`-n`，所以此条命令是模拟替换，不会真实生效，而是以`rename(file1 file01), rename(file2, file02), ...`的形式一一列举模拟过程中会进行的替换
- `rename -v 's/file/file0/' file*` => 真实替换并且显示替换过程信息，如：`file1 renamed as file01`等等

## basename

### 作用

提取文件路径名最后的文件名，可以根据需求删除指定后缀

### 案例

- `basename /etc/passwd` => 提取出文件名`passwd`
- `basename /usr/local/` => 提取出目录名（会自动删除最后的`/`）`local`
- `basename -a /etc/passwd /usr/local/` => 添加`-a`以支持提取多个输入，按照输入的顺序分行显示提取出的文件/目录名
- `basename /etc/sysctl.conf .conf` => 提取出`sysctl.conf`后会删除指定后缀`.conf`，所以最终得到结果为`sysctl`<br>`basename -s .conf /etc/sysctl.conf`与之等价<br>**注意：**`.`不能忘，否则将会得到`sysctl.`

## dirname

### 作用

提取路径

### 案例

- `dirname /usr/bin/cat` => 提取找到`cat`文件的路径，即得到`/usr/bin`
- `dirname /home/username/commands/` => 提取找到`commands`目录的路径，即得到`/home/username`

## chattr && lsattr

### 作用

- `chattr` => 更改文件属性<br>非`root`用户需要用`sudo`提权才能使用该命令
- `lsattr` => 查看文件属性

###  属性

- `A` => 不要修改对这个文件的最后访问时间
- `S` => 一旦应用程序对这个文件执行了写操作，使系统立刻把修改的结果写到磁盘
- `a` => 系统只允许在这个文件之后追加数据，不允许任何进程覆盖或截断这个文件<br>如果拥有该属性的是目录，那么系统将只允许在这个目录下建立和修改文件，而不允许删除任何文件
- `b` => 不更新文件或目录的最后存取时间
- `c` => 将文件或目录压缩后存放
- `d` => 当`dump`程序执行时，该文件或目录不会被`dump`备份
- `D` => 检查压缩文件中的错误
- `i` => 系统将不允许对这个文件进行任何的修改<br>如果目录具有该属性，那么任何进程只能修改目录之下的文件，不允许建立和删除文件
- `s` => 彻底删除文件，不可恢复
- `u` => 当一个应用程序请求删除这个文件，系统会保留其数据块以便以后能够恢复，用来防止意外删除文件或目录
- `t` => 文件系统支持尾部合并
- `X` => 可以直接访问压缩文件的内容

### 案例

- `sudo chattr +i file` => 为`file`这个文件添加`i`属性，系统将不允许任何人修改它
- - `echo 111 >> file` => 尝试将`111`追加入`file`文件，将得到报错`Operation not permitted`
  - `rm file` => 尝试删除这个文件，依旧得到报错`Operation not permitted`
  - ......
- `lsattr file` => 可以观察到属性里有`i`
- `sudo chattr -i file` => 撤销刚刚添加的`i`属性，现在可以修改它
- `sudo chattr +a file` => 只允许在`file`文件里追加内容（对日志文件特别有用）
- `sudo chattr -R +i dir` => 对`dir`目录中的所有文件都添加`i`属性限制

## file

### 作用

识别文件类型

### 案例

- `file file.txt` => 得到其类型为`ASCII text`
- `file dir` => 得到其类型为`directory`
- `file /dev/sda` => 得到其类型为`block special`

## md5sum

### 作用

生成和校验文件的md5值（根据内容按照某个算法算出来的32位16进制数，与文件名无关），确保文件的准确性

### 案例

- `md5sum file` => 生成`file`文件的md5值

- `md5sum -b file` => 以二进制模式读取文件再计算md5值

- `md5sum -t file` => 以文本模式读取文件再计算md5值

  以上不论哪一种，计算得到的md5值都是相同的，因为内容本质没有任何变化

- `md5sum file > file.md5` => 计算`file`文件的md5值并将结果保存到`file.md5`文件中

- `md5sum -c file.md5` => 校验上一个命令生成的md5值与`file`文件是否一致，修改`file`文件后再次执行查看是否一致

- `md5sum -c --status file.md5` => md5校验但是不显示任何输出，用返回码表示成功与否<br>`echo $?` => 其中，`$?`用来查询上一条命令执行的结果（0表示成功，1表示失败），`echo`表示将其打印出来

## find

### 作用

搜索指定文件/目录

### 案例

- `find / -name *.conf` => 全盘搜索（`/`根目录开始）所有以`.conf`结尾的文件

- `find /etc -size +1k` => 在`/etc`目录下搜索所有大于1k的文件

- `find /home -user username` => 在`/home`目录下搜索属于指定用户`username`的所有文件

  上述命令可能涉及文件权限问题，可以用`sudo`提权后执行

- `find . -type f` => 查找当前目录下的所有文件（`file`类型）

- `find . -perm 664 -exec ls -l {} \;` => 查找当前目录下所有权限为`664`的文件，并将其通过`ls -l`进行显示

- `find .` => 列出当前目录中的所有文件、目录以及子文件信息

- `find . -iname *.txt` => 在当前目录中查找所有后缀为`.txt`（不区分大小写）的文件

- `find . ! -name *.txt` => 在当前目录中查找所有后缀不为`.txt`的文件

- `find . -mtime -7 -exec rm -i {} \;` => 找到当前目录下所有在7天内被修改过的文件并依次询问是否将其删除

- ......

## which

### 作用

在`path`变量指定的路径当中，搜索某个**系统命令**的位置，并且返回第一个搜索结果

查看`path`变量指定的路径：`echo $PATH`

### 案例

- `which ls` => 查找命令`ls`所在的位置
- `which bash` => 查找命令`bash`所在的位置

## whereis

### 作用

查找命令的二进制程序、源代码文件和`man`手册页等相关文件的路径

`whereis`查找速度相当快，因为Linux系统会将系统内的所有的文件都记录在一个数据库当中，而不是在磁盘里乱找，但是这个数据库不是实时更新的（一般一天自动更新一次），所以有可能找不到刚刚添加的文件，或者找到了已被删除的文件<br>手动更新该数据库：`sudo updatedb`

### 案例

- `whereis ls` => 将显示其命令位置及`man`手册页位置：`ls: /usr/bin/ls /usr/share/man/man1/ls.1.gz`
- `whereis -b ls` => 只查找`ls`命令的二进制程序所在的位置
- `whereis -m ls` => 只查找`ls`命令的`man`手册页路径

## locate

### 作用

快速查找文件或目录，速度比`find`快，与`whereis`一样，也是在数据库中搜索

### 案例

- `locate file` => 查找所有路径当中包含`file`的文件
- `locate /etc/sh` => 查找所有路径中包含`/etc/sh`的文件
- `locate -i locate/f` => 以`locate`结尾的目录且该目录下含有以`f`开头的文件，含有这一特点的所有文件都将被检索出来，而`-i`使得检索过程当中忽略大小写

## chown

### 作用

改变文件或目录的用户和用户组，通常需要加上管理员权限执行

### 案例

- `sudo chown user:group file` => 将`file`文件的用户更改为`user`，用户组更改为`group`
- `sudo chown user file` => 只更改它的用户
- `sudo chown :group file` => 只更改它的用户组
- `sudo chown -c user:group file` => 显示改变过程
- `sudo chown -R user:group dir` => 改变指定目录下所有子文件的所属主和所属组

## chgrp

### 作用

更改用户组，通常需要加上管理员权限

### 案例

- `sudo chgrp group file` => 更改`file`文件的用户组为`group`
- `sudo chgrp -v group file` => 显示命令执行过程
- `sudo chgrp --reference=reffile file` => 依据参照物`reffile`来更改`file`的用户组
- `sudo chgrp -R group dir` => 将指定目录下的所有子文件的所属组更改为`group`

## chmod

### 作用

改变文件/目录的权限，只有你是该文件/目录的所属主或者`root`用户才可以执行

### 对象

- `u` => `user`即文件所有者
- `g` => `group`即文件所属组
- `o` => `others`即其他用户
- `a` => `all`即所有用户，相当于`ugo`

### 操作

- `+` => 增加权限
- `-` => 去除权限
- `=` => 设置权限

### 权限

- `r` => 可读
- `w` => 可写
- `x` => 可执行/可切换目录

### 数字模式

`drwxrwxrwx`

将上述权限表示人为分成四个部分

`(- or d)(rwx)(rwx)(rwx)`

1. `- or d` => 表示文件类型

2. `rwx` => 第一组表示该文件/目录所有者所拥有的权限，按照类似二进制的规则来转化为数字：

   - `x` => $2 ^ 0$
   - `w` => $2 ^ 1$
   - `r` => $2 ^ 2$
   - `-` => 该位为$0$

   例如：<br>`rwx` => $7$<br>`r-x` => $5$<br>`---` => $0$

3. 第二组`rwx`表示该文件/目录所属组所拥有的权限

4. 第三组`rwx`表示该文件/目录对其他用户开放的权限

### 案例

- `chmod a+r file` => 为所有`all`用户添加读`r`权限
- `chmod -R a+r *` => 为当前目录及其所有子目录下的文件都添加所有用户`all`的读`r`权限
- `chmod u+x file` => 为`file`文件的拥有者`user`添加可执行`x`权限
- `chmod ug+w,o-w file` => 只有`file`文件的拥有者`user`及其所属组用户`group`拥有对其写入`w`的权限，而其他用户`others`将失去对其写入`w`的权限
- `chmod a+r,a+w,a+x file` or `chmod 777 file` => `file`文件对所有人`all`可读`r`可写`w`可执行`x`
- `chmod 755 file` => `file`文件的拥有者可读可写可执行，所属组用户及其他用户可读可执行不可写
- `chmod u=rw,go= file` => `file`文件的拥有者可读可写，所属组用户及其他用户没有任何权限

## grep

### 作用

文本搜索工具

### 案例

- `grep keywords /etc/passwd` => 在`/etc/passwd`文件中搜索包含字符串`keywords`的内容
- `grep keywords file1 file2` => 在多个文件中搜索
- `grep -h keywords file1` => 搜索但是结果不包含文件名
- `grep -rl keywords *` => 递归搜索`-r`当前目录及其子目录中的所有文件，将内容含有字符串`keywords`的文件的文件名的相对路径依次打印出来`-l`
- `grep -c keywords file1 file2` => 在某个文件中，包含该关键词的内容的数量，`file1`和`file2`会单独统计数量
- `grep -i KeyWords file` => 搜索过程忽略大小写
- `grep -n keywords file` => 显示的结果将包含行号
- `grep -v keywords file` => 反向查找，即在`file`文件中搜索出所有不包含字符串`keywords`的内容
- `grep -x keywords file` => 精确搜索，即同一行内容除了字符串`keywords`之外没有其它（不包括换行）才会被匹配上
- `grep -q keywords file` => 询问`file`文件中是否含有所需要查找的字符串`keywords`，此条命令不会有输出，而是通过状态值返回，可以通过`$?`来获取，方便在`Shell`脚本中判断和调用

## egrep

### 作用

查找指定字符串

### 案例

- `egrep 'a+' file` => 在`file`文件中查找包含一个或多个`a`（可以间隔其它字符）的内容

- `egrep 'linux|666' file` => 在`file`文件中查找包含`linux`或`666`的内容

- `egrep '(linux)+' file` => 在`file`文件中查找包含一个或多个完整字符串`linux`的内容

- `egrep '(linux){2}' file` => 在`file`文件中查找连续包含两个完整字符串`linux`的内容

- `egrep '^#' file` => 查找以`#`开头的内容

- `egrep 'linux$' file` => 查找以`linux`结尾的内容

- `egrep 'ab[cd]' file` => 查找含有字符串`abc`或`abd`的内容

  上述命令的''中均为正则表达式

## cat

### 作用

在终端上显示内容，一股脑输出，所以一般用来查看短小精悍的文件

### 案例

- `cat file` => 在终端上显示`file`文件的内容
- `cat file1 file2` => 查看多个文件
- `cat -n file` => 显示行数编号，多个连续的空行也会连续编号
- `cat -s file` => 去除重复的空行
- `cat -b file` => 显示行数，但是空行不编号，不过空行依旧会存在
- `cat -E file` => 每一行末尾显示`$`符号，包括空行
- `cat -T file` => 将`TAB`字符显示为`^I`符号
- `cat file > output` => 重定向输出文件内容，即不再显示到终端，而是写入`output`文件<br>如果`output`不存在则创建后写入，否则将覆盖内容
- `cat file >> output` => 重定向追加，同样不显示到终端，而是追加进`output`文件<br>如果`output`不存在则创建后写入，否则将追加到`output`原内容的末尾
- `cat file1 file2 > combinedfile` => 合并文件
- `cat > file` => 回车后会让你输入内容，完成后按`Ctrl + D`保存，你输入的内容将会被保存进`file`文件

## more

### 作用

分页显示文本文件内容，但是只能往下翻，不能往回翻

### 基本操作

- 回车：下滚一行
- 空格：下翻一页
- `q`：退出

### 案例

- `more ~/.bashrc`
- `more -c -10 ~/.bashrc` => 先清屏，再以每次10行内容的格式显示指定文本文件内容
- `more -s ~/.bashrc` => 当出现多个连续的空白行的时候，将它们合并为一行
- `more +10 ~/.bashrc` => 从第10行开始显示

## less

### 作用

分页显示文本文件内容，支持向前向后翻页<br>**注意：**前文提到的`man`手册嵌入了`less`命令，各种操作与其一致

### 基本操作

- 回车：下滚一行
- 空格：下翻一页
- `j`：下滚一行
- `k`：上滚一行
- `f`：下翻一页
- `b`：上翻一页
- `q`：退出
- `/word`：搜索`word`关键词

### 案例

- `less ~/.bashrc`
- `less ~/.bashrc ~/.bash_history` => 查看多个文件
- - `n`：浏览下一个文件
  - `p`：浏览上一个文件
- `history | less` => 查看历史使用的命令，并将其以`less`命令分页显示

## head

### 作用

显示文件开头的内容

空行算作一行，空格和换行符都算作一个字符

### 案例

- `head ~/.bashrc` => 默认显示该文件的前10行
- `head -n 5 ~/.bashrc` => 显示该文件的前5行
- `head -n -6 ~/.bashrc` => 显示除了最后6行之外的所有内容
- `head -c 20 ~/.bashrc` => 显示文件的前20个字符
- `head -c -30 ~/.bashrc` => 显示除了最后30个字符之外的所有内容

## tail

### 作用

查看文件结尾的内容

空行算作一行，空格和换行符都算作一个字符

### 案例

- `tail ~/.bashrc` => 默认显示该文件的最后10行
- `tail -n 20 ~/.bashrc` => 查看最后20行内容
- `tail -n +20 ~/.bashrc` => 查看从文件第20行开始一直到文件末尾
- `tail -c 10 ~/.bashrc` => 查看最后10个字符
- `tail -f file` => 动态显示文件的最后10行<br>此时另起一个终端，往`file`文件里加内容，再切换回执行了该命令的终端，可以发现该新添加的内容<br>该命令应用于日志文件特别有效

## tac

### 作用

反向显示文件内容，以行为单位，与`cat`的显示顺序正好相反

### 案例

`tac file` => 先显示最后一行，再显示倒数第二行...最后显示第一行

## nl

### 作用

添加行号

### 案例

- `nl file` => 列出`file`文件的内容，同时添加行号，空行不显示行号
- `nl -b a file` => 空行显示行号
- `nl -b a -n rz file` => 行号在自己栏位的最右侧显示，并且加前导零使得格式对齐，宽度默认为6为，即：第一行显示为000001
- `nl -b a -n rz -w 3 file` => 将宽度更改为3，即：第一行显示为001
- `nl -b t file` => 空行不显示行号（与不加任何参数时等价）

## wc

### 作用

统计文本信息

### 案例

- `wc file` => 统计该文件的行数、字数（由空白、跳格或换行符分隔的字符串）以及字节数（包括可见字符和不可见字符）

  **注意：**一个字符可能占多个字节，例如：在UTF-8编码中，一个英文字母占一个字符，占用空间一个字节，而一个中文，则需要占用三个字节大小

- `wc -w file` => 统计字数

- `wc -m file` => 统计字符数

- `wc -c file` => 统计字节数

- `wc -l file` => 统计行数

- `wc -L file` => 打印该文件最长行的长度（不包含不可见字符）

## split

### 作用

文件分割<br>默认按每1000行分割成一个小文件<br>默认情况下，分割成的文件按照以下规律依次命名：`xaa, xab, xac, ......`

### 案例

- `split -2 file` => 将`file`文件的内容按照每两行切割成一个小文件
- `split -b 10k file` => 根据文件大小，每10kb切割成一个小文件
- `split -d -a 3 file` => 切割成的文件以数字进行命名，命名宽度为3，即：`x000, x001, x002, ......`
- `split -d -a 3 file split_file` => 切割成的文件拥有指定前缀，即：`split_file000, split_file001, split_file002, ......`<br>**注意：**该命令中，要切割的文件`file`和指定前缀字符串`split_file`的顺序不能颠倒

## cut

### 作用

从文件中提取文本的一部分

### 案例

- `cut -f 2 file` or `cut -f2 file` => 提取`file`文件当中第二列的内容<br>默认情况下，`cut`命令会将一行内容依据制表符`TAB`分成若干列
- `cut -f2 --complement file` => 提取除第二列之外的内容
- `cut -f2 -d";" file` => 提取第二列，但是一行内容将以分号来分成若干列
- `cut -b 2-4,6 file` => 提取每一行的第2, 3, 4, 6个字节的内容
- `cut -c1-3 file` => 提取每一行的第1, 2, 3个字符的内容
- `cut -c-2 file` => 提取每一行的前两个字符的内容
- `cut -c4- file` => 提取每一行的第四个字符及其后的内容

## paste

### 作用

合并两个或多个文件

### 案例

- `paste file1 file2` => 按照纵列将两个文件拼接起来，键入命令中的文件顺序不同，结果也不同<br>想要拼接更多的文件，只需要在命令后继续输入文件名即可<br>**注意：**如果文件中的行数不同，那么缺失位置将用空白字符填充
- `paste -d":" file1 file2 file3` => 合并文件的时候，每一行的内容以`:`来分隔<br>**注意：**如果文件中的行数不同，又指定了分隔符（以`:`为例），那么最后一行就可能出现`::words`之类的形式（因为前两个文件内容较少）
- `paste -d":" -s file1 file2` => 每个文件内部用`:`替换掉换行符组成一个一行的字符串，再将若干个字符串一行一行拼接
- `ls | paste -d " " - - - -` => 将`ls`的结果进行`paste`命令，将以空格进行分隔，并依次组成四列的形式

## sort

### 作用

对文本内容进行排序

### 案例

- `sort file` => 按字母字典序升序进行排序
- `sort -r file` => 按字母字典序降序进行排序
- `sort -n number_file` => 按照数字本身（从小到大）进行排序
- `sort -n -r number_file` => 从大到小
- `sort -t : -k 3 -n file` => 首先将每一行按照`:`进行分隔，按照第三列的数字本身从小到大的顺序来确定行的顺序

## uniq

### 作用

去除文件中的重复行

**注意：**这里的重复行必须是**连续**的重复行，如果中间被什么东西分隔开就不行

### 案例

- `uniq file` => `file`文件中每一重复的连续行都将只剩下一行内容
- `uniq -c file` => 去除重复行的同时统计每一行所在原文有多少重复行
- `uniq -d file` => 只显示有重复的记录，且每个记录只出现一次
- `uniq -u file` => 只显示没有重复的记录

## diff

### 作用

逐行比较文件差异，并且可以生成补丁文件

### 符号介绍

- `a` => 增加
- `c` => 改变
- `d` => 删除
- `|` => 前后两个文件内容有不同
- `<` => 后面文件比前面文件少了一行内容
- `>` => 后面文件比前面文件多了一行内容
- `+` => 比较的文件的后者比前者多一行
- `-` => 比较的文件的后者比前者少一行
- `!` => 两个文件有差别的行

### 案例

- `diff file1 file2` => 逐行比较并在每一个有差异的地方用上述符号进行展示
- `diff -y -W 50 file1 file2` => 并排格式输出，设置间隔宽度为50，同时在每一个有差异的地方用上述符号进行展示，相较于上一个命令，并排显示会更加直观
- `diff -c file1 file2` => 上下文格式输出
- `diff -u file1 file2` => 统一格式输出
- `diff file1 file2 > file.patch` => 生成补丁<br>如果为`file1`文件打上这个生成的补丁，那么它的内容将与`file2`完全一致
- `patch file1 file.patch` => 为`file1`文件打上刚刚生成的补丁

## join

### 作用

连接两个文件当中相同的连接字段后的内容

### 案例

- `join file1 file2` => 默认以第一列为连接字段

  ```bash
  cat file1
  # output:
  1 username 99
  2 test 100
  3 pp jj
  
  cat file2
  # output:
  1 username 1
  2 jj pp
  4 963 369
  
  join file1 file2
  # output:
  1 username 99 username 1
  2 test 100 jj pp
  ```

- `join -a1 file1 file2` => 左边文件，即`file1`当中未匹配上连接字段的内容也将显示

- `join -a2 file1 file2` => 右边文件，即`file2`当中未匹配上连接字段的内容也将显示

- `join -a1 -a2 file1 file2` => 两个文件当中未匹配上连接字段的内容也将显示<br>显示顺序：<br>1. 匹配上连接字段的内容<br>2. 左边文件，即`file1`当中未匹配上连接字段的内容<br>3. 右边文件，即`file2`当中未匹配上连接字段的内容

- `join -o 1.2 1.3 2.3 file1 file2` => 如果匹配上连接字段，那么将截取第一个文件`file1`的第二第三个字段与第二个文件`file2`的第三个字段组合在一起<br>**注意：**计算第几个字段时需要考虑连接字段（它也占个数）

- `join -t ' ' file1 file2` => 指定分隔符

- `join -v 1 file1 file2` => 只显示第一个文件，即`file1`文件当中，未能匹配上连接字段的内容

- `join -j 2 file1 file2` => 指定以两个文件当中的第二个字段作为连接字段进行匹配<br>**注意：**输出结果时，会自动将连接字段放在第一位

## tr

### 作用

转换或删除文件中的字符

### 案例

- `tr "[a-z]" "[A-Z]" < file` => 对`file`文件当中的内容进行小写到大写转换
- `cat file | tr a-z A-Z` => 对`file`文件当中的内容进行小写到大写转换
- `echo "hello world" | tr [:lower:] [:upper:]` => 对字符串`hello world`进行小写到大写转换
- - `[:alnum:]` => 字母和数字
  - `[:alpha:]` => 字母
  - `[:cntrl:]` => 控制（非打印）字符
  - `[:digit:]` => 数字
  - `[:graph:]` => 图形字符
  - `[:lower:]` => 小写
  - `[:upper:]` => 大写
  - `[:print:]` => 可打印字符
  - `[:punct:]` => 标点符号
  - `[:space:]` => 空白字符
  - `[:xdigit:]` => 十六进制字符
- `echo "Hello World" | tr "[A-Za-z]" "[a-zA-Z]"` => 将字符串`Hello World`当中的大小写字符互换
- `echo "daflenDAGDNfdsaf" | tr -d "[a-z]"` => 将字符串`daflenDAGDNfdsaf`中的小写字母删除
- - 类似的：<br>`tr -d 0-9` => 删除某一段内容中的数字<br>`tr -d "[ \t]"` => 删除某一段内容中的空格和tab符<br>`tr -d -c "0-9\n"` => 删除某一段内容中的，不在指定集合中的字符
- `echo -e "1\n\n\n2\n\n3\n\n\n" | tr -s "\n"` => 压缩重复的空白行<br>**注意：**`echo -e`表示后面紧跟的字符串中需要进行转译，这个例子当中就是需要将`\n`转译为换行符
- - 类似的：<br>`tr -s "[ xo]"` => 在某一段内容中，删除字符集中的重复字符<br>`tr -s " " "-"` => 在某一段内容中，将连续的空格压缩为一个空格，并将空格替换为`-`
- `echo -e "hello\tworld" | tr "\t" " "` => 将制表符替换为空格

## sed

### 作用

批量编辑文本文件（行处理）

### 动作

- `a` => 新增
- `c` => 取代
- `d` => 删除
- `i` => 插入
- `p` => 打印
- `s` => 取代

**注意：**默认情况下，该命令并非直接修改文件中的内容，而是将处理后的结果输出，文件内容保持不变

### 案例

- `sed -n '2p' file` => 仅输出`file`文件的第二行
- `sed -n '3,5p' file` => 输出第三、第四、第五行
- `sed -n '/an/p' file` => 输出带有关键词`an`的行<br>搜索支持使用正则表达式
- `sed '2,4d' file` => 删除第二、第三、第四行的内容并输出到屏幕上
- `sed '/an/d' file` => 删除带有关键词`an`的行
- `sed '2a nice' file` => 在第二行后追加一行字符串`nice`
- `sed '2i 123456789' file` => 在第二行前插入一行字符串`123456789`
- `sed '2c asdfgh' file` => 将第二行整行替换成字符串`asdfgh`
- `sed '2,5c data changed' file` => 将第二行、第三行、第四行、第五行的内容替换成一行字符串`data changed`<br>**注意：**并不是将第2-5行每一行都替换成该字符串，而是将第2-5行视为一个整体，用一个字符串将这个整体替换
- `sed 's/oldstring/newstring/g' file` => 全局替换`g`，把`oldstring`替换为`newstring`
- `sed '3s/oldstring/newstring/g' file` => 只将第三行的`oldstring`替换为`newstring`
- `sed -e 's/oldstring//g;s/yyds/newstring/g' file` => 多条件替换`-e`，将`oldstring`替换为空字符串（等同于删除），同时将`yyds`替换为`newstring`
- `sed -i '3s/oldstring/newstring/g' file` => 将第三行的`oldstring`替换为`newstring`，同时将修改后的结果写入`file`文件

## awk

### 作用

对文本和数据进行处理的编程语言，不过一般只是使用它进行内容提取（列处理），而编程部分则交给`Shell`

### 案例

- `df -h | awk '{print $1 "\t" $3}'` => 对`df -h`输出的内容进行处理，打印其第一列、第三列，中间用tab符隔开

- `awk -F : '{print $1 "\t" $3}' /etc/passwd` => 处理`/etc/passwd`文件，用冒号作为分隔符将每一行分成若干列（默认情况下以空白字符作为分隔符），然后提取显示其第一列、第三列的内容，中间用tab符隔开

- `awk -F : '$3>=500' /etc/passwd` => 将`/etc/passwd`文件中，以冒号分隔后的第三列中的数据不小于500的行提取出来，提取出来的结果没有被用冒号分割

- `awk -F : '/username/' /etc/passwd` => 搜索`/etc/passwd`文件中有关键词`username`的内容，并打印出所在的行的原内容

- `awk -F : '/username/{print $7}' /etc/passwd` => 搜索`/etc/passwd`文件中有关键词`username`的内容，并打印出所在的行的第七列内容

- `head /etc/passwd | awk -F : 'BEGIN{print "name\tuid"}{print $1 "\t" $3}END{print "from file /etc/passwd"}'` => 用`head`命令提取`/etc/passwd`文件的前十行，用`awk`对这十行内容进行处理：

- - `-F :` => 用冒号将每一行分割成若干列

  - `BEGIN{print "name\tuid"}` => 打印`name    uid`，中间为制表符

  - `{print $1 "\t" $3}` => 提取并打印用冒号分隔后的第一列和第三列内容，中间用制表符隔开

  - `END{print "from file /etc/passwd"}` => 打印`from file /etc/passwd`

    其中，`BEGIN`表示在处理之前执行，`END`表示在处理之后执行

## du

### 作用

查看磁盘使用空间

### 案例

- `du` => 查看当前目录下所有文件和目录的容量大小
- `du -h dir` => 以易读的方式显示`dir`目录及其子目录大小
- `du -ah dir` => 以易读的方式显示`dir`目录内所有文件的容量大小
- `du file` => 单独查看`file`文件所占用的磁盘空间（一般都会加上`-h`选项易读）
- `du -s dir` or `du --max-depth=0 dir` => 仅查看`dir`目录的总大小（一般都会加上`-h`选项易读）

## df

### 作用

查看磁盘使用了多少空间以及剩余多少空间等信息

### 案例

- `df` => 显示磁盘使用空间情况
- `df -h` => 以易读的方式显示
- `df /home` => 显示指定文件/目录所在分区的磁盘空间使用情况
- `df -t squashfs` => 查看指定文件类型的磁盘使用情况
- `df -i` => 以`inode`模式来显示磁盘空间使用情况
- `df -a` => 显示所有信息，包含具有0 Blocks的文件系统
- `df -T` => 列出文件系统的类型

## sync

### 作用

强制将更改的内容立刻写入磁盘（一般情况下不需要手动执行）

在Linux系统中，在对文件或数据处理的过程中，一般都会先将其先放到内存的缓冲区，等到适当的时机再写入磁盘，以提高系统的运行效率

## mount

### 作用

把文件系统（一般指被格式化后的硬盘或分区设备，如：U盘、光驱等等）挂载到目录，之后，用户就可以直接在挂载的目录当中操作该文件系统

使用该命令需要管理员权限

### 案例

- `mount` => 查看当前系统中挂载的所有文件系统信息
- `mount -t tmpfs` => 查看指定类型挂载的文件系统
- `sudo fdisk -l | grep sd` => 查看系统当中已具有哪些`sd`设备<br>`sudo mkdir /mnt/udisk` => 一般都会挂载都`/mnt`目录下，如果设备过多，为了方便管理，可以在该目录下新建一个目录<br>`sudo mount /dev/sdb /mnt/udisk` => 将第一步中查看到的我们需要挂载的设备（如：U盘）挂载到`/mnt/disk`目录<br>**注意：**多个设备可以挂载到同一个目录，但是后挂载的设备会将之前挂载的设备的内容隐藏
- `sudo umount udisk` => 解除挂载
- `sudo mount -o ro /dev/sdb /mnt/udisk` => 只读模式挂载<br>**注意：**无法在以可读可写的方式挂载的同时又在新目录以只读模式挂载，此时需要用上一条命令`umount`来解除可读可写的挂载
- `sudo mount -o loop /home/username/commands/mount/mydisk.iso /mnt/iso` => 将iso镜像挂载到`/mnt/iso`目录

## umount

### 作用

卸载已经安装的文件系统目录或文件

### 案例

- `sudo umount /dev/sdb` => 通过设备名卸载
- `sudo umount /media/username/devicename` => 通过挂载点卸载

## dd

### 作用

拷贝及转换文件

可以完整拷贝文件，可以部分拷贝文件，也可以在拷贝的过程当中对内容进行转换

同时，利用该命令，可以测试磁盘的读取与写入速度

### 参数

- `if=file` => 默认从标准输入，即指定源文件
- `of=file` => 默认从标准输出，即指定目标文件
- `ibs=bytes` => 一次读入`bytes`个字节，即指定一个块大小为`bytes`个字节
- `obs=bytes` => 一次输出`bytes`个字节，即指定一个块大小为`bytes`个字节
- `bs=bytes` => 同时指定一次输入/输出`bytes`个字节
- `cbs=bytes` => 一次转换`bytes`个字节，即指定转换缓冲区大小
- `skip=blocks` => 从输入文件的开头跳过`blocks`个块后再开始拷贝
- `seek=blocks` => 从输出文件的开头跳过`blocks`个块后再开始拷贝
- `count=blocks` => 仅拷贝`blocks`个块，一个块大小等于`ibs/obs`指定的字节数
- `conv=<keywords>` => 指定关键字
- - `conversion` => 用指定的参数转换文件
  - `ascii` => 转换`ebcdic`为`ascii`
  - `ebcdic` => 转换`ascii`为`ebcdic`
  - `ibm` => 转换`ascii`为`alternate ebcdic`
  - `block` => 把每一行转换为长度为`cbs`字节的内容，不足的部分用空格填充
  - `unblock` => 使每一行的长度为`cbs`，不足的部分用空格填充
  - `lcase` => 大写转小写
  - `ucase` => 小写转大写
  - `swab` => 交换输入的每对字节
  - `noerror` => 出错时不停止
  - `notrunc` => 不截断输出文件
  - `sync` => 将每个输入快填充到`ibs`个字节，不足部分用空（NULL）字符补齐

### 案例

- `dd if=/dev/zero of=file bs=500M count=1` => 生成一个500M的文件<br>从`/dev/zero`文件中拷贝500M数据，一共拷贝一次，将这些数据写入一个名为`file`的文件中<br>**注意：**`/dev/zero`是一个特殊文件，它将源源不断为你提供0这个数据
- `dd if=file1 of=file2 bs=50 count=1` => 拷贝指定文件`file1`的前50个字节到目标文件`file2`中
- `dd if=file1 of=file2 conv=ucase` => 拷贝指定内容，同时小写转大写
- `dd conv=ucase` => 回车后在终端输入任意字符，按`ctrl + d`结束，转化为大写后的结果也将在终端显示

## tar

### 作用

打包/解压工具

### 参数

- `-c` => 新建打包文件
- `-x` => 解压文件，配合`-C`解压到对应的文件目录
- `-f` => （压缩或解压时）指定要处理的文件
- `-j` => 通过`bzip2`方式压缩或解压，最后以`.tar.br2`为后缀。压缩后大小小于`.tar.gz`
- `-z` => 通过`gzip`方式压缩或解压，最后以`.tar.gz`为后缀，一般使用得比较多
- `-v` => 显示操作过程
- `-t` => 查看打包文件中的内容
- `-C dir` => 指定压缩/解压缩的目录，若无指定，默认是当前目录

### 案例

- `tar -cvf files.tar *` => 将当前目录下所有文件打包（未压缩），并显示操作过程
- `tar -zcvf files.tar.gz *` => 将当前目录下所有文件用`gzip`方式压缩，并显示操作过程
- `tar -zxvf files.tar.gz` => 解压文件到当前目录下，如果当前目录下已存在文件则会被覆盖
- `tar -zxvf files.tar.gz -C dir` => 解压文件到当前目录的`dir`目录下
- `tar -tf files.tar.gz` => 列出压缩包里的内容

## zip && unzip

### 作用

压缩/解压，以`.zip`后缀结尾

### 案例

- `zip -r dir.zip dir` => 将`dir`目录下的所有文件和子目录用`zip`格式压缩成一个压缩包`dir.zip`
- `zip files.zip *.txt` => 将当前目录下所有以`.txt`结尾的文件用`zip`格式压缩成一个压缩包`files.zip`
- `zip -dv files.zip new_file` => 将当前目录下的`new_file`文件添加`-d`进已有的压缩包`files.zip`中，并且显示操作过程`-v`
- `unzip -l files.zip` => 查看压缩包中的文件
- `unzip -v files.zip` => 查看压缩包中的文件及其压缩比率
- `unzip -t files.zip` => 检查压缩包是否被损坏
- `unzip files.zip` => 解压压缩包到当前目录下
- `unzip files.zip -d dir` => 解压压缩包到指定目录下`dir`

## gzip && gunzip

### 作用

压缩/解压文件，以`.gz`后缀结尾，对文本的压缩比率通常能够达到60% ~ 70%

### 案例

- `gzip file` => 压缩`file`文件，默认压缩后的文件名为该文件名加上对应的后缀，即：`file.gz`。与此同时，原文件将被删除
- `gzip -r dir` => 压缩`dir`目录，但是`dir`目录不会被压缩，切换进该目录后，发现该目录下所有文件单独被压缩了，命名方式如上，且各个文件都会被删除
- `gzip -l *` => 查看当前目录下所有压缩包的信息，包括压缩比率
- `gzip -dv file.gz` or `gunzip -v file.gz` => 解压指定压缩包文件，并且显示操作过程`-v`，如果存在同名文件则会被覆盖
- `gzip -dr dir` or `gunzip -r dir` => 递归解压该目录下的所有压缩包文件
- `gzip -k file` => 压缩指定文件，但是不删除原文件
- `gunzip -t file.gz` => 测试指定压缩包文件内容是否被损坏

## uname

### 作用

显示系统信息

### 参数

- `a` => 系统所有相关信息
- `m` => 计算机硬件架构
- `n` => 主机名称
- `r` => 内核发行版本号
- `s` => 内核名称，如果直接使用`uname`命令，则默认加上该参数
- `v` => 内核版本
- `p` => 处理器类型
- `o` => 操作系统名称
- `i` => 硬件平台

### 案例

- `uname -a` => 显示系统主机名、内核版本、硬件架构等全部信息
- `uname -n` => 显示系统主机名
- `uname -r` => 显示内核发行版本号
- ......

## hostname

### 作用

显示和设置系统的主机名

### 案例

- `hostname` => 显示主机名
- `sudo hostname newname` => 临时改变主机名，系统重启后失效
- `hostname -I` => 显示主机的所有IP地址

### 永久修改系统主机名

方法1：修改配置文件

- `sudo vim /etc/hostname` => 修改其中内容
- `sudo vim /etc/hosts` => 将其中当前的主机名修改为想要更新为的主机名

方法2：`hostnamectl`命令

-  `sudo hostnamectl set-hostname newhostname` => 利用命令设置新主机名
- `sudo vim /etc/hosts` => 将其中当前的主机名修改为想要更新为的主机名

不难发现，两个方法中的第一步最终导致的结果是等价的，第二步是完全相同且必不可少的

## dmesg

### 作用

显示开机信息

开机信息一般保存在内核的环形缓冲区中：`/var/log/dmesg`

### 案例

- `dmesg` => 显示开机信息
- `dmesg | less` => 用`less`进行分页查看
- `dmesg | grep -i memory` => 显示与内存相关的信息
- `dmesg | grep -i usb` => 显示与usb相关的信息
- `dmesg -x` => 显示信息级别，如：`alert, err, warn, info, debug......`
- `dmesg --level=err,warn` => 只显示指定级别的信息
- `dmesg -T` => 显示时间戳
- `dmesg -r` => 显示原始数据
- `sudo dmesg -c` => 清空`dmesg`环形缓冲区中的日志

## uptime

### 作用

查看系统启动时间及负载信息

### 案例

- `uptime` => 显示当前系统运行负载信息
- `uptime -p` => 显示系统正常运行的时间
- `uptime -s` => 显示系统启动时间

## free

### 作用

显示系统内存使用量情况

### 参数

- `b` => 以`Byte`显示内存使用情况
- `k` => 以`kb`显示内存使用情况
- `m` => 以`mb`显示内存使用情况
- `g` => 以`gb`显示内存使用情况
- `s` => 持续显示
- `t` => 显示内存使用总和
- `h` => 以易读的单位显示内存使用情况

### 输出内容介绍

- `Mem`行（第二行）是内存的使用情况
- `Swap`行第三行是交换空间的使用情况
- `total`列显示系统总的可用物理内存和交换空间
- `used`列显示已经被使用的物理内存和交换空间
- `free`列显示还有多少物理内存和交换空间可供使用
- `shared`列显示被共享使用的物理内存大小
- `buff/cache`列显示被`buffer`和`cache`使用的物理内存大小
- `available`列显示还可以被应用程序使用的物理内存大小

### 案例

- `free` => 以默认的容量单位显示内存使用量情况
- `free -m` => 以`mb`为单位显示
- `free -h` => 以易读的单位显示（不统一单位，而是某个数字在哪个单位下易读就以哪个为单位显示）
- `free -hs 3` => 以易读的单位显示，每3秒刷新一次

## ulimit

### 作用

`Shell`的内建命令，用来控制`Shell`程序的资源，以达到系统调优的作用

### 参数

- `-a` => 显示目前资源限制的设定
- `-c <core文件上限>` => 设定`core`文件的最大值，单位为区块
- `-d <数据节区大小>` => 程序数据节区的最大值，单位为`kb`
- `-f <文件大小>` => `Shell`所能建立的最大文件，单位为区块
- `-H` => 限制资源的硬性限制，也就是管理员所设下的限制
- `-m <内存大小>` => 指定可使用的内存上限，单位为`kb`
- `-n <文件数目>` => 指定同一时间最多可开启的文件数
- `-p <缓冲区大小>` => 指定管道缓冲区的大小，单位为512字节
- `-s <堆栈大小>` => 指定堆栈上限，单位为`kb`
- `-S` => 设定资源的弹性限制
- `-t <CPU时间>` => 指定`CPU`使用时间的上限，单位为秒
- `-u <程序数目>` => 用户最多可开启的程序数目
- `-v <虚拟内存大小>` => 指定可使用的虚拟内存上限，单位为`kb`

### 案例

- `ulimit -a` => 显示系统资源的所有设置
- `ulimit -n 2048` => 将每个进程可以打开的文件数目加大到2048

## init

### 作用

切换系统运行级别

### 案例

- `init 0` => 关机
- `init 1` => 单用户模式
- `init 2` => 多用户，没有NFS不联网
- `init 3` => 多用户-命令行模式
- `init 4` => 没有用到
- `init 5` => 图形化界面模式
- `init 6` => 重新启动

## service

### 作用

控制系统服务，可以启动、停止、重新启动甚至直接关闭某个系统服务

### 案例

- `service --status-all` => 查看系统中所有服务现在的状态
- `service sshd status` => 查看`sshd`运行状态
- `service sshd start` =>  启动`sshd`服务
- `service sshd stop` => 停止`sshd`服务
- `service sshd restart` => 重启`sshd`服务

## vmstat

### 作用

显示虚拟内存状态，显示系统的进程、内存等整体的运行状态

### 案例

- `vmstat` => 显示虚拟内存使用情况
- `vmstat 1 3` => 每隔1秒采样一次，总共采样3次
- `vmstat -a` => 显示活跃和非活跃内存统计信息
- `vmstat -f` => 显示从系统启动以来的fork数量
- `vmstat -s` => 显示详细信息
- `vmstat -d` => 显示磁盘相关的信息（读/写情况）
- `vmstat -p /dev/sda1` => 查看`/dev/sda1`这个磁盘分区的读/写情况
- `sudo vmstat -m` => 显示系统的slabinfo

## iostat

### 作用

监视系统输入输出设备和CPU使用情况

### 案例

- `iostat` => 显示所有设备负载情况
- `iostat 2 3` => 每隔2秒显示一次，总共显示3次
- `iostat -d sda1` => 显示指定磁盘信息
- `iostat -t` => 显示tty和cpu信息
- `iostat -m` => 以M为单位显示
- `iostat -d -k 1 1` => 查看tps和吞吐量信息
- `iostat -x /dev/sda1` => 查看磁盘I/O详细情况
- `iostat -d -x -k 1 1` => 查看设备使用率`%util`、响应时间`await`
- `iostat -c 1 3` => 查看CPU状态

## ipcs

### 作用

显示进程间通信设备的状态，包括消息队列、共享内存以及信号量的信息

### 案例

- `ipcs` or `ipcs -a` => 显示所有的IPC
- `ipcs -t` => 输出信息的详细变化时间
- `ipcs -p` => 输出IPC方式的进程ID
- `ipcs -c` => 输出IPC方式的创建者/拥有者
- `ipcs -u` => 输出当前系统下IPC各种方式的状态信息
- `ipcs -l` => 查看各个资源的系统限制信息

## ipcrm

### 作用

删除一个或更多的消息队列、信号量集或者共享内存标识，同时将其`(IPC对象)`所关联的数据一并删除

只有超级用户以及IPC对象的创建者有权限删除

**注意：**删除可能用到的`id`或`key`需要通过`ipcs -c`或`ipcs`查看

### 案例

- `ipcrm -m id` => 通过`id`删除共享内存
- `ipcrm -M key` => 通过`key`删除共享内存
- `ipcrm -q id` => 通过`id`删除消息队列
- `ipcrm -Q key` => 通过`key`删除消息队列
- `ipcrm -s id` => 通过`id`删除信号量
- `ipcrm -S key` => 通过`key`删除信号量
- `ipcrm -a` => 删除所有共享内存、消息队列和信号量
- `ipcrm -v -a` => 删除所有共享内存、消息队列和信号量，并且显示过程

## route

### 作用

显示并设置IP路由表

### 参数

- `-n` => 不要使用通讯协议或主机名称，直接使用`IP`或`port number`
- `-net` => 表示后面接的路由为一个网域
- `-host` => 表示后面接的为连接到单部主机的路由
- `netmask` => 与网域有关，可以设定`netmask`决定网域大小
- `gw` => `gateway`的缩写，后续接的是`IP`的数值，与`dev`不同
- `dev` => 表示路由必须要经过的网关，后面接`eth0`等

### flag

- `U(Up)` => 表示此路由当前为启动状态
- `H(Host)` => 表示此网关为一主机
- `G(Gateway)` => 表示此网关为一路由器
- `R(Reinstate Route)` => 使用动态路由重新初始化的路由
- `D(Dynamically)` => 此路由是动态性地写入
- `M(Modified)` => 此路由是由路由守护进程或导向器动态修改
- `!` => 表示此路由当前为关闭状态

### 案例

- `route` or `route -n` => 显示当前路由
- `sudo route add -net 224.0.0.0 netmask 240.0.0.0 dev ens33` => 添加网关/设置网关
- `sudo route add -net 224.0.0.0 netmask 240.0.0.0 reject` => 屏蔽一条路由
- `sudo route del -net 224.0.0.0 netmask 240.0.0.0` or `sudo route del -net 224.0.0.0 netmask 240.0.0.0 reject` => 删除路由记录

## ping

### 作用

测试主机间网络连通性，测试网速等

### 参数

- `-c` => 指定发送报文的次数
- `-i` => 指定收发信息的间隔时间
- `-s` => 设置数据包的大小
- `-t` => 设置存活数值`TTL`的大小
- - `Linux`系统的`TTL`值为64或255
  - `Windows NT/2000/XP`系统的`TTL`值为128
  - `Windows 98`系统的`TTL`值为32
  - `UNIX`主机的`TTL`值为255

### 案例

- `ping www.baidu.com` => 测试与`www.baidu.com`网站的连通性
- `ping -c 4 www.baidu.com` => 连续`ping`四次
- `ping -c 4 -i 3 www.baidu.com` => 连续`ping`四次，每次之间间隔三秒
- `ping <IP Address>` => 测试局域网连通性<br>例如：测试局域网与物理机之间的网络连通性，需要提前知道物理机的`IP`地址是多少
- `ping -s 1024 -t 255 www.baidu.com` => 设置数据报为1024字节，TTL为255

## traceroute

### 作用

追踪数据包在网络上传输时的全部路径

试图以最小的`TTL`发出探测包来追踪数据包到达目的主机所经过的所有网关，然后监听来自网关`ICMP`的应答。一条路径上，每个设备`traceroute`都会测三次

### 案例

- `traceroute www.baidu.com` => 追踪本地数据包到百度的传输路径
- `traceroute -m 7 www.baidu.com` => 追踪指定量的跳数
- `traceroute -n www.baidu.com` => 显示`IP`地址而非主机名
- `traceroute -q 4 www.baidu.com` => 设置探测包的个数
- `traceroute -w 3 www.baidu.com` => 设置对外发探测包的等待时间，以秒为单位
- `traceroute -p 6888 www.baidu.com` => 设置基本`UDP`端口
- `traceroute -r www.baidu.com` => 绕过正常的路由表，直接发送到网络相连的主机

## ifconfig

### 作用

显示或设置网络设备参数信息

通常不建议直接使用`ifconfig`命令来修改配置网络信息，因为一旦重启，配置过的参数就会失效

### 案例

- `ifconfig` => 显示网络设备信息
- `sudo ifconfig eth0 up` / `sudo ifconfig eth0 down` => 打开/关闭指定网卡
- `sudo ifconfig eth0 192.168.1.56` => 为网卡`eth0`配置`IP`地址
- `sudo ifconfig eth0 192.168.1.56 netmask 255.255.255.0` => 为网卡`eth0`配置`IP`地址与子网掩码
- `sudo ifconfig eth0 192.168.1.56 netmask 255.255.255.0 broadcast 192.168.1.255` => 为网卡`eth0`配置`IP`地址、子网掩码以及广播包
- `sudo ifconfig eth0 add <IPv6 Address>` => 为网卡设置`IPv6`地址
- `sudo ifconfig eth0 del <IPv6 Address>` => 为网卡删除`IPv6`地址
- `sudo ifconfig eth0 down`<br>`sudo ifconfig eth0 hw ether <MAC Address>`<br>`sudo ifconfig eth0 up`<br>先关闭，然后修改`MAC`地址，最后再启动
- `sudo ifconfig eth0 arp` / `sudo ifconfig eth0 -arp` => 启动/关闭`ARP`协议
- `sudo ifconfig eth0 mtu 1500` => 设置最大传输单元为1500字节

## ifup && ifdown

### 作用

激活/禁用网络接口

### 案例

- `sudo ifup eth0` => 激活`eth0`网络接口
- `sudo ifdown eth0` => 关闭`eth0`网络接口

## netstat

### 作用

显示网络状态，包括路由表、实际网络连接、每一个网络接口等

### 案例

- `netstat -a` => 显示系统网络状态中的所有连接信息
- `netstat -at` => 显示`TCP`连接信息
- `netstat -au` => 显示`UDP`连接信息
- `netstat -p` => 显示`PID`和进程名
- `netstat -l` => 显示监听端口
- `netstat -lt` => 显示`TCP`监听端口
- `netstat -lu` => 显示`UDP`监听端口
- `netstat -lx` => 显示`UNIX`监听端口
- `netstat -s` => 显示所有端口的统计信息
- `netstat -st` => 显示`TCP`端口的统计信息
- `netstat -su` => 显示`UDP`端口的统计信息
- `netstat -apu` => 显示`UDP`连接端口号使用信息
- `netstat -i` => 显示网卡当前状态信息
- `netstat -r` => 显示网络路由表状态信息
- `netstat -ap | grep ssh` => 找到某个服务器所对应的连接信息

## ss

### 作用

显示活动套接字信息

### 参数

- `-n` => 不解析服务名称，以数字方式显示
- `-a` => 显示所有套接字
- `-l` => 显示处于监听状态的套接字
- `-o` => 显示计时器信息
- `-e` => 显示详细的套接字信息
- `-m` => 显示套接字的内存使用情况
- `-p` => 显示使用套接字的进程
- `-i` => 显示内部的`TCP`信息
- `-s` => 显示套接字使用概况
- `-4` => 仅显示`IPv4`的套接字
- `-6` => 仅显示`IPv6`的套接字
- `-O` => 显示`PACKET`套接字
- `-t` => 仅显示`TCP`套接字
- `-u` => 仅显示`UDP`套接字
- `-d` => 仅显示`DCCP`套接字
- `-w` => 仅显示`RAW`套接字
- `-x` => 仅显示`UNIX`套接字
- `-D` => 将原始`TCP`套接字信息转储到文件

### 案例

- `ss -at` => 显示`TCP`套接字
- `ss -au` => 显示`UDP`套接字
- `ss -s` => 显示套接字使用概况
- `ss -l` => 列出所有打开的网络连接端口
- `ss -lp` => 查看进程使用的`socket`
- `ss -lp | grep 6010` => 找出打开套接字/端口的应用程序
- `ss -tnl` => 查看主机监听的端口
- `ss -tlr` => 解析`IP`和端口号

## telnet

### 作用

远程登入服务器，但是它采用的是明文的传送报文，安全性不强

### 案例

- `telnet <address>` => 远程登录
- `telnet <address> <port>` => 指定端口

## ssh

### 作用

远程连接工具，使用`ssh`加密协议，安全性高

配置文件：`/etc/ssh/sshd_config`

### 案例

- `ssh <address>` => 远程登录
- `ssh <username@address>` or `ssh -l <username@address>` => 以`username`身份远程登录
- `ssh -p <port> <username@address>` => 指定端口号及用户名远程登录
- `ssh <address> date` => 远程执行命令，并且在终端返回结果

## ftp

### 作用

文件传输协议客户端工具，数据未加密，安全性不高

### 增加ftp写权限

1. `sudo gedit /etc/vsftpd.conf`
2. 去除`#write_enable=YES`前的`#`，即去除该行的注释符号
3. `sudo service vsftpd restart`

### 案例

- `ftp <address>` => 建立`FTP`连接
- `get file` => 下载文件
- `mget file1 file2` => 下载多个文件
- `put file` => 上传文件
- `mput file1 file2` => 上传多个文件

## sftp

### 作用

交互式的文件传输工具，数据使用`ssh`加密，安全性高

### 案例

- `sftp <username@address>` => 连接服务器
- `sftp -P <port> <username@address>` => 指定端口
- `help` or `?` => 查看支持的命令
- `get file` => 从远程服务器下载文件
- `get -r dir` => 从远程服务器下载目录
- `put file` => 从本地上传文件
- `put -r dir` => 从本地上传目录
- `!command` => 执行本地`Shell`命令，如：`!echo hello world`
- `bye` or `exit` => 退出连接

## lftp

### 作用

功能强大的下载工具，支持很多协议：`ftp, ftps, http, https...`

界面及功能非常像`Shell`，允许多个后台任务执行，书签排队，镜像，断点续传，多线程下载等

### 案例

- `lftp <username@address>` => 远程登录
- `help` or `?` => 查看支持的命令
- `get file` or `mget file*` or `mget -c *.txt` => 下载文件/多个文件到本地<br>如果文件已存在，会报错，不会覆盖，但不会影响其它文件传输<br>`-c` => 断点续传，如果网络不稳定，或者文件比较大，下次下载的时候就可以直接在上一次传输的中途继续下载
- `mirror dir` => 下载目录到本地
- `put file` or `mput *` => 从本地上传文件/多个文件
- `mirror -R dir` => 从本地上传目录
- `bye` or `exit` => 退出连接

## wget

### 作用

从指定的`url`上去下载文件，支持断点下载

如果下载的内容与已存在的内容重名了，那么新下载的内容会自动在文件名末尾添加`.1`之类的标识以区分

### 参数

- `-i` => 下载指定文件里列出的地址
- `-O` => 下载后重命名文件
- `-c` => 打开断点续传
- `-b` => 启动后转入后台执行
- `-P` => 指定保存路径

### 案例

- `wget https://...` => 下载单个文件
- `vim urllist`<br>`wget -i urllist`<br>=><br>在`urllist`文件中键入所有需要下载的文件的地址，然后使用`-i`参数从文件里列出的地址一一下载
- `wget -O rename https://...` => 将下载的文件重命名为`rename`
- `wget -P dir https://...` => 将下载的文件保存到指定的目录`dir`
- `wget --limit-rate=300k https://...` => 限速下载
- `wget -c https://...` => 打开断点续传<br>比如：下载到一半，由于网络因素等原因断开了连接（手动用`ctrl + c`来模拟），等问题排除后再一次运行相同的命令，下载不会从`0%`开始，而是继续从中断的位置往后下载
- `wget -b https://...` => 后台下载<br>`tail -f wget-log` => 查看下载进度

## scp

### 作用

远程拷贝文件

### 案例

- `scp username@IP_Address:~/file ~` => 从远程服务器指定用户的家目录下的`file`文件，下载到本地的家目录下
- `scp -r username@IP_Address:~/dir ~` => 从远程服务器指定用户的家目录下的`dir`目录及其下的所有文件，下载到本地的家目录下
- `scp ~/file username@IP_Address:~` => 从本地上传`file`文件到远程服务器指定用户的家目录下
- `scp -r ~/dir username@IP_Address:~` => 从本地上传`dir`目录及其下的所有文件到远程服务器指定用户的家目录下
- `scp -P 2222 ......` => 使用指定端口号`2222`进行传输
- `scp -p ......` => 保留文件的最后修改时间及访问时间

## curl

### 作用

数据传输工具

### 参数

- `-o` => 指定新的本地文件名
- `-O` => 保留远程文件的原始名
- `-u` => 通过服务端配置的用户名和密码授权访问
- `-I` => 打印`HTTP`响应头信息
- `-A` => 设置用户代理标头信息
- `-b` => 设置用户`cookie`信息
- `-C` => 支持断点续传
- `-s` => 静默模式，不输出任何信息
- `-T` => 上传文件

### 案例

- `curl www.baidu.com` => 获取指定网站的网页源码
- `curl -o baidu.html www.baidu.com` => 保存网页
- `curl -O https://...` => 下载指定网站中的文件
- `curl -o test.zip https://...` => 下载并重命名为`test.zip`
- `curl -C - -O https://...` => 断点续传
- `curl -I https://...` => 打印指定网站的`HTTP`响应头文件
- `curl -u user:passwd ftp://...` => 通过`ftp`下载指定文件服务器中的文件
- `curl -T file -u user:passwd ftp://...` => 将本地的`file`文件通过`ftp`上传到指定的文件服务器中的指定目录下

## host

### 作用

域名查询，测试域名系统工作是否正常

### 案例

- `host www.baidu.com` => 查询域名对应的`IP`地址
- `host -v www.baidu.com` => 显示执行域名查询的详细信息
- `host -a www.baidu.com` => 显示详细的`DNS`信息

## tcpdump

### 作用

监听网络流量，能够记录所有经过服务器的数据包的信息，运行该命令需要管理员权限

### 案例

- `tcpdump` => 监视第一个网络接口上所有流过的数据包
- `tcpdump -i eth0` => 监视指定网络接口的数据包<br>通过`ifconfig`来查看当前系统下有哪些网络接口
- `tcpdump -c 20` => 显示指定数量的包
- `tcpdump -c 10 -q` => 以精简模式显示指定数量的包
- `tcpdump host <Hostname>` => 监视指定主机的数据包（主机名）
- `tcpdump host <IP Address>` => 监视指定主机的数据包（`IP`地址）
- `tcpdump -i any port 22 -A` => 监听指定端口号的数据包，并以文本形式展示

## nc

### 作用

设置路由器，支持测试`Linux`的`TCP`和`UDP`端口，也经常被使用于端口的扫描

### 参数

- `-v` => 显示执行过程
- `-w<超时秒数>` => 设置等待连线的时间
- `-z` => 使用0输入/输出模式，只在扫描通信端口使使用
- `-n` => 直接使用`IP`地址，而不通过域名服务器
- `-u` => 使用`UDP`传输协议
- `-l` => 使用监听模式，管控传入的资料

### 案例

- `nc -v -z -w2 <IP Adress> 1-100` => 扫描指定`IP`的`TCP`端口，范围为`1-100`
- `nc -u -z -w2 <IP Adress> 1-100` => 扫描指定`IP`的`UDP`端口，范围为`1-100`
- `nc -nvv <IP Adress> <port>` => 扫描指定端口
- `nc -l <port>` => 监听某个端口
- `nc <IP Adress> <port>` => 连接某个端口

## useradd

### 作用

创建并设置账户信息

### 参数

- `-d<登入目录>` => 指定用户登入时的目录
- `-g<群组>` => 初始群组
- `-G<群组>` => 非初始群组
- `-m` => 自动创建用户的家目录
- `-M` => 不要创建用户的家目录
- `-N` => 不要创建以用户名为名的群组
- `-s` => 指定用户登入后所使用的`Shell`

### 重要文件

- `/etc/passwd` => 记录用户的信息<br>记录的格式：`<username>:<password>:<userID>:<groupID>:<注释信息>:<家目录>:<shell>`，其中，`password`是隐藏的，用`x`代替显示
- `/etc/shadow` => 每个用户经过加密后的密码，如果没设置密码用`!`表示
- `/etc/group` => 组信息
- `/etc/gshadow` => 组对应的密码信息，一般不对其设置，除非需要很高的安全性

### 案例

- `useradd user1` => 直接创建新用户，用户名为`user1`
- `useradd -m -s /bin/bash user2` => 常用创建方式
- `useradd -m -d /new/dir user3` => 指定家目录
- `useradd -u 1500 user4` => 指定用户`ID`
- `useradd -g <group> user5` => 指定组`ID`
- `useradd -g <group> -G <group1,group2> user6` => 分配多个组
- `useradd -c "Test User Account" user7` => 自定义注释

## adduser

### 作用

创建用户账户，与`useradd`不同的是，`adduser`是一个人机交互的过程，会一步步引导你输入对应的信息，而`useradd`如果不自己手动添加参数或后续设置，将创建一个三无账户

### 案例

`adduser` => 根据交互内容，一步步输入信息以创建账户

## passwd

### 作用

修改用户的密码

### 参数

- `-d` => 删除已有密码
- `-l` => 锁定密码，不允许修改
- `-u` => 解除锁定，允许修改
- `-e` => 下次登录强制修改密码
- `-k` => 用户在期满后仍能使用
- `-S` => 查询密码状态

### 案例

- `passwd` => 修改当前用户的密码
- `passwd username` => 修改指定用户的密码（需要有管理员权限，同时还得知道该用户当前的密码）

## userdel

### 作用

删除用户账户

### 案例

- `userdel username` => 删除指定的用户账户信息
- `userdel -r username` => 删除指定的用户账户信息、家目录及其目录下所有文件

## su

### 作用

切换用户身份

### 案例

- `su` or `su root` => 切换超级用户（某些系统不允许你切换超级用户）
- `su -c whoami username` => 变更账号为`username`，在执行完`whoami`这一条命令后立即退出
- `su username` => 变更账号为`username`并保留在当前工作目录
- `su - username` => 变更账号为`username`，同时切换到对应的家目录

## sudo

### 作用

以系统管理员身份执行指令

### 配置文件

`/etc/sudoers`

查看配置文件：<br>`sudo visudo`<br>or<br>`sudo vim /etc/sudoers`

### 案例

- `sudo -l` => 列出当前用户的权限
- `sudo -u username whoami` => 指定以`username`这一身份去执行`whoami`这一条命令，默认情况下不加`-u`则是以管理员身份执行
- `sudo !!` => 以管理员权限执行上一条命令

## id

### 作用

显示用户`ID`和组`ID`

### 案例

- `id` => 显示当前用户的所有信息

- `id username` => 显示指定用户信息

- `id -g username` => 显示指定用户所属组群的`ID`

- `id -G username` => 显示指定用户所属附加组群的`ID`

  参数后不加用户名，则默认显示当前用户的信息

## usermod

### 作用

修改用户账户信息

### 参数

- `-c <备注>` => 修改用户账户的备注文字
- `-d <登入目录>` => 修改用户登录时的家目录
- `-e <有效期限>` => 修改账号的有效期限
- `-f <缓冲天数>` => 修改在密码过期后多少天即关闭该账号
- `-g <群组>` => 修改用户所属的群组
- `-G <群组>` => 修改用户所属的附加群组
- `-l <账号名称>` => 修改用户账号名称
- `-L` => 锁定用户密码，使密码无效
- `-s <Shell>` => 修改用户登录后所使用的`Shell`
- `-u <uid>` => 修改用户`ID`
- `-U` => 解除密码锁定

### 案例

- `usermod -d /home/hometest username` => 将账户`username`的家目录更改为`/home/hometest`
- `usermod -u 1234 username` => 将账户`username`的`ID`更改为`1234`
- `usermod -l newname oldname` => 将账户`oldname`更名为`newname`
- `usermod -L username` => 锁定账户`username`
- `usermod -U username` => 解锁账户`username`

## groups

### 作用

显示用户加入的所有的用户组

### 案例

`groups username` => 显示用户`username`加入的所有的用户组

## groupadd

### 作用

创建新的用户组

### 案例

- `groupadd work` => 创建一个名为`work`的用户组

- `groupadd -g 1234 work` => 创建一个名为`work`，用户组组`ID`为`1234`的用户组

- `groupadd -r grouptest` => 创建一个新的用户组，并将其设定为系统工作组

  系统工作组`GID`定义在文件`/etc/login.defs`，字段是`SYS_GID_MIN`和`SYS_GID_MAX`，前者默认`100`，后者默认`999`，可自行修改

## groupdel

### 作用

删除用户组

### 案例

`groupdel groupname` => 将用户组`groupname`删除

## whoami

### 作用

打印当前登录的用户

### 案例

`whoami` => 查询当前登录的用户名

## who

### 作用

查看当前登录至系统的所有用户的信息

一个终端登入就算一个，所以查询得到的结果可能包含多个相同用户

### 案例

- `who` => 查看当前登录至系统的用户信息
- `who -H` => 查看当前登录至系统的用户信息，并加上标题栏
- `who -H -a` => 查看当前登录至系统的全部用户信息
- `who -b` => 查看系统的最近启动时间
- `who -T -H` => 显示终端属性
- `who -q` => 以精简模式显示

## w

### 作用

显示已登入系统的用户列表，同时显示用户正在执行的命令

### 案例

- `w` => 显示目前登入系统的用户列表
- `w -h` => 不打印标题栏
- `w -f` => 显示/不显示用户从哪登录
- `w -s` => 使用短格式输出

## last

### 作用

显示用户或终端的登录情况，可以看出谁曾经或企图登录系统

### 参数

- `-R` => 省略`hostname`的栏位
- `-a` => 把从何处登入系统的主机名或`IP`地址显示在最后一行
- `-n <显示行数>` or `-<显示行数>` => 指定显示个数
- `-i`=> 显示`IP`地址而不是主机名

### 案例

- `last` => 显示近期用户或终端的登录情况
- `last -n 5 -R` or `last -5 -R` => 简略显示，并指定显示个数
- `last -n 5 -a -i` => 最后一列显示主机`IP`地址

## users

### 作用

显示当前登录至系统的用户

一个终端登入就算一个，所以查询得到的结果可能包含多个相同用户

### 案例

`users` => 显示当前登录至系统的用户

## top

### 作用

实时显示动态进程

### 参数

- `-d` => 指定每两次屏幕信息刷新之间的时间间隔（单位为秒）
- `-c` => 切换显示命令名称和完整命令行
- `-p` => 通过指定监控进程`ID`来仅仅监控某个进程的状态
- `-n` => 信息更新最大次数

### 快捷键

- `c` => 显示进程绝对路径
- `P` => 根据`CPU`使用率排行
- `M` => 根据物理内存使用率排行
- `1` => 显示每个核的`CPU`状况

### 案例

- `top` => 实时显示进程动态
- `top -c` => 显示完整的进程信息<br>与直接`top`打开后按快捷键`c`等效
- `top -d 5` => 指定信息刷新时间间隔为5秒
- `top -p 1877` => 仅监控进程`ID`为1877的进程动态
- `top -n 2` => 设置信息刷新次数

## ps

### 作用

显示进程状态

### 参数

- `-A` => 显示所有进程
- `-a` => 显示所有终端机下执行的程序
- `-x` => 通常与`-a`一起使用，可以列出较为完整的信息
- `-e` => 列出程序时，显示每个程序所使用的环境变量
- `-f` => 用`ASCII`字符显示树状结构，表达程序间的相互关系
- `-u <用户识别码>` => 列出属于该用户的程序的状况，也可以使用用户名称来指定

### 信息说明

- `USER` => 用户名称
- `PID` => 进程号
- `%CPU` => 该进程所占用的`CPU`百分比
- `%MEM` => 该进程所占用的内存百分比
- `VSZ` => 该进程所占用的虚拟内存大小
- `RSS` => 进程所占用的实际内存大小
- `TTY` => 该进程运行在哪个终端上，若与终端无关，则显示
- `STAT` => 进程状态：
- - `R` => 运行
  - `S` => 可中断睡眠
  - `D` => 不可中断睡眠
  - `T` => 停止
  - `Z` => 僵死
- `START` => 进程启动时间
- `TIME` => 进程实际占用`CPU`的时间
- `COMMAND` => 该进程对应的执行程序

### 案例

- `ps -aux` => 列出目前所有的正在内存当中的程序<br>内容较多不方便查看的话可以通过管道给`less`打开：`ps -aux | less`
- `ps -A` => 显示所有进程信息
- `ps -ef` => 显示所有进程信息，连同命令行
- `ps -axf` => 树形显示所有进程
- `ps -aux | grep ssh` => 查找特定进程信息
- `ps -u username` => 显示指定用户信息
- `ps -aux | sort -rnk 3` => 依据处理器使用量（第三列）的情况降序排序

## pstree

### 作用

以树状图显示进程

### 案例

- `pstree` => 以树状图显示进程
- `pstree -a` => 显示该进程的完整指令及参数，遇到相同的进程名可以压缩显示
- `pstree -p` => 显示当前所有进程的进程号和进程`ID`
- `pstree -u` => 同时显示用户名

## pgrep

### 作用

检索当前正在运行的进程

### 参数

- `-d` => 设置一个字符串，用于分隔输出的每个进程`ID`
- `-f` => 匹配进程名（绝对路径）
- `-l` => 列出进程名及其进程`ID`
- `-u` => 选择仅匹配指定有效用户进程
- `-a` => 显示更多内容

### 案例

- `pgrep sshd` => 查找`sshd`进程的`pid`
- `pgrep sshd -d' '` => 指定分隔符输出<br>此时显示为一行，每个`pid`之间用空格隔开
- `pgrep -u username sshd` => 查询用户`username`启动的`sshd`进程的`pid`
- `pgrep -l sshd` => 显示进程名及`pid`
- `pgrep '^sshd$' -l` => 使用正则表达式
- `pgrep -f ssh` => 匹配进程名（绝对路径中是否包含某字符串）

## lsof

### 作用

查看进程打开的文件

### 参数

- `-a` => 列出打开文件存在的进程
- `-c <进程名>` => 列出指定进程打开的文件
- `-g` => 列出`GID`号进程详情
- `-d <文件号>` => 列出占用该文件号的进程
- `+d <目录>` => 列出目录下被打开的文件
- `+D <目录>` => 递归列出目录下被打开的文件
- `-n <目录>` => 列出使用`NFS`的文件
- `-i <条件>` => 列出符合条件的进程
- `-p <进程号>` => 列出指定进程号打开的文件
- `-u` => 列出`UID`号进程详情

### 案例

- `lsof` => 查看当前系统中全部文件与进程之间的对应信息<br>若查询结果出现`unknown`，说明这一条信息需要管理员权限
- `lsof +d /home` => 显示指定目录中被调用的文件信息
- `lsof +D /home` => 递归显示指定目录中全部被调用的文件信息
- `lsof /bin/bash` => 查看谁正在使用某个文件（查找某个文件相关的进程）
- `lsof -u username` => 列出某个用户打开的文件信息
- `lsof -c bash` => 列出某个进程所打开的文件信息
- `lsof -p 1930` => 通过某个进程号显示该进程打开的文件
- `lsof -d 1` => 根据文件描述列出对应的文件信息

## jobs && bg && fg

### 作用

终端任务调度

### 案例

- `jobs -l` => 列出当前`Shell`的任务
- `fg 2` => 将2号任务调到前台运行
- `ctrl + z` => 将当前进程切到后台，但状态会停止`Stopped`
- `bg 2` => 恢复2号任务在后台运行（可以唤醒`Stopped`为`Running`）
- `kill %3` => 杀死3号任务，状态更改为`Terminated`<br>直接`kill 3`会报错，因为这代表另外的含义，具体可见下一节内容<br>上述命令中的`fg/bg`后接的编号前也可以加`%`

## kill

### 作用

发送信号到进程

### 常用信号

- `HUP 1` => 终端断线
- `INT 2` => 中断，同`ctrl + c`
- `QUIT 3` => 退出，同`ctrl + \`
- `TERM 15` => 终止
- `KILL 9` => 强制终止
- `CONT 18` => 继续，与`STOP`相反
- `STOP 19` => 暂停，同`ctrl + z`

### 案例

- `kill -l` => 列出系统支持的所有信号
- `kill 1951` => 不指定信号，通过进程号来终止某一个进程，等同于发送终止信号<br>有的进程可能会忽略这个信号从而不终止，此时需要发送强制终止：`kill -9 1951`
- `kill -l KILL` => 查看`KILL`这个信号对应的数值
- `kill -9 $(ps -ef | grep username)` => 杀死指定用户`username`的所有进程

## killall

### 作用

杀死一个或一组命令

### 案例

- `killall sleep` => 杀死所有名为`sleep`的进程
- `killall -l` => 查看`killall`支持的所有信号
- `killall -9 sleep` => 发送指定信号
- `killall -u username` => 杀死指定用户的所有进程

## nice && renice

### 作用

调整进程的优先级

### 案例

- `ps -l` => 查看`nice`值，即标题为`NI`的列
- `nice -n 15 vim &` or `nice -15 vim &` => 启动`vim`命令在后台运行，同时将它的`nice`值设为15<br>`nice`值可设置范围在`-20 ~ 19`<br>**注意：**`-n 15`是直接设置为`15`，而`-15`是在原值的基础上增加`15`
- `renice 6 -p 5200` => 根据`pid`重新设置`nice`值为`6`
- `renice -5 -u username` => 根据用户名重新设置`nice`值为`-5`

## nohup

### 作用

后台运行程序

### 案例

- 有一个每隔1秒打印一段文字的程序：`./test`<br>在后台运行：`./test &`，但是输出的文字还是会占用终端，而且，在关闭终端后该进程也将终止<br>与终端切断关联：`nohup ./test &`，同时，输出的内容将会保存到`test`程序同级目录下的`nohup.out`文件中
- `nohup ./test > file 2>&1 &` => 将输出重定向到`file`文件中<br>其中，`2>&1`表示：将标准错误输出重定向到标准输出中，而标准输出又被重定向到了`file`文件，所以，该进程产生的所有输出都将被重定向到`file`文件<br>但是，运行后立即`cat file`将发现没有任何内容，因为它存在一定缓存，需要到一定量才会输出到文件，过一会儿后再查看，会发现里面存在内容

## apt

### 作用

包管理器

### 案例

- `sudo apt update` => 列出所有可更新的软件清单
- `sudo apt upgrade` => 升级所有可更新的软件包
- `sudo apt upgrade vim` => 单独升级某一个软件包
- `sudo apt install bat` => 安装软件包
- `sudo apt remove bat` => 删除软件包
- `sudo apt show bat` => 打印软件包信息
- `sudo apt autoremove` => 清理不再使用的依赖和库文件
- `sudo apt list --installed` => 列出已安装的所有软件包

## apt-get

### 作用

包管理器

### 与`apt`异同点

最初，包管理器被分散在`apt-get, apt-cache, apt-config`这三个命令中，而`apt`包管理则是为了解决命令过于分散的问题，它相当于是这三个中最常用命令选项的集合

`apt`视觉功能更好

`apt`替换了部分`apt-get`系列命令，同时也有它独有的新增的命令

### 选择

建议尽快适应并首选`apt`

## export

### 作用

设置或显示环境变量

环境变量指：在操作系统当中，用来指定操作系统运行的环境的一些参数，例如：`PATH`，它用来保存可以搜索的目录、路径，可以通过`echo $PATH`查看

### 参数

- `-f` => 代表`<变量名称>`中为函数名称
- `-n` => 删除指定的变量<br>实际上未被删除，只是不会输出到后续指令的执行环境中
- `-p` => 列出所有的`Shell`赋予程序的环境变量

### 注意

- `export`的作用效果仅限于本次登录
- 想要永久生效需要修改配置文件：
- - `/etc/profile` => 所有用户
  - `~/.bashrc` => 当前用户

### 案例

- `export -p` => 列出当前所有的环境变量
- `export MYENV` => 定义环境变量
- `export MYENV=666` => 定义环境变量并赋值
- `export PATH=$PATH:/usr/local/mysql/bin` => 修改环境变量
- `echo $PATH` => 查看环境变量

## source

### 作用

在当前`Shell`环境中从指定文件读取和执行命令，例如：在修改配置文件后，将其`source`一下，就能使其生效，而不是重启

可以使用`.`来替代

### 案例

- `source ~/.bashrc` or `. ~/.bashrc` => 读取和执行`.bashrc`文件
- `source /etc/profile` => 执行刚修改的初始化文件，使之立即生效

## set && unset

### 作用

设置/删除`Shell`变量

### 案例

- `set` => 显示所有的`Shell`变量
- 1. `declare myenv="666"` => 定义一个新的变量
  2. `set -a myenv` => 将定义的变量输出到环境变量
  3. `env | grep myenv` => 查看是否设置成功
- `unset -v myenv` => 删除环境变量<br>**注意：**参数`-v`表示仅删除变量，参数`-f`表示仅删除函数
- `unset myenv` => 优先删除变量

## echo

### 作用

在终端输出字符串

### 参数

- `-n` => 不输出结尾的换行符
- `-e "\a"` => 发出警告音
- `-e "\b"` => 删除前面一个字符
- `-e "\c"` => 结尾不加换行符，同时，`\c`后面的字符不会输出
- `-e "\f"` => 换行，光标仍停留在原来的坐标位置
- `-e "\n"` => 换行，光标移到行首
- `-e "\r"` => 光标移到行首，但不会换行，会覆写行开头的字符
- `-E` => 禁止反斜杠转译，与`-e`参数功能相反

### 案例

- `echo "Hello World"` or `echo Hello World` => 在终端输出`Hello World`

- `echo $PATH` => 输出变量提取后的值

- `echo \$PATH` => 取消转译

- `echo "Hello echo" > file` => 重定向输出

- ```bash
  echo `date`
  # 显示命令执行结果
  ```

- `echo -e "a\nb\nc"` => 输出带有换行符的内容（开启转译）

## printf

### 作用

格式化并输出结果

### 转译字符

- `\a` => 警告字符，通常为`ASCII`的`BEL`字符
- `\b` => 后退
- `\c` => 不显示输出结果中任何结尾的换行符，而且任何留在参数里的字符，任何接下来的参数以及任何留在格式字符串中的字符都被忽略
- `\f` => 换页
- `\n` => 换行
- `\r` => 回车
- `\t` => 水平制表符
- `\v` => 垂直制表符
- `\\` => 反斜杠字符

### 格式替代符

- `%c` => `ASCII`字符，显示相对应参数的第一个字符
- `%d %i` => 十进制整数
- `%E` => 浮点格式
- `%e` => 浮点格式
- `%g` => `%e`和`%f`之间转换，看哪一个较短，则删除结尾的零
- `%G` => `%E`和`%f`之间转换，看哪一个较短，则删除结尾的零
- `%s` => 字符串
- `%u` => 不带正负号的十进制整数
- `%x` => 不带正负号的十六进制，使用`a ~ f`来表示`10 ~ 15`
- `%%` => 字面意义的`%`
- `%X` => 不带正负号的十六进制，使用`A ~ F`来表示`10 ~ 15`

### 案例

- `printf "%d %s\t%d\n" 666 "Hello printf" 999` => 常见格式化字符，输出：`666 Hello printf	999`
- `printf "%-10s%-8s%-4.2f\n" first second 1.1234` => 输出：`first     second  1.12`<br>`%10s` => 该字符串宽度为`10`，若字符串长度不足则在字符串前用空格补齐<br>`%-10` => 含义同上，只不过当长度不足时在字符串后用空格补齐<br>`%-4.2f` => 该浮点数的整数部分最多显示四位，小数部分最多显示两位，`-`表示左对齐，所以`1.1234`格式化后为`1.12`

## clear

### 作用

清除屏幕

## history

### 作用

显示并管理历史命令

### 参数

- `-c` => 清空命令记录
- `-d` => 删除指定序号的命令记录
- `-n` => 读取命令记录

### 案例

- `history` => 显示执行过的全部命令记录
- `history 5` => 显示执行过的最近5条命令
- `!2039` => 重新执行2039号命令
- `!!` => 重新执行上一条命令
- `!ls` => 将搜索与你输入相匹配的最近一个命令，并重新执行它
- `ctrl + r` => 调用命令历史记录的递归搜索
- `history -d 1234` => 删除特定序号的命令
- `history -c` => 清空全部历史记录

## login && logout

### 作用

登入/登出系统

## exit

### 作用

退出终端/ssh连接

### 案例

- `exit`
- `ctrl + d`

## xargs

### 作用

过滤器

### 参数

- `-n` => 多行输出
- `-d` => 自定义一个定界符
- `-I` => 指定一个替换字符串`{}`
- `-t` => 打印`xargs`执行的命令
- `-p` => 执行每一个命令时弹出确认

### 案例

- `cat file | xargs` => 多行输入单行输出，将换行符替换为空格
- `cat file | xargs -n3` => 分成三列进行输出
- `echo "hello:hello:hello" | xargs -d:` => 通过`:`进行分割，输出为`hello hello hello`
- `echo "hello:hello:hello" | xargs -d: -p` => 执行每一个命令时弹出确认
- `ls | xargs -t -I {} echo {}` => 将`ls`结果的每一行都作为参数给`echo`命令，用`-t`来打印`xargs`执行的命令
- `find . -name "*.txt" | xargs -I {} mv {} dir` => 查找当前文件下的所有后缀为`txt`的文件，将它们移动到`dir`目录下
- `cat url-list | xargs wget -c` => 使用`wget`下载`url-list`下所有的`URL`<br>如果添加`-I`是一行一行输送，而这里是整体输送

## exec

### 作用

调用并执行指定命令

### 案例

- `exec -c echo hello world` => 调用并执行指定的命令，如果是在终端输入，那么在执行完后会退出终端
- `find . -name "*.txt" -exec ls {} \;` => 结合`find`命令使用

## alias && unalias

### 作用

设置/取消命令别名

### 案例

- `alias` => 查看系统已设置的别名
- `alias "rm=rm -i"` => 给命令设置别名
- `unalias rm` => 取消别名

## type

### 作用

显示指定命令的类型

### 参数

- `-a` => 可以显示所有可能的类型，比如有些命令如`pwd`是`Shell`内建命令，同时也可以是外部命令
- `-p` => 只返回外部命令的信息，相当于`which`命令
- `-f` => 只返回`Shell`函数的信息
- `-t` => 返回指定类型的信息

### 常见类型

- `alias` => 别名
- `keyword` => 关键字，`Shell`保留字
- `function` => 函数，`Shell`函数
- `builtin` => 内建命令，`Shell`内建命令
- `file` => 文件，磁盘文件，外部命令
- `unfound` => 没有找到

### 案例

- `type -t ls` => `alias`
- `type -t cut` => `file`
- `type -t for` => `keyword`
- `type -t pwd` => `builtin`
- `type -a pwd` => 显示包含该命令的所有位置

## date

### 作用

显示或设定系统日期和时间

### 案例

- `date` => 以默认格式显示当前时间和日期
- `date +"%Y%m%d %H:%M:%S"` => 以指定格式显示当前时间和日期
- `date +"current: %D %T %P%thello world"` => 显示时间的同时加入更多信息
- `date -d yesterday +"%Y%m%d"` => 显示昨天的日期<br>同理，也可以显示其它日期：`next-month, last-year, 7 days...`<br>日期加减操作：`"+1 day", "-1 month", "+1 year"`<br>这些设定都需要跟在参数`-d`后
- `date --date "12:34:56"` or `date -s "12:34:56"` => 设置日期与时间<br>不过，系统自带时间校准，如果与互联网时间不一致，会自动更新

## cal

### 作用

显示日历

### 案例

- `cal` or `cal -1` => 显示当前月份日历
- `cal -3` => 显示近期3个月日历
- `cal 5 2024` => 显示指定年月的日历
- `cal -y 2024` or `cal 2024` => 显示指定年份的所有日历
- `cal -j` => 显示自1月1日起到今天的天数

## crontab

### 作用

定时执行任务（重复）

### 案例

- `crontab -e` => 创建、编辑计划任务
- `crontab -l` => 查看当前用户的计划任务
- `crontab -r` => 删除当前用户的计划任务（所有）
- 计划任务实例（在通过`crontab -e`打开后）:
- - `* * * * * /bin/ls` => 每一分钟执行一次`/bin/ls`
  - `3,15 * * * * /usr/bin/pwd` => 每个小时的第3和第15分钟执行`/usr/bin/pwd`
  - `30 0-23/3 * * * echo "Hello"` => 每天的0-23小时内，每隔3小时的第30分钟执行`echo "Hello"`<br>即：`0:30, 3:30, 6:30, ...`执行
  - `0 */2 * * * /etc/init.d/smb restart` => 每两个小时重启一次`smb`
  - `10 1 * * 6,0 /etc/init.d/smb restart` => 每周六周日的一点十分重启一次`smb`
  - `50 5 1,15 * * fsck /home` => 每月1号和15号的5点50分检查`/home`磁盘
  - `0 22 * * 0 ls` => 每周日晚上10点执行`ls`
  - `30 6 */10 * * ls` => 每月的1、11、21、31号的6点30执行`ls`
  - `* * * * * command`依次表示分钟、小时、日期、月份、周，最后接上需要重复执行的命令

## at && atq && atrm

### 作用

定时执行一次任务

### 案例

- `atq` => 查看系统中的等待作业
- `at -d 1` or `atrm 1` => 删除系统中的编号为1的等待作业
- `at 5 pm` => 创建一个作业等到`5:00pm`时执行，此时将进入交互式界面编写作业内容
- - 例如：`echo Hello World`......
  - `ctrl + d`保存
  - `ctrl + c`取消
- `at -f script.sh now` => 立即执行脚本
- `at -f script.sh now+5 min` => 5分钟后执行脚本
- `at -f script.sh 17:00` => 在17:00执行脚本
- `at -f script.sh 11/06/2024` => 在2024年11月6号的当前时间点执行脚本

## time

### 作用

显示命令执行时所消耗的时间

### 时间

- `real` => 挂钟时间，也就是命令开始执行到结束的时间。这个短时间包括其它进程所占用的时间片和进程被阻塞时所花费的时间
- `user` => 进程花费在用户模式中的`CPU`时间，这是唯一真正用于执行进程所花费的时间，其它进程和花费阻塞状态中的时间没有计算在内
- `sys` => 花费在内核模式中的时间，代表在内核中执行系统调用所花费的时间，这也是真正由进程使用的`CPU`时间

### 案例

`time date` => 显示命令`date`的时间统计结果

## watch

### 作用

周期性执行命令

### 案例

- `watch uptime` => 重复执行`uptime`命令（默认每2秒一次）
- `watch -n 1 -d uptime` => 每隔1秒执行一次`uptime`，并高亮显示变化的数据
- `watch -d 'ls -l | grep file'` => 监测当前目录中`file`文件的变化
- `watch -n 1 "df -i; df"` => 监测磁盘`inode`和`block`数据变化情况

## bc

### 作用

数字计算器

### 案例

- `bc` => 进入计算器
- 计算：
- - `+-*/` => 加减乘除
  - `^` => 平方
  - `sqrt` => 平方根
  - `scale` => 设置小数位
  - `obase, ibase` => 进制转换
- `quit` => 退出
- 通过管道计算：
- - `echo "scale=2;(3.141-1.717)/1" | bc` => 设置小数位计算结果<br>**注意：**这里必须小括号再除以一才能生效
  - `echo "obase=10;ibase=2;110101" | bc` => 二进制转十进制 

## ln

### 作用

为文件创建快捷方式

软链接：相当于`Windows`系统中的快捷方式，原始文件被移动或删除后，软链接的文件就无法使用

硬链接：将文件的`inode`属性块进行复制，将原始文件移动或删除后，硬链接文件依旧可以使用

### 案例

- `ln file hfile` => 创建硬链接
- `ln -s file sfile` => 创建软链接

## shutdown && halt && poweroff && reboot

### 作用

关闭/重启服务器

### 案例

- 立即关机：
- - `shutdown -h now`
  - `halt`
  - `halt -f`（强制关机或重启）
  - `poweroff`
- 立即重启
- - `shutdown -r now`
  - `reboot`
  - `reboot -w`（模拟重启过程，将过程写入到日志中）
- `shutdown -h 21:00` => 晚上11点关机
- `shutdown +5 "System will shutdown after 5 minutes"` => 5分钟后关机，并且通知所有人
- `shutdown -c` => 取消所有关机任务