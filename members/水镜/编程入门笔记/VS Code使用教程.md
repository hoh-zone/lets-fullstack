# **简介**
本文主要内容：   
1.介绍VS Code的概念    
2.详细演示VS Code对一些编程语言的环境配置：    
- C/C++
- Python
- HTML+CSS+JS

3.介绍一些方便的快捷操作  
VS Code官网：[https://code.visualstudio.com/](https://code.visualstudio.com/)  
(官网的文档中有对该软件使用的全面介绍)

---

# **一.VS Code的概述**

---

Visual Studio Code (VS Code) 是由微软开发的一个免费、开源、跨平台的源代码编辑器，支持Windows、macOS 和 Linux 系统。它以轻量级、速度快、功能强大著称，特别适合现代编程工作流。VS Code 的主要特点包括：

1. **多语言支持**  
VS Code 支持多种编程语言，包括但不限于：JavaScript、Python、C++、Java、Go、HTML/CSS、TypeScript 等。借助扩展，几乎可以支持任何编程语言。
   
2. **丰富的扩展功能**  
VS Code 有一个庞大的扩展市场，用户可以安装各种插件来增强编辑器的功能，例如调试工具、代码片段、代码格式化、版本控制支持等。这些插件使得 VS Code 可以适应各种开发需求。你可以使用这些扩展来定制和优化你的开发环境。

3. **集成的终端**  
VS Code 提供了一个集成终端，允许你直接在编辑器中运行命令行程序，无需切换窗口。这非常适合开发者进行实时编译、运行、调试程序。

4. **调试功能**  
VS Code 提供了强大的调试工具，可以轻松设置断点、监控变量、调试前端和后端应用程序。你可以通过配置文件来调试Node.js、Python、C++等多种语言的项目。

5. **Git 和版本控制**  
VS Code 内置了 Git 支持，可以让你在图形化界面中执行大部分 Git 操作，比如提交、合并分支、查看历史记录等。这对版本管理非常方便，适合与 GitHub 等平台结合使用。

6. **智能代码补全**  
VS Code 采用了 IntelliSense 技术，能够智能地补全代码，提供语法建议、函数提示、自动导入库等功能，极大提高了编码效率。

7. **多平台支持**  
VS Code 可以在 Windows、macOS 和 Linux 上运行，开发者可以在任何操作系统上享受一致的开发体验。此外，它还支持远程开发，通过 SSH 或 Docker 直接在远程服务器上编写、调试代码。

8. **轻量且高度可定制**  
VS Code 虽然功能强大，但仍然保持了轻量的特性。用户可以根据需求定制界面、快捷键、主题等，来创造个性化的开发环境。

9. **社区支持和文档**  
VS Code 拥有一个活跃的开发者社区，用户可以通过论坛、文档、教程、示例代码等方式获取支持和帮助。

**总结**  
VS Code 是一个功能强大且高度可定制的编辑器，适用于从前端开发、后端开发到数据科学等各种编程领域。它凭借简洁的界面和强大的扩展性成为了现代开发者的首选工具之一。

---

# **二.下载**

---

## 1.下载VS Code
网址：[https://code.visualstudio.com/](https://code.visualstudio.com/)
![](/images/vscode-images/vscode.1.png)

---

# **三.配置中文环境**

---

## 1.打开扩展
![](/images/vscode-images/vscode.2.png)

## 2.安装中文包

### 2.1.在搜索栏中搜索Chinese
### 2.2.选择简体中文安装
### 2.3.重启
![](/images/vscode-images/vscode.3.png)

---

# **四.根据所需语言配置环境（C/C++）**

---

**不需要此语言请跳过**  
## 1.安装插件
### 1.1.C/C++ 插件

- **用途**：这是由微软官方提供的插件，主要用于在 VSCode 上开发和调试 C/C++ 代码。它提供了丰富的功能来增强 C/C++ 开发的体验。
- **功能**：
    - 代码自动补全：帮助你快速编写代码，并提示函数、变量和类型。
    - 语法高亮：为 C/C++ 代码提供清晰的语法高亮显示。
    - 调试支持：通过 VSCode 内置的调试功能，可以使用 GDB、LLDB 或 Visual Studio 调试器来调试 C/C++ 程序。
    - IntelliSense：通过提供自动补全、悬停信息和参数提示等功能，提高代码编写的效率。
    - 多平台支持：该插件支持在 Windows、Linux 和 macOS 平台上工作。

![](/images/vscode-images/vscode.4.png)

---

### 1.2.C/C++ Compile Run 插件

- **用途**：该插件简化了在 VSCode 上编译和运行 C/C++ 程序的过程，特别适合需要快速测试代码的开发者。
- **功能**：
    - 一键编译和运行：你只需按一个快捷键（通常是 F6），就可以编译并立即运行代码，而不必手动编写终端命令。
    - 灵活的配置：你可以通过配置文件自定义编译和运行命令。
    - 适合小型项目：这个插件更适合快速测试小型 C/C++ 项目，因为它不提供完整的调试功能。

![](/images/vscode-images/vscode.5.png)

---

### 1.3.Better C++ Syntax 插件

- **用途**：这个插件专注于改进 C++ 代码的语法高亮显示和格式化，提供比默认的 C++ 高亮显示更丰富的特性。
- **功能**：
    - 改进的语法高亮：为 C++ 提供更精确的语法高亮，特别是模板和更复杂的语言特性。
    - 支持现代 C++：该插件支持 C++11、C++14、C++17 等现代 C++ 标准，确保新的语言特性也能得到良好的高亮。
    - 自定义语法高亮：你可以根据自己的需求自定义 C++ 的高亮规则。

![](/images/vscode-images/vscode.6.png)

---

## 2.配置开发者工具集MinGW，获得UCRT

注意：UCRT是为C和C++设计的标准运行时库，通过MSYS2安装ucrt64工具链时，实际上安装了一个基于UCRT的GCC工具链(这个工具链中包括编译器(gcc,c++),链接器，库文件等)
### 2.1.下载MSYS2
网址：[https://code.visualstudio.com/docs/cpp/config-mingw](https://code.visualstudio.com/docs/cpp/config-mingw)  
注：该网站是英文的，可以使用浏览器自带翻译，翻译成中文，后续配置内容在网站下也有讲解
![](/images/vscode-images/vscode.7.png)
### 2.2.安装后复制网站中的命令输入
**pacman -S --needed base-devel mingw-w64-ucrt-x86_64-toolchain**  
注意：安装时碰到Enter a selection (default=all):，回车就行，网站上说的也有
![](/images/vscode-images/vscode.8.png)
### 2.3.复制ucrt64文件中的bin文件地址
在电脑文件中找到ucrt64文件下的bin文件(就在安装MSYS2的文件中)，并复制bin文件的文件地址
![](/images/vscode-images/vscode.9.png)
### 2.4.添加到Windows环境变量的Path路径中
.将ucrt64的bin文件地址到 Windows环境变量的Path路径中
#### 2.4.1.打开系统环境变量界面
在搜索栏中搜索系统环境变量并打开
![](/images/vscode-images/vscode.10.png)
#### 2.4.2. 进入Path变量编辑界面
点击环境变量，在用户/系统变量中，选择Path变量，然后选择编辑
#### 2.4.3. 新建并放入复制的地址
点击新建，将复制的文件地址复制进去，最后点击确定退出
#### 2.4.4.图片演示
![](/images/vscode-images/vscode.11.png)
![](/images/vscode-images/vscode.12.png)
![](/images/vscode-images/vscode.13.png)

---

## 3.编写C/C++程序

### 3.1.创建一个文件
![](/images/vscode-images/vscode.15.png)
### 3.2.通过VScode打开你上面创建的文件
![](/images/vscode-images/vscode.16.png)
### 3.3.创建文本文件，后缀需为.c或.cpp,再在弹出的语言选择中选择c++
![](/images/vscode-images/vscode.17.png)
### 3.4.编写代码并运行，可以在终端看到输出结果
![](/images/vscode-images/vscode.18.png)
### 3.5.设置在控制台中输出结果
#### 3.5.1.打开C/C++ Compile Run的设置
![](/images/vscode-images/vscode.19.png)
#### 3.5.2.下滑勾选选项Run-in-external-terminal
![](/images/vscode-images/vscode.20.png)
#### 3.5.3.配置环境完成
![](/images/vscode-images/vscode.21.png)

---

# **五.根据所需语言配置环境（Python）**

---

**不需要此语言请跳过** 
## 1下载Python解释器
网址：[https://www.python.org/downloads/](https://www.python.org/downloads/)
![](/images/vscode-images/vscode.22.png)
![](/images/vscode-images/vscode.23.png)(下面两个选项要勾上，第一个就是运行Python程序时会调用它，第二个是把它添加到系统路径，让系统可以直接调用它)
## 2.安装插件
### 2.1.python 插件
![](/images/vscode-images/vscode.24.png)
### 2.2.python的主要功能
- **代码智能提示**：提供 Python 代码的自动补全、函数参数提示、变量/函数定义跳转等功能。
- **调试支持**：集成调试器，可以直接在 VS Code 中进行 Python 代码的调试，设置断点、变量监视和调用堆栈查看等。
- **代码检查**：支持代码静态分析工具，如 Pylint 和 Flake8，帮助你发现代码中的潜在错误和格式问题。
- **虚拟环境和 Conda 支持**：可以轻松选择和管理不同的 Python 解释器、虚拟环境或 Conda 环境。
- **Jupyter 支持**：可以在 VS Code 中直接运行 Jupyter Notebooks，进行交互式的 Python 开发，特别适合数据科学工作流。
- **测试集成**：支持常用的测试框架（如 unittest、pytest），便于运行和调试测试用例。
这个插件是 Python 开发者在 VS Code 中工作的基础工具，帮助进行代码编写、调试、测试和管理开发环境。

---

### 2.3.Python Extension Pack 插件
![](/images/vscode-images/vscode.26.png)

### 2.4.Python Extension Pack 的主要功能：
**Python Extension Pack** 是为 Visual Studio Code 的 Python 开发者设计的一组插件包，包含了多个非常有用的扩展，主要包括：
1. **Python** - 提供核心功能，如代码检查（linting）、调试（包括多线程和远程调试）、智能感知（IntelliSense）、代码格式化、重构、单元测试，以及用于数据科学任务的 Jupyter Notebook 支持。
2. **Jinja** - 提供 Jinja 模板语言的语法高亮和代码片段。
3. **Django** - 为 Django Web 开发添加了特定的语法和代码片段。
4. **Visual Studio IntelliCode** - 基于机器学习的 AI 辅助工具，帮助提供智能代码补全和建议。
5. **Python Environment Manager** - 帮助你在 VS Code 中查看和管理 Python 环境及其依赖包。
6. **Python Docstring Generator** - 辅助自动生成 Python 函数和类的文档注释。
7. **Python Indent** - 自动纠正 Python 代码的缩进。
8. **Jupyter** - 提供对 Jupyter Notebook 的支持，适用于数据科学、机器学习和科学计算等任务。

---

## 3.编写Python程序

### 3.1创建一个文件
![](/images/vscode-images/vscode.15.png)
### 3.2.通过VScode打开你上面创建的文件
![](/images/vscode-images/vscode.16.png)
### 3.3.创建文本文件，后缀需为.py,再在弹出的语言选择中选择python
![](/images/vscode-images/vscode.17.png)
### 3.4.编写代码并运行，可以在终端看到输出结果
![](/images/vscode-images/vscode.25.png)

---

# **六.根据所需语言配置环境（HTML+CSS+JS）**

---

**不需要此语言请跳过** 
## 1.安装插件
### 1.2.HTML CSS Support 插件
![](/images/vscode-images/vscode.27.png)
### 1.3.HTML CSS Support的主要功能

- 为 HTML 文件中的元素提供 CSS 类名的自动补全。你在 HTML 文件中编辑时，输入 `class` 属性时，插件会自动从项目中的 CSS 文件中获取可用的类名并建议补全。
- 支持从链接的 CSS 文件中提取类名，还包括嵌入在 HTML 中的 `<style>` 标签内的样式。
- 这有助于提高开发效率，避免拼写错误，并且能更轻松地管理和使用样式表中的 CSS 类。
这个插件非常适合在 HTML 和 CSS 开发中频繁切换的开发者。

---

### 1.4.Live Server 插件
![](/images/vscode-images/vscode.28.png)

### 1.5.Live Server的主要功能
- 启动一个本地开发服务器，让你可以实时预览 HTML、CSS 和 JavaScript 文件的更改。
- 每次保存文件时，浏览器会自动刷新页面，立即反映所做的更改（即所谓的 "热重载" 功能）。
- 支持自定义端口、根目录等配置，适合多种开发场景。
- 提高了开发效率，无需手动刷新浏览器，特别适合前端开发。
对于那些进行网页设计和前端开发的用户来说，这个插件非常实用。

---

### 1.6.Auto Rename Tag 插件
![](/images/vscode-images/vscode.29.png)
### 1.7.Auto Rename Tag的主要功能
- 自动同步重命名 HTML/XML 标签。当你修改或重命名一个标签时，插件会自动更新相应的闭合标签。
- 支持所有 HTML、XML 和相关语言中的标签。
- 减少了手动修改闭合标签的麻烦，提高了开发效率，尤其是对嵌套标签较多的代码片段非常有用。
这个插件对写 HTML 和 XML 时特别有帮助，能有效避免遗漏或错误的闭合标签。

---

## 2.编写HTML程序
### 2.1.创建一个文件
### 2.2.通过VScode打开你上面创建的文件
### 2.3.创建文本文件，后缀需为.html
### 2.4.编写代码，鼠标右键再点击Open with Live Server
![](/images/vscode-images/vscode.30.png)

![](/images/vscode-images/vscode.31.png)

---

# **七.快捷操作**

---

## 1.使用编辑器操场
编辑器操场会提供许多快捷键的使用
![](/images/vscode-images/vscode.32.png)
## 2.Multi-Cursor Editing（多光标编辑） 
注意：DownArrow就是键盘上的向下箭头，其它同理
### 2.1.Box selection
（选择矩形块）  
```
Shift+Alt再拖动鼠标
```
实现选择一个矩形块
![](/images/vscode-images/vscode.33.png)
### 2.2.Add a Cursor
（添加光标）  
```
Crtl+Alt+UpArrow/DownArrow(上/下箭头)
```
将向上/向下额外添加一个光标  
```
Alt再点击鼠标
```
可以在点击位置额外添加一个光标
### 2.3.Creat curosrs on all occurences of a string
（选择光标所在字符串，并在字符串的所有出现处创建光标）  
```
Crtl+Shift+L
```
选中光标所在单词的所有单词，并创建一个光标到单词尾  
注意：截图不显示光标，实际上每个backgroud的末尾都有一个光标，可以对这个单词进行批量操作
![](/images/vscode-images/vscode.34.png)
## 3.Line Actions（行操作）
### 3.1.Copy a line and insert it above or below the current postion
（复制一行到上/下一行）  
```
Shift+Alt+UpArrow/DownArrow(上/下箭头)
```
会将光标所在行向上/下复制一行
### 3.2.Move an entire line or selection of lines up or downloads
（将所在行与上/下行将换位置）  
```
Alt+UpArrow/DownArrow
```
### 3.3.Delete the entire Line
（删除选中或所在行）  
```
Ctrl+Shift+K
```
## 4.Rename Refactoring
（重命名一个类或函数名的所有字符串）
```
F2
```
先选中需要重命名的函数或类的名称，再点击**F2**进行重命名，注意：这对不是类或函数名的字符串不起作用
## 5.Formatting
（格式化代码）
```
Shift+Alt+F
```
将你的代码格式化，注意：这里的格式化不是删除的意思，而是让你的代码更规范，像是是排布很乱的代码整理的意思
## 6.Code Folding
（代码折叠）
```
Ctrl+Shift+[/]
```
将代码折叠/解除折叠，就像这个笔记软件，一个大点下面的小点都可以折叠起来
## 7.撤销
```
Ctrl+Z
```
可以撤销到你的上一步，错删时很好用

---

# **八.命令搜索栏与其它**

---

## 1.使用命令
帮助里编辑器操场的上一个显示所有命令，就可以进入可输入命令搜索栏，也可以直接使用快捷键  
也可直接在搜索栏里输入一个>进入命令搜索栏
```
Ctrl+Shift+P
```
## 2.更改语言
先**Ctrl+Shift+P**进入命令搜索栏，再在搜索栏中搜索语言，点击配置显示语言就能实现中英文切换
![](/images/vscode-images/vscode.35.png)
## 3.更改字体
![](/images/vscode-images/vscode.36.png)
## 4.快捷键参考
![](/images/vscode-images/vscode.37.png)

---

# **九.完结**

---

**根据上述操作，就能正常使用VS Code  
VS Code还能方便的管理Git项目，详情请见介绍Git的文章**
