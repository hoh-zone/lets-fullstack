# **简介**
本文主要内容：   
1.分别介绍CMD与Powershell的概念  
2.分别列出CMD与Powershell的常用命令  
3.分别演示CMD与Powershell的常见使用  
4.分别举例bat与ps1脚本的一些使用示例  

---

# **一.CMD与Powershell的概述**

---

## 1.CMD

CMD（命令提示符）是**Windows 操作系统**中的一个**命令行界面**，用于执行各种命令行任务。它的作用主要集中在基本的**系统操作、文件管理、网络配置和诊断任务**等，尽管功能比 PowerShell 简单，但在日常使用中仍然非常实用。

### 1. 文件和目录管理

CMD 最基本的功能是操作文件和文件夹。用户可以通过命令创建、删除、复制和移动文件及文件夹，也可以查看当前目录中的文件列表或更改当前工作目录。文件管理操作在维护和组织系统文件时非常常用。

### 2. 系统诊断和维护

CMD 提供了许多系统维护相关的命令，用于检查系统健康状态、修复系统文件错误和获取有关计算机硬件和操作系统的信息。这些命令可以帮助用户排查系统问题，如文件损坏、磁盘错误等，确保计算机稳定运行。

### 3. 网络操作与诊断

通过 CMD，可以执行多种网络操作和测试。用户可以查看计算机的网络配置、测试与其他计算机或服务器的连接、追踪网络路径以及查看当前网络连接的状态。这些网络命令在解决网络连接问题或配置网络设置时非常有用。

### 4. 批处理与自动化

CMD 支持批处理脚本，这使得用户可以自动执行一系列任务。批处理文件可以包含多个命令，按照顺序执行，从而自动化一些重复性的工作任务。批处理文件在系统管理和运维中经常使用，特别是需要定期执行的任务，如备份或清理。

### 5. 进程和服务管理

CMD 提供了管理系统进程和服务的功能。用户可以查看当前正在运行的进程，终止不需要的进程，启动或停止系统服务。管理进程和服务对于监控和维护计算机的正常运行至关重要，特别是在处理性能问题或特定服务故障时。

### 6. 用户和权限管理

CMD 允许用户管理系统账户和权限设置。这包括创建新用户、删除现有用户、更改用户密码以及将用户添加到系统组。这些功能在多用户系统或需要配置权限的环境中非常重要，特别是管理员在管理本地用户时。

### 7. 磁盘和分区管理

CMD 具有一些磁盘管理命令，可以帮助用户查看和管理磁盘上的分区、格式化驱动器或检查磁盘的健康状况。这些命令可以在处理存储设备问题或重新组织磁盘空间时发挥作用。

### 8. 计划任务管理

用户可以通过 CMD 配置计划任务，自动执行某些命令或脚本。这对定期执行的任务（如备份、更新、清理等）非常有帮助，且可以精确控制任务执行的时间和频率。

### 9. 高级系统设置

CMD 提供了某些高级系统设置的访问权限，包括管理启动配置、更新组策略等。系统管理员通常使用这些命令来修改系统行为或执行深度管理任务。

### 10. 调试与故障排查

CMD 还提供了许多用于调试和故障排查的工具。例如，用户可以使用它检查系统的详细状态信息、查看日志，或测试与特定服务器的连接。它是排查问题、修复故障、提高计算机稳定性的重要工具。

CMD 是一个功能丰富的工具，虽然它的界面基于文本，但它可以执行各种任务，尤其适用于系统管理、文件操作、批量任务自动化以及故障排查等场景。在现代 Windows 系统中，虽然 PowerShell 更加功能强大，但 CMD 依然是一个简单易用的工具，适合执行许多日常的系统操作。

### CMD 的局限性：

CMD 虽然功能实用，但与现代工具（如 PowerShell）相比，功能较为基础，缺少编程和高级管理功能。而 PowerShell 不仅能够执行 CMD 的所有功能，还提供了更强大的脚本能力和系统管理功能。  

总结：CMD 是一个简单但功能可靠的工具，适合执行文件操作、网络诊断、批处理任务等基本管理任务，但它在现代自动化需求中已经逐渐被 PowerShell 等功能更强的工具所取代。  

Windows批处理是使用CMD运行的一系列命令，通常以.bat或.cmd扩展名的文件保存

---

## 2.Powershell

PowerShell 是一种基于命令行的任务自动化和配置管理框架，由 Microsoft 开发，专为系统管理员和高级用户设计。它具有以下几个主要功能和作用：

### 1. 命令行接口 (CLI)

PowerShell 允许你使用命令（称为 **cmdlets**）执行各种任务，如文件操作、网络配置、服务管理等。它比传统的 CMD 提供了更强大的功能和更复杂的脚本处理能力。

### 2. 脚本编写和自动化

PowerShell 支持编写脚本文件（通常扩展名为 .ps1），通过这些脚本，你可以自动化复杂的系统管理任务，比如批量创建用户、部署应用、备份数据等。系统管理员可以使用它自动化日常任务，提高工作效率。

### 3. 对象导向

与传统命令行不同，PowerShell 的输出是对象，而不是纯文本。这意味着可以轻松处理、过滤和操作这些数据，进行更精细的管理。例如，你可以获取系统中的进程，然后筛选或终止特定的进程。

### 4. 跨平台支持

虽然 PowerShell 最初是为 Windows 开发的，但现在它已经开源并跨平台支持，可以在 Linux 和 macOS 上运行。这使得它适合管理混合环境的企业或开发者。

### 5. 系统管理和配置

PowerShell 提供了对 Windows 操作系统和应用程序的深入控制，用户可以通过它管理注册表、服务、进程、事件日志、网络配置、文件系统等。管理员也可以使用 PowerShell 执行远程管理。

### 6. 模块扩展和社区支持

PowerShell 支持模块化扩展，你可以安装第三方模块以获得更多功能，像 Azure PowerShell 模块用于管理 Azure 资源。PowerShell 库还提供了大量社区和官方开发的脚本和模块，进一步增强了它的功能。

### 常见用法：

- **启动 PowerShell**：按 Win+X，选择 "Windows PowerShell" 或 "Windows PowerShell (管理员)"。
- **执行命令**：你可以在 PowerShell 中输入类似 Get-Process 来获取当前运行的进程，或用  Get-Help 查询命令的帮助文档。

如果你是开发人员或系统管理员，PowerShell 是非常强大且灵活的工具，适合用于自动化任务和复杂的系统管理。

---

## 3.区别

PowerShell 和 CMD（命令提示符）是 Windows 操作系统中两种命令行接口，但它们在功能、设计和用途上有显著的区别。（不过都使用命令cls清屏）以下是一些主要差异：

### 1. 命令集和功能

- **CMD**：CMD 是 Windows 操作系统的传统命令行界面，它使用一组相对简单的命令（如 dir, copy, del）来执行文件管理和一些基本的系统任务。CMD 的命令集较为有限，适合执行简单的任务。
- **PowerShell**：PowerShell 是一个功能强大的任务自动化工具，提供了更为丰富和复杂的命令集（称为 **cmdlets**）。它可以管理文件系统、注册表、进程、服务、事件日志等，远超 CMD 的功能。

### 2. 基于文本 vs 基于对象

- **CMD**：CMD 的输出都是纯文本。当你运行一个命令时，它会以文本格式输出结果。这意味着进一步处理或解析数据时，需要手动使用字符串操作。
- **PowerShell**：PowerShell 的输出是 **对象**，而不是文本。每个 cmdlet 都输出.NET 对象，可以直接对这些对象进行操作，而不需要将输出转换为文本再解析。这使得数据处理更加简洁和高效。

### 3. 脚本能力

- **CMD**：CMD 支持简单的批处理脚本（以 .bat 或 .cmd 为后缀），这些脚本文件可以自动执行一系列命令。然而，CMD 的脚本功能较为基础，缺少现代编程语言中的结构和灵活性。
- **PowerShell**：PowerShell 提供了强大的脚本编写能力，支持复杂的编程结构，如循环、条件语句、函数和错误处理。PowerShell 脚本文件以 .ps1 作为扩展名，能够编写和自动化非常复杂的任务。

### 4. 跨平台支持

- **CMD**：CMD 是 Windows 专用的命令行界面，只能在 Windows 系统中使用。
- **PowerShell**：PowerShell（从 PowerShell Core 开始）是跨平台的，支持 Windows、Linux 和 macOS。这使得它在管理混合系统环境时非常有用。

### 5. 模块化和扩展性

- **CMD**：CMD 的功能较为固定，没有模块化系统，无法轻松扩展其命令集。
- **PowerShell**：PowerShell 具有模块化体系结构，允许用户加载模块以扩展其功能。用户可以安装官方或社区提供的模块，来支持更多任务，如管理云资源、网络设备等。

### 6. 管理员权限

- **CMD**：虽然 CMD 可以通过“以管理员身份运行”提升权限，但其系统管理功能相对有限。
- **PowerShell**：PowerShell 提供了更深入的系统管理功能，特别是在管理员权限下，可以执行高级任务，如管理注册表、Windows服务、事件日志、进程等。

### 7. 命令语法

- **CMD**：CMD 的命令语法比较简单。例如，列出目录中的文件使用 dir。
- **PowerShell**：PowerShell 的命令语法更像编程语言，通常遵循 动词-名词 格式。例如，列出目录中的文件使用 Get-ChildItem。这种命令格式使命令更加直观和一致。

### 8. 集成 .NET

- **CMD**：CMD 与 .NET 无关，无法直接利用 .NET 框架的功能。
- **PowerShell**：PowerShell 完全基于 .NET 框架，允许你直接使用 .NET 类和方法，这为编写复杂脚本和自动化任务提供了强大支持。

### 9. 远程管理

- **CMD**：CMD 不具备本地化远程管理功能。
- **PowerShell**：PowerShell 具有强大的远程管理能力，支持通过 PowerShell Remoting 连接到远程计算机，执行远程任务，非常适合管理员对大规模服务器或计算机网络进行管理。

### 什么时候使用 CMD 和 PowerShell？

- **CMD**：如果你只是需要执行一些简单的命令，如导航目录、管理文件等，CMD 足够好用，启动速度也较快。
- **PowerShell**：如果你需要自动化复杂的任务，进行系统管理、跨平台开发，或者需要更强大的编程能力，那么 PowerShell 是更好的选择。

总结：

- CMD 适合执行简单的、快速的任务。
- PowerShell 更现代化、功能更强大，适合需要复杂任务自动化和系统管理的场景。

你可以根据任务的复杂度选择最合适的工具！

---

## 4.win+R
Win+R用于打开 “运行”对话框  
在这个**对话框**中，你可以输入**程序名、文件名、文档名或互联网地址**，**快速启动**相应的**应用程序**或打开**文件**  
你可以输入**cmd打开命令提示符**，也可输入**powershell打开终端**
![](/images/CMD_Powershell-images/cmd_powershell.1.png)

---

# **二.CMD使用示例**

---

以我目前使用CMD的经验，主要有三个方面的用法  
关于这些命令和bat中的语法，可以先去看看后面  
下面演示都只用了最基本的命令与语法  
更高级的目前我还没用到  
## 1.查询信息
1.可以用ipconfig查询ip地址
![](/images/CMD_Powershell-images/cmd_powershell.2.png)
2.可以使用ping命令查看是否连接有网络，包括是否是科学环境
![](/images/CMD_Powershell-images/cmd_powershell.3.png)
## 2.使用bat脚本
再次介绍：BAT文件是批处理文件的一种，包含一系列可以在CMD中自动执行的命令，常用于自动化任务  
需求：1.我每次想浏览Jekyll网站时，都需要运行一个命令，以此启动一个本地的开发服务器  
通过运行这个bat文件，就能自动运行其中的命令
![](/images/CMD_Powershell-images/cmd_powershell.4.png)
2.可以写一个py文件的启动器
![](/images/CMD_Powershell-images/cmd_powershell.5.png)
## 3.进行文件间的操作
1.图中演示了我将ipconfig的输出重定向到了ip.txt
![](/images/CMD_Powershell-images/cmd_powershell.6.png)
## 4.核心概念
1.重定向运算
```
>> (是左边出内容追加到右边)
>  (是左边输出内容覆盖到右边)
<  (是右边出内容追加到左边)
<< (记忆：箭头哪边，内容向哪边走)
```
2.管道运算
```
A `|` B (A的输出作为B的输入)
```
3.命令帮助信息查看
```
命令 /?
```
使用此命令后会显示命令的用法，和参数的介绍
![](/images/CMD_Powershell-images/cmd_powershell.7.png)
4.更多的操作我目前并没怎么没有用到，如果有机会用到再更新

---

# **三.CMD命令大全**

---

CMD（命令提示符）有许多命令，用于文件管理、系统诊断、网络操作等。在这里，将根据日常使用的**重要性和频率**对 CMD 命令进行排序和介绍。

## 1. 文件和目录管理命令

这些是最常用的命令，用于操作文件和文件夹。

- **dir**：列出当前目录的文件和子目录。
```
dir
```
- **cd**：改变当前目录，进入指定路径。
```
cd 路径
```
- **copy**：复制文件到指定位置。
```
copy source.txt 路径
```
- **move**：移动文件或重命名文件。
```
move source.txt 路径
```
- **del**：删除一个或多个文件。
```
del file.txt
```
- **mkdir**：创建新目录。
```
mkdir NewFolder
```
- **rmdir**：删除目录。

## 2. 系统诊断和修复命令

这些命令用于检查和修复系统，排查问题。

- **sfc /scannow**：扫描并修复系统文件的完整性。
```
sfc /scannow
```
- **chkdsk**：检查磁盘并修复文件系统错误。
```
chkdsk C: /f
```
- **tasklist**：显示当前运行的所有进程。
```
tasklist
```
- **taskkill**：终止指定进程。
```
taskkill /IM notepad.exe /F
```
- **systeminfo**：显示系统的详细配置信息。
```
systeminfo
```
- **ipconfig**：显示网络接口的配置信息，如 IP 地址、子网掩码等。
```
ipconfig
```
- **ping**：测试与远程服务器的网络连接。
```
ping google.com
```

## 3. 网络命令

这些命令用于诊断网络连接和配置网络设置。

- **netstat**：显示当前的网络连接、端口和协议。
```
netstat -an
```
- **tracert**：显示到目标主机的路由路径。
```
tracert google.com
```
- **nslookup**：查询域名对应的 IP 地址或检查 DNS 解析问题。
```
nslookup google.com
```
- **net use**：映射或断开网络驱动器。
```
net use Z: \\server\sharedfolder
```
- **netsh**：管理网络配置（如 IP 设置、防火墙规则）。

## 4. 批处理命令

这些命令经常在批处理脚本（.bat 文件）中使用，以自动化重复任务。

- **echo**：显示消息或启用/禁用命令回显。
```
echo Hello, World!
```
- **set**：设置或显示环境变量。
```
set PATH
```
- **pause**：在批处理文件中暂停命令执行，等待用户按键。
```
pause
```
- **if**：条件语句，判断是否执行某些命令。
```
if exist file.txt echo File exists
```
- **for**：循环处理文件或命令。
```
for %%f in (*.txt) do echo %%f
```
- **goto**：跳转到脚本中的某个标签，通常和 if 配合使用。
```
goto :start
```

## 5. 用户和权限管理

这些命令用于管理用户账户和权限。

- **net user**：管理用户账户（创建、删除、修改用户）。
```
net user username password /add
```
- **net localgroup**：管理本地用户组。
```
net localgroup administrators username /add
```
- **runas**：以其他用户身份执行命令。
```
runas /user:Administrator cmd
```

## 6. 磁盘管理命令

这些命令用于管理硬盘驱动器和分区。

- **diskpart**：管理磁盘分区（创建、删除、调整大小）。
```
diskpart
```
- **format**：格式化磁盘或分区。
```
format D:
```

## 7. 进程和服务管理

这些命令用于查看、终止进程或管理系统服务。

- **sc**：管理系统服务（启动、停止、查询服务状态）。  

**sc query wuauserv**

- **shutdown**：关闭或重启计算机。  

**shutdown /s /t 0  # 立即关机 shutdown /r /t 0  # 立即重启**

## 8. 时间与计划任务管理

这些命令用于与系统时间、计划任务有关的操作。

- **time**：显示或设置系统时间。  

**time**

- **schtasks**：管理计划任务，自动执行任务。  

**schtasks /create /sc daily /tn "Backup" /tr "backup.bat" /st 23:00**

## 9. 高级管理命令

- **bcdedit**：管理启动配置数据（修改启动选项）。

**bcdedit /set {bootmgr} timeout 30**

- **gpupdate**：更新组策略设置。  

**gpupdate /force**

- **wmic**：Windows Management Instrumentation Command，用于查询和管理操作系统相关信息。  

**wmic process get name**

## 10.总结：

1. **文件和目录管理**：如 dir、cd、copy、del 等，是最基础的操作。
2. **系统诊断和修复**：如 sfc、chkdsk、ipconfig 等，用于维护和修复系统。
3. **网络操作**：如 ping、netstat、tracert，对于网络调试和故障排查非常有用。
4. **批处理和自动化**：如 echo、for、if，用于编写自动化脚本。
5. **用户和权限管理**：如 net user、runas，用于管理账户和权限。

---

# **四.bat文件语法**

---

批处理文件（BAT 文件）的语法基于 Windows 的命令行工具 CMD。BAT 文件用于自动执行一系列命令，通常以 .bat 或 .cmd 为扩展名。编写 BAT 文件时，使用的是 CMD 中的命令及其特定的控制结构来控制脚本的流程。

## 1.基本语法结构

BAT 文件的每一行通常包含一个命令，并且按照自上而下的顺序执行。常用的命令包括文件操作、系统管理、进程控制等。

- **注释：** 使用 REM 或 :: 来注释代码，注释行不会执行。  

**REM This is a comment
::  This is also a comment**

- **显示消息：** 使用 echo 打印消息或控制命令回显。  

**echo Hello, World!**

- **变量：** 使用 set 定义和访问变量。变量名用 % 包围来引用。  

**set myVar=123 echo %myVar%**

- **禁用回显：** 在脚本开头使用 @echo off 来关闭命令回显，使得脚本只输出你想要的内容，而不是每个命令的执行行。  

**@echo off**

## 2.流程控制语法

BAT 文件支持基本的流程控制语法，如条件语句、循环等。

### 条件语句 (if)

- if用于执行条件判断。可以根据文件是否存在、字符串比较或者数值比较来决定代码的执行。

 - 存在判断：  

**if exist file.txt echo File exists**

 - 字符串比较：  

**if "%myVar%"=="123" echo Variable is 123**

 - 数值比较：  

**if %myVar% GEQ 100 echo Value is greater than or equal to 100**

### 循环语句 (for)

- for 循环用于遍历文件、目录或变量集合。

 - 遍历文件：  

**for %%f in (*.txt) do echo %%f**

 - 遍历数字范围：  

**for /L %%i in (1, 1, 10) do echo %%i**

## 3.输入输出

- **用户输入：** 使用 set /p 提示用户输入，并将输入存储到变量中。  

**set /p userInput=Enter your name:  echo Hello, %userInput%**

- **重定向输出：** 使用 >、>> 将命令的输出重定向到文件。

- 将输出重定向到文件并覆盖该文件的内容。  

**echo This is a test > output.txt**

- 将输出附加到文件末尾。  

**echo Another line >> output.txt**


## 4.子程序与跳转

- **标签 (:)** 和 **跳转 (goto)**：可以通过标签创建脚本的不同部分，并使用 goto 跳转到某个标签。  

**goto :start  :start echo This is the start**

- **call 语句：** 用于调用另一个批处理文件或调用当前脚本的子例程。  

**call otherScript.bat**


## 5.错误处理

- **errorlevel**：每个命令执行后会设置一个返回码，称为 errorlevel。可以通过检查 errorlevel 来执行错误处理。

**if %errorlevel% neq 0 echo An error occurred**

## 6.批处理文件常见参数

- **%1 到 %9**：批处理文件可以接收命令行参数，使用 %1 访问第一个参数，%2 访问第二个参数，依次类推。  

**echo First parameter is %1**

- **shift**：用于左移参数，%2 变为 %1，%3 变为 %2。  

**shift**

## 7.批处理文件常用命令

- **pause**：暂停脚本执行，等待用户按任意键继续。  

**pause**

- **exit**：终止批处理文件的执行，并可选择返回错误码。  

**exit**


## 8.高级功能

- **setlocal 和 endlocal**：用于限制变量的作用范围，使得在 setlocal 和 endlocal 之间定义的变量在该范围外无效。

**setlocal set myVar=123 endlocal**

- **环境变量操作**：批处理文件可以访问系统环境变量，如 PATH、TEMP 等，并进行修改或使用。
    

## 9.批处理文件的应用场景

- **自动化任务**：定期执行备份、清理日志文件或其他维护任务。
- **批量操作**：批处理文件可以批量处理大量文件，如重命名、复制或移动。
- **系统配置和设置**：设置系统变量、安装软件或配置网络等。

## 10.总结：

BAT 文件语法虽然简单，但在系统自动化和维护中非常有用。它结合了条件语句、循环、变量操作等功能，可以编写复杂的脚本来处理各种任务。如果需要实现更复杂的功能或与外部工具交互，批处理脚本也可以作为基础，通过调用其他程序实现更强大的自动化解决方案。

---

# **五.Powershell命令大全**

---

PowerShell 是一个功能强大的命令行界面和脚本语言，支持多种命令（cmdlets），这些命令用于系统管理、文件操作、网络管理等。以下是按重要性排序的一些常用 PowerShell 命令及其简要说明：

## 1.基本命令

- **Get-Command**：获取可用的所有命令及其详细信息。
- **Get-Help**：显示有关 PowerShell 命令和语法的帮助信息。
- **Get-Process**：获取当前正在运行的进程列表。
- **Get-Service**：获取当前计算机上所有服务的状态。

## 2.文件和目录管理

- **Get-ChildItem**：列出目录中的文件和子目录（相当于 CMD 中的 dir）。
- **Set-Location**：改变当前工作目录（相当于 CMD 中的 cd）。
- **Copy-Item**：复制文件或目录。
- **Move-Item**：移动文件或目录。
- **Remove-Item**：删除文件或目录。
- **New-Item**：创建新文件或目录。

## 3.系统管理

- **Get-EventLog**：获取系统事件日志。
- **Clear-Host**：清除 PowerShell 窗口中的所有内容。
- **Get-ExecutionPolicy**：查看当前的脚本执行策略。
- **Set-ExecutionPolicy**：设置 PowerShell 脚本的执行策略。

## 4.网络管理

- **Test-Connection**：测试与远程主机的网络连接（相当于 ping 命令）。
- **Get-NetAdapter**：获取网络适配器的详细信息。
- **Get-NetIPAddress**：获取 IP 地址配置。
- **New-NetFirewallRule**：创建新的防火墙规则。

## 5.用户和权限管理

- **Get-LocalUser**：列出本地用户账户。
- **New-LocalUser**：创建新的本地用户账户。
- **Remove-LocalUser**：删除本地用户账户。
- **Add-LocalGroupMember**：将用户添加到本地组中。

## 6.服务和进程管理

- **Start-Service**：启动指定服务。
- **Stop-Service**：停止指定服务。
- **Restart-Service**：重启指定服务。
- **Stop-Process**：终止指定进程。

## 7.脚本和自动化

- **Invoke-Command**：在本地或远程计算机上执行命令或脚本块。
- **Start-Job**：启动后台作业。
- **Get-Job**：获取后台作业的信息。
- **Receive-Job**：接收后台作业的输出。

## 8.对象和管道处理

- **Select-Object**：选择对象的特定属性。
- **Where-Object**：过滤对象集合，返回满足条件的对象。
- **Sort-Object**：对对象集合进行排序。

## 9.注册表操作

- **Get-Item**：获取指定路径的注册表项。
- **Set-Item**：设置注册表项的值。
- **Remove-Item**：删除注册表项或值。

## 10.获取系统信息

- **Get-ComputerInfo**：获取计算机的系统信息。
- **Get-WmiObject**：访问 Windows 管理工具（WMI）以获取系统的详细信息。

## 11.环境变量

- **Get-ChildItem Env:**：列出所有环境变量。
- **Set-Item Env:VariableName**：设置或修改环境变量。

## 12.其他常用命令

- **Write-Host**：向控制台输出信息。
- **Read-Host**：从用户获取输入。
- **Exit**：退出 PowerShell 会话。

## 13.总结

以上列举的是一些重要且常用的 PowerShell 命令，按照其在日常使用中的重要性进行排序。这些命令可以帮助用户完成许多任务，从基础的文件管理到复杂的系统管理和自动化操作。PowerShell 的强大之处在于它的命令组合能力和对象处理能力，用户可以通过管道将一个命令的输出直接传递给另一个命令，从而实现更复杂的操作。

---

# **六.ps1文件语法**

---

PSL 文件通常是指 PowerShell 脚本文件，其扩展名为 .ps1。PowerShell 脚本使用 PowerShell 语言编写，支持丰富的语法和功能。以下是对 PowerShell 脚本（PSL 文件）语法的详细介绍：

## 1.**基本结构**

- **脚本注释**：

 - 单行注释使用井符号  

**# This is a comment**

 - 多行注释使用 <# 和 #>：  

**<# This is a multi-line comment It can span multiple lines #>**

## 2.变量

- **定义变量**：使用 $ 符号定义变量，等号（=）用于赋值。  

**$myVariable = "Hello, World!"**

- **使用变量**：在字符串中使用变量时，可用双引号引用。  

**Write-Host "The message is: $myVariable"**

## 3.数据类型  

**$stringVar = "This is a string" $intVar = 42 $arrayVar = @(1, 2, 3, 4) $hashTable = @{"key1" = "value1"; "key2" = "value2"}**

## 4.流程控制

- **条件语句**：

**if ($condition) {     # Do something } elseif ($otherCondition) {     # Do something else } else {     # Do another thing }**

- **循环语句**:

 - for 循环：  

**for ($i = 0; $i -lt 10; $i++) {     Write-Host $i }**

 - foreach 循环：  

**foreach ($item in $arrayVar) {     Write-Host $item }**

  - while 循环：  

**$counter = 0 while ($counter -lt 5) {     Write-Host $counter     $counter++ }**

## 5.函数

- **定义函数**：使用 function 关键字定义一个函数。  

**function MyFunction {     param ($param1, $param2)     Write-Host "Parameter 1 is $param1"     Write-Host "Parameter 2 is $param2" }  MyFunction "Value1" "Value2"**

## 6.错误处理

- **try、catch 和 finally**：  

**try {     # Code that might throw an exception } catch {     Write-Host "An error occurred: $_" } finally {     # Code that runs regardless of success or failure }**

## 7.模块和导入

- **导入模块**：使用 Import-Module 导入 PowerShell 模块。  

**Import-Module ModuleName**

## 8.输入和输出

- **输出到控制台**  

**Write-Host "This is output to the console"**

- **获取用户输入**  

**$userInput = Read-Host "Enter your name" Write-Host "Hello, $userInput!"**

## 9.管道

- PowerShell支持管道（`|`）将一个命令的输出直接传递给另一个命令。  

**Get-Process `|` Where-Object { $_.CPU -gt 100 }**

## 10.文件操作

- **读取文件**  

**$content = Get-Content "C:\path\to\file.txt"**

- **写入文件**  

**"Hello, World!" `|` Out-File "C:\path\to\output.txt"**

## 11 对象和属性

- PowerShell 的强大之处在于对对象的处理，可以访问对象的属性和方法。  

**$process = Get-Process `|` Where-Object { $_.Name -eq "powershell" } Write-Host "Process ID: $($process.Id)"**

## 12.自动化和计划任务

- **创建计划任务**：  

**$action = New-ScheduledTaskAction -Execute "PowerShell.exe" -Argument "C:\path\to\script.ps1" $trigger = New-ScheduledTaskTrigger -At 7am -Daily Register-ScheduledTask -Action $action -Trigger $trigger -TaskName "MyTask"**

## 13.模块的创建与使用

- **创建模块**：将相关的函数和命令放入一个 .psm1 文件中。
- **使用模块**：导入模块并调用模块中的函数。

## 14.管道和流

- 管道允许多个命令连接在一起，可以有效处理数据流。
- **示例**：  

**Get-Service `|` Where-Object { $_.Status -eq 'Running' }**

## 15.自动完成和参数

- PowerShell 支持命令的自动完成功能，并可以使用参数简化命令的输入。

## 16.总结

PowerShell 脚本（PSL 文件）语法强大且灵活，支持多种编程结构，使其能够用于系统管理、自动化任务、文件处理等多种场景。通过合理使用这些语法结构，用户可以编写高效、可维护的脚本来完成复杂的操作。

---

#  **七.Powershell使用示例**

---

## 1.配置环境

### 1.1.执行策略介绍

执行策略（Execution Policy）是 PowerShell 中的一个安全功能，用于控制脚本和配置文件的运行权限。它通过限制脚本的执行来保护系统不受潜在恶意代码的影响。主要的执行策略有：

1. **Restricted**：默认策略，不允许任何脚本运行。
2. **AllSigned**：只允许运行由受信任的发布者签名的脚本。
3. **RemoteSigned**：本地脚本可以运行，远程脚本必须签名。
4. **Unrestricted**：允许所有脚本运行，但在执行远程脚本时会有警告。
5. **Bypass**：不进行任何检查，允许所有脚本运行。
6. **Undefined**：没有设置策略，PowerShell 会回到默认策略。

可以通过 PowerShell 中的 Get-ExecutionPolicy 命令查看当前策略，通过 Set-ExecutionPolicy 命令更改策略。修改执行策略时需要考虑安全性和系统的需求。

### 1.2.运行命令检查执行策略

我这已经提前更改过了，初始是限制的

**Get-ExecutionPolicy -List**

![](/images/CMD_Powershell-images/cmd_powershell.8.png)

### 1.3.更改执行策略
更改CurrentUser 的策略为RemoteSigned

**Set-ExecutionPolicy RemoteSigned -Scope CurrentUser**


## 2.批量重命名文件名

### 2.1.需求

我需要对一个目录下的所有png图片按照时间顺序进行指定格式的重命名

### 2.2.编写代码

文件后缀是ps1,不要写成psl了，数字1与字母l很像
![](/images/CMD_Powershell-images/cmd_powershell.9.png)

### 2.3.在终端中运行

需处理的文件
![](/images/CMD_Powershell-images/cmd_powershell.10.png)
运行命令
![](/images/CMD_Powershell-images/cmd_powershell.11.png)
完成处理
![](/images/CMD_Powershell-images/cmd_powershell.12.png)

### 2.4.python实现相同操作

![](/images/CMD_Powershell-images/cmd_powershell.13.png)
![](/images/CMD_Powershell-images/cmd_powershell.14.png)

## 3.注意事项

### 1.文件名命名最好不要用中文和空格

在**文件路径**中使用**中文字符和空格**可能导致路径**解析错误**，特别是在某些编程语言和工具中。这可能导致文件**无法找到或命令无法执行**，增加了开发和调试的复杂性。因此，使用英文字符和下划线等替代方式更为稳妥

---

# **八.完结**
 
---

**关于CMD与Powershell，我目前并没有使用到过多的功能，相比于ps1脚本，更多人应该更喜欢py脚本，本文也仅简要介绍ps1与bat脚本，更多的功能请自行探索**

