# **简介**
本文主要内容：  
1.介绍Jekyll的概念  
2.详细演示如何使用Jekyll来搭建静态网站  
3.演示如何通过Github Pages部署  
4.演示如何获得现成的静态网站   
作者实现的静态网站：[verumkey.github.io](https://verumkey.github.io)  
项目仓库：[https://github.com/Verumkey/verumkey.github.io](https://github.com/Verumkey/verumkey.github.io)  
Jekyll官方文档：[https://jekyllrb.com/docs/](https://jekyllrb.com/docs/)  

---

# **一.Jekyll概述**

---

Jekyll 是一个静态网站生成器，专为博客和文档类网站设计，广泛用于 GitHub Pages。它的主要特点是将 Markdown、Liquid 模板和静态文件（如 CSS、JavaScript、图片等）转化为完整的 HTML 静态页面。因为生成的是静态页面，Jekyll 网站速度快、安全性高，且不需要数据库支持。

## Jekyll 的工作原理：

1. **Markdown 文件**：你撰写的内容通常以 Markdown 格式保存，它是一种简单的标记语言，易于编写和阅读。
2. **模板（Layout）和组件（Includes）**：Jekyll 使用 Liquid 模板引擎（由 Shopify 开发），允许你创建可复用的 HTML 模板和组件来组织页面结构，比如头部、脚部等。
3. **静态文件**：除了内容和模板，Jekyll 还会处理所有静态资源，比如 CSS、JS 和图片。
4. **生成 HTML**：运行 Jekyll 时，它会读取这些内容并结合模板生成静态 HTML 文件，最终输出一个可直接部署的网站。

## Jekyll 的特点：

- **易于部署**：你可以将 Jekyll 站点托管在 GitHub Pages 上，GitHub 会自动帮你运行 Jekyll，并生成你的网站。
- **支持 Markdown**：方便编写内容，尤其是对于写作博客或技术文档。
- **无数据库需求**：Jekyll 不需要数据库支持，所有内容都以文件形式存储，速度更快，适合小型或中型网站。
- **插件支持**：Jekyll 允许用户通过插件扩展功能，比如添加搜索、自动标签生成等。

## 基本使用步骤：

1. **安装 Jekyll**：通过 Ruby 安装。命令是 gem install jekyll bundler。
2. **创建新站点**：运行命令 jekyll new my-site 创建一个新项目。
3. **启动开发服务器**：进入站点文件夹后，运行 jekyll serve 启动本地服务器，Jekyll 会自动编译文件并提供本地预览。
4. **配置 _config.yml**：通过配置文件定制站点，比如设置站点标题、描述、URL、主题等/
5. **添加内容**：在 _posts 文件夹中添加新的 Markdown 文件，即可发布新的博客文章或页面。

---

# **二.在Windows上配置Jekyll**

---

## 1.安装Ruby和DevKit
网址：[https://rubyinstaller.org/downloads/](https://rubyinstaller.org/downloads/)
![](/images/Jekyll-images/jekyll.1.png)

---

## 2.安装Bundler和Jekyll
在命令行或终端输入：
```
gem install bundler jekyll
```
![](/images/Jekyll-images/jekyll.2.png)

---

# **三.创建Jekyll网站项目**

---

## 1.创建一个存放项目的文件
![](/images/Jekyll-images/jekyll.3.png)

---

## 2.创建一个Jekyll网站项目
### 2.1.使用cd命令进入你上面创建的文件的目录下
**注意：如果你使用的是cmd,要先切换盘符**
```
D：
cd "D:\Work\My-Website"
```
### 2.2.输入命令：jekyll new 文件名
```
jekyll new my-website
```
### 2.3.进入创建的文件安装项目依赖
```
cd my-website
bundle install
```
### 2.4.运行本地服务器以预览网站
```
bundle exec jekyll serve
```
### 2.5.图片演示
![](/images/Jekyll-images/jekyll.4.png)
![](/images/Jekyll-images/jekyll.5.png)
**这就是一个静态网站**
![](/images/Jekyll-images/jekyll.6.png)
### 2.5.编辑脚本快速打开
每次浏览Jekyll网站时，都需要**重新运行**budle exec jekyll serve命令，以此启动一个本地的**开发服务器**，使你能够在浏览器中访问你的**网站**
```
D:
cd "D:\Work\My-Website\my-website"
bundle exec jekyll serve
```
![](/images/Jekyll-images/jekyll.7.png)

---

# **四.在GitHub上配置静态网站**

---

## 1.创建仓库
![](/images/Jekyll-images/jekyll.8.png)
**GitHub 对静态网页托管的特殊规则决定了你的个人或组织站点的仓库名必须为**
```
用户名.github.io
```
![](/images/Jekyll-images/jekyll.9.png)
### 规定由来
GitHub 对静态网页托管的特殊规则决定了你的个人或组织站点的仓库名必须为 用户名.github.io。这是因为 GitHub Pages 在为个人或组织提供顶级域名托管时，需要使用固定的命名约定。具体原因如下：

#### 1. **唯一识别的顶级域名**：

个人或组织级的 GitHub Pages 网站会使用特定的顶级域名，形式为 https://用户名.github.io。GitHub 通过仓库名匹配该域名来提供唯一的托管地址。

- 例如，如果你的 GitHub 用户名是 exampleuser，那么 GitHub Pages 会自动把 exampleuser.github.io 解析为你 exampleuser.github.io 仓库中的内容。这个仓库名直接与该域名绑定，便于 GitHub 自动识别和生成网站。

#### 2. **自动部署机制**：

GitHub Pages 自动识别带有 .github.io 后缀的仓库名，并将其视为用户的顶级个人或组织站点。当你提交代码到这个仓库时，GitHub Pages 的服务会立即自动触发站点的构建和部署过程。

如果你的仓库名是其他的，比如 my-website，虽然它也可以用来生成 GitHub Pages 网站，但它只能通过二级域名访问，例如 https://用户名.github.io/my-website/，而不是直接的 用户名.github.io。

#### 3. **区别于项目页面**：

GitHub Pages 支持两种类型的站点：

- **用户/组织页面**：这种站点与 GitHub 用户名直接相关，域名是 用户名.github.io，并且仓库名必须为 用户名.github.io。
- **项目页面**：你可以为 GitHub 中的任何项目创建页面，域名格式为 https://用户名.github.io/项目名。项目页面的仓库名没有强制要求。

通过强制 用户名.github.io 这样的仓库命名规则，GitHub Pages 可以清楚区分个人/组织站点与项目站点，并将它们映射到不同的 URL 上。

因此，要求个人或组织网站的仓库名必须是 用户名.github.io，是为了确保每个用户或组织都有一个唯一且固定的顶级域名来展示其内容，并简化自动部署和解析流程。

---

## 2.配置Jekyll
### 2.1.启用GitHub Action
![](/images/Jekyll-images/jekyll.10.png)
### 2.2.GitHub Action介绍

GitHub Actions 是 GitHub 提供的一项持续集成（CI）和持续交付（CD）服务，允许你在 GitHub 仓库中自动执行各种任务和工作流。它让你能够编写、共享和执行自动化流程，以便在代码提交时执行测试、构建、部署等操作。

#### 核心功能：

1. **自动化工作流**：GitHub Actions 允许你定义一系列自动化任务（称为 "工作流"），这些工作流可以在特定事件（如代码推送、Pull Request、Issue 创建等）发生时触发。
    
2. **持续集成和持续交付**：它可以用来自动化测试、构建和发布代码。例如，每当你推送代码到 GitHub 时，GitHub Actions 可以自动运行单元测试、构建项目，甚至将应用部署到服务器上。
    
3. **灵活性与可扩展性**：GitHub Actions 允许你根据自己的需求，灵活地定义自定义工作流。工作流是通过 YAML 文件定义的，存储在仓库的 .github/workflows/ 目录中。你可以使用 GitHub 自带的动作（Actions）或创建自定义的动作。
    

#### GitHub Actions 的基本概念：

1. **工作流（Workflow）**：
    
    - 工作流是由一系列自动化任务组成的。它们是 GitHub Actions 的核心，用来定义你想自动化的过程。工作流文件使用 YAML 语法编写，放置在 .github/workflows/ 目录下。
    - 每个工作流可以根据事件（如代码提交、Pull Request 等）被触发。
2. **事件（Event）**：
    
    - 事件是触发工作流的特定动作，比如代码的 push、pull_request，创建 Issue，或者手动触发。
    - 例如，当你推送代码时，可以触发一个测试工作流，确保新代码不会破坏现有功能。
3. **任务（Job）**：
    
    - 工作流由一个或多个任务组成。每个任务可以在不同的虚拟机环境（例如 Ubuntu、macOS 或 Windows）上运行，并且任务可以并行或按顺序执行。
4. **步骤（Step）**：
    
    - 每个任务由多个步骤组成。步骤是在运行环境中执行的单个命令或操作。可以使用现有的 Actions 或者在步骤中编写自定义的 Shell 脚本。
5. **动作（Action）**：
    
    - 动作是 GitHub Actions 中的可复用组件，你可以在步骤中调用它们。GitHub 提供了很多官方的 Actions（如 actions/checkout 用于检出代码），并且社区中也有许多开源的 Actions 可以使用。
    - 你也可以编写自己的动作，来实现自定义需求。

#### GitHub Actions 的用途：

1. **自动化测试**：每当代码变更时自动运行测试，确保代码的质量。
2. **持续集成**：合并代码时自动构建和测试项目，避免引入错误。
3. **自动部署**：在代码推送到某个分支时，自动将项目部署到服务器或云端。
4. **代码审查**：自动检查代码格式、代码覆盖率等问题，帮助维护代码质量。
5. **发布管理**：自动生成版本、打包应用，甚至发布到包管理平台（如 npm、Docker 等）。

使用 GitHub Actions 对于 Jekyll 项目的帮助主要体现在自动化、灵活性和自定义能力方面。以下是一些具体的优点和场景，说明 GitHub Actions 如何提升你的 Jekyll 项目体验：

#### 1. **自动化构建和部署**：

- **自动化构建**：通过 GitHub Actions，你可以设置在每次提交代码时自动构建 Jekyll 网站。这样可以确保每次更新后网站的最新版本都会被生成并可用。
- **定期部署**：可以配置定期触发的工作流，自动生成和部署 Jekyll 网站，无需手动操作。

#### 2. **自定义构建过程**：

- **使用特定版本的 Ruby 和 Jekyll**：可以在工作流中指定使用的 Ruby 和 Jekyll 版本，确保在构建过程中的一致性，避免因环境差异导致的问题。
- **预处理和后处理步骤**：在构建前后执行特定的命令，比如优化图片、清理文件、运行自定义脚本等，以确保生成的站点符合你的需求。

#### 3. **集成其他工具**：

- **测试和验证**：可以在构建过程中添加自动化测试，确保 Jekyll 生成的内容符合特定标准，比如 Markdown 语法、链接有效性等。
- **部署到其他平台**：除了 GitHub Pages，你还可以通过 GitHub Actions 将生成的 Jekyll 网站部署到其他平台（如 Netlify、AWS S3、Vercel 等），增强灵活性。

#### 4. **使用自定义插件**：

- **支持更多 Jekyll 插件**：GitHub Pages 默认只支持一部分 Jekyll 插件。如果你使用了自定义或不在默认列表中的插件，GitHub Actions 允许你在自己的工作流中设置环境，支持这些插件的使用。

#### 5. **持续集成和持续交付（CI/CD）**：

- **实现 CI/CD 流程**：通过 GitHub Actions，可以实现完整的 CI/CD 流程，在代码更新时自动进行构建、测试和部署。这使得团队协作时更容易保证代码的质量。

#### 6. **简化复杂的部署需求**：

- **配置和管理更复杂的部署需求**：如果你的项目需要处理多个分支、子模块或复杂的文件结构，GitHub Actions 可以提供更强大的控制能力，帮助你管理这些需求。

### 2.3.安装Jekyll依赖
![](/images/Jekyll-images/jekyll.11.png)
### 2.4.Jekyll依赖作用
### 1. **自动构建 Jekyll 网站**：

- 选择这个选项后，GitHub Actions 会自动帮你构建 Jekyll 网站，而不需要你手动运行构建命令。你只需要提交内容更新（比如新的 Markdown 文件），GitHub Actions 就会自动生成静态网页。

### 2. **预安装 GitHub Pages 依赖**：

- 这个选项会确保 GitHub Pages 构建过程中所需的 Jekyll 依赖（例如 github-pages Gem 和其他插件）已经预先安装好。这样你就不需要自己去担心依赖的安装和配置问题。

### 3. **简化部署流程**：

- 通过使用 GitHub Actions，整个构建和发布的流程变得自动化且透明。每次你向仓库提交代码或文章时，GitHub Actions 会自动运行，安装依赖、生成 HTML 文件，并将其部署到你的 GitHub Pages 网站。

### 4. **确保版本一致性**：

- 当你选择这个选项时，GitHub Pages 使用的 Jekyll 及其插件的版本会和你在本地或其他地方使用的保持一致。这避免了因为版本差异带来的潜在问题，保证你的 Jekyll 网站能够正常生成。

#### **总结**：

- 选择这个选项意味着每次你更新仓库内容时，GitHub Actions 会自动构建你的 Jekyll 网站，并确保所需的依赖已经预先安装好，从而简化了整个网站的生成和部署过程。如果你不选择这个，依然可以用手动配置的方式，但使用 GitHub Actions 自动化这一过程会更加方便。

**直接提交即可**
![](/images/Jekyll-images/jekyll.12.png)
### 2.5.查看网站
**直接在浏览器中输入你的仓库名即可**
```
用户名.github.io
```
![](/images/Jekyll-images/jekyll.13.png)
当然现在什么都没有
![](/images/Jekyll-images/jekyll.14.png)

---

## 3.将Jekyll项目push到仓库
### 3.1.打开上传
![](/images/Jekyll-images/jekyll.15.png)
### 3.2.复制粘贴
打开你创建的Jekyll项目，**将所有文件全选拖动复制进去**
![](/images/Jekyll-images/jekyll.16.png)
### 3.3.提交
![](/images/Jekyll-images/jekyll.17.png)
### 3.5.查看网站
等待Action自动部署完成，然后点击进去
![](/images/Jekyll-images/jekyll.18.png)
成功部署后，点击链接，就是你的静态网站网址
![](/images/Jekyll-images/jekyll.19.png)
**静态网站成功搭建**
![](/images/Jekyll-images/jekyll.20.png)

---

# **五.修改Jekyll项目**

---

**介绍：这里演示使用VS Code管理我们的项目**
## 1.将远程仓库克隆到本地
打开用来保存项目的文件夹，然后克隆远程仓库
其实不用初始化，直接克隆就行了
![](/images/Jekyll-images/jekyll.21.png)

---

## 2.进入克隆的目录下修改文件
示例：我对index.markdown做出了更改
![](/images/Jekyll-images/jekyll.22.png)

---

## 3.本地运行
本地修改一些文件运行后会根据规则生成一些文件，而在GitHub仓库里修改不会显示
![](/images/Jekyll-images/jekyll.23.png)
![](/images/Jekyll-images/jekyll.24.png)

---

## 4.push到远程仓库
### 4.1.提交更改
**注意：要打开克隆的这个目录，原来的目录**
![](/images/Jekyll-images/jekyll.25.png)
### 4.2.推送
![](/images/Jekyll-images/jekyll.26.png)
可以在仓库中看到正在push
![](/images/Jekyll-images/jekyll.27.png)
### 4.3.查看网站
**可以看出，我们本地打开后是一个样，原封不动push上去竟然还有些差别  
这是为什么？~~我也不知道~~   
我们添加一些文件代替默认的配置，就不会出现这种情况了**
![](/images/Jekyll-images/jekyll.28.png)

---

# **六.Jekyll 项目文件结构及作用**

---

## 1.主要文件

1. **_config.yml**
    
    - 这是 Jekyll 项目的配置文件，定义站点的基本信息和行为，例如站点标题、作者、URL、插件、主题等。
    - 常见配置项：
        - title: 网站的名称
        - author: 作者名称
        - baseurl: 网站的基本 URL（如果不在根目录下托管）
        - permalink: 定义文章 URL 的格式
        - theme: 使用的 Jekyll 主题
        - markdown: 指定 Markdown 解析器（通常是 kramdown）

2. **index.html**
    
    - 这是网站的主页文件，通常是一个静态 HTML 文件或包含 Jekyll 模板标记的文件。
    - 它会根据 _config.yml 中的配置渲染成主页。

3. **_posts/**
    
    - 存放所有博客文章的目录，所有文章都以 .md 或 .html 格式编写。
    - 文章文件命名格式：YYYY-MM-DD-title.md（年-月-日-文章标题），这个命名方式用于生成文章的 URL 和时间归档。
    - 每篇文章都需要设置 **Front Matter**（前置信息），用于指定元数据。

4. **_layouts/**
    
    - 存放网站布局文件的目录，Jekyll 用这些布局文件来包裹内容页面。
    - 常见的布局文件：
        - default.html: 网站的默认布局
        - post.html: 单篇文章的布局
        - page.html: 普通页面的布局

5. **_includes/**
    
    - 存放可重用的部分或片段的目录，这些片段可以在其他模板文件中通过(有些问题，无法打出)引用
 
    - 常见的包括导航栏、页脚、头部、或其他重复的 HTML 片段。

6. **_sass/**
    
    - 存放 SASS（CSS 预处理器）文件的目录，用于自定义样式。
    - 这些文件通常通过主样式文件导入，并编译成单个 CSS 文件。

7. **_site/**
    
    - Jekyll 将项目编译生成的静态网站文件都会存储在这个目录中，生成的 HTML 文件可以直接部署到服务器上。
    - 注意：该文件夹在生成时自动创建，不需要手动修改。

8. **assets/**
    
    - 存放项目的静态资源文件，比如图片、CSS、JavaScript 等。
    - 通常开发者会把自定义的样式或脚本放在这个目录中。

9. **Gemfile**
    
    - 用于 Ruby 环境的依赖管理，包含 Jekyll 和其他插件的安装信息。
    - bundle install 命令会依据该文件安装必要的依赖。

10. **pages/**（可选）
    
    - 通常用于存放自定义的页面，比如关于页面、联系页面等。
    - 这些页面的布局可以与博客文章不同。

---

## 2.发文章的规则

1. **文章文件命名**：
    
    - 格式为 YYYY-MM-DD-title.md 或 YYYY-MM-DD-title.html，其中 YYYY-MM-DD 是发布日期，title 是文章的简短描述，通常以短横线 - 分隔单词。
    - 例如：2024-10-19-my-first-post.md。

2. **Front Matter（前置信息）**：
    
    - 文章必须在文件的顶部包含 Front Matter，这是用 YAML 格式定义的元数据，用三条短横线包裹。

    - 常用字段：
        - layout: 指定使用哪个布局文件（通常是 post）
        - title: 文章标题
        - date: 文章发布日期
        - categories: 文章分类，可以用于按分类归档
        - tags: 文章标签，用于更细的分类或标签云展示
  
3. **使用 Markdown 或 HTML 编写**：
    
    - 文章主体可以使用 Markdown（通常是 .md 文件）编写，Jekyll 会自动将其转换为 HTML。
    - 也可以直接使用 .html 文件，编写自定义的 HTML 内容。

4. **URL 生成规则**：
    
    - 根据文件名的日期和 _config.yml 中的 permalink 配置，Jekyll 会自动生成每篇文章的 URL。
    - 默认的 URL 规则通常是：/year/month/day/title/。

5. **Drafts（草稿）**：
    
    - 如果文章存放在 _drafts/ 目录下，并没有指定发布日期，Jekyll 默认不会发布这些草稿文章。
    - 如果要预览草稿，可以使用 jekyll serve --drafts 命令运行。

6. **发布文章时的注意事项**：
    
    - 确保 Front Matter 的日期是当前或过去的日期，否则 Jekyll 不会将其作为已发布的文章显示。
    - 若设置了 future: true 配置项，Jekyll 可以显示未来的文章（即发布日期在未来）。

---

## 3,总结

Jekyll 的文件结构和规则简单而清晰，每个目录和文件都各司其职。通过合理使用 Front Matter 和布局文件，你可以灵活地创建和管理博客文章，同时根据需要自定义网站的外观和功能。

---

# **七.Markdown基本语法**

---

在Jekyll中，提交在_post中特定格式的markdown文件会自动转换问html文件  
所以需要熟悉它的用法，用来写文章  
Markdown 是一种轻量级的标记语言，常用于格式化文本。它的语法简单易懂，适合用于写作和排  版。以下是 Markdown 常用语法的总结：

## 1. 标题

使用 # 来表示标题。# 的数量决定了标题的级别（1-6级）。

**# 一级标题 ## 二级标题 ### 三级标题 #### 四级标题 ##### 五级标题 ###### 六级标题**

## 2. 段落和换行

段落通过一个或多个空行分隔。要在段落中插入换行，可以在行尾添加两个空格，然后按 Enter。

## 3. 强调

- **加粗**：使用 ** 或 __ 包围文本。
- _斜体_：使用 * 或 _ 包围文本。
- ~~删除线~~：使用 ~~ 包围文本。

**加粗文本**   *斜体文本*   ~~删除线文本~~

## 4. 列表

- **无序列表**：使用 *、+ 或 - 开始每个列表项。
- **有序列表**：使用数字和点号（如 1.、2.）表示。

无序列表： 
* 项目一 * 项目二   * 子项目一   * 子项目二  
* 有序列表： 1. 第一项 2. 第二项    1. 子项一    2. 子项二

## 5. 链接

使用 [链接文本](URL) 创建链接。
```
[OpenAI](https://www.openai.com)
```
[OpenAI](https://www.openai.com)
## 6. 图片
```
![示例图片](https://example.com/image.jpg)
```
## 7. 引用

使用 > 来创建引用。

> 这是一段引用文本。

## 8. 代码

- **行内代码**：使用反引号    包围代码。
- **代码块**：使用三个反引号 包围多行代码，可以指定语言。
 
```
这是一个代码块。
```
## 9. 水平线

使用三个或更多的 *、- 或 _ 创建水平线。
```
---
```
---
## 10. 表格

使用 | 分隔列，并使用 - 创建表头。
```
| 列1 | 列2 | 列3 | 
|-----|-----|-----| 
| 数据1 | 数据2 | 数据3 | 
| 数据4 | 数据5 | 数据6 |
```
## 11. 任务列表
使用 - [ ] 创建任务列表项。
```
- [ ] 待办事项1 
- [x] 已完成事项
```

---

# 八.fork别人的静态网站仓库

---

上文都是介绍怎么自己做静态网站，可能要花费不少时间精力  
我们可以fork别人的项目，做出更改
## 1.找到一个合适的静态网站仓库并fork
仓库名是用户名+.github.io的都是  
这里我以自己的仓库为例：[https://github.com/Verumkey/verumkey.github.io](https://github.com/Verumkey/verumkey.github.io)
![](/images/Jekyll-images/jekyll.29.png)
仓库名必须是：**用户名.github.io**
![](/images/Jekyll-images/jekyll.30.png)
## 2.启用GitHub Action
![](/images/Jekyll-images/jekyll.31.png)
## 3.安装Jekyll站点
![](/images/Jekyll-images/jekyll.32.png)
直接提交
![](/images/Jekyll-images/jekyll.33.png)
## 4.做出修改并保存
## 5.查看网站
我这里仅改了下标题
![](/images/Jekyll-images/jekyll.34.png)
## 6.自定义域名
1.在你的域名的域名商那里添加**五条DNS记录**  
**1个CNAME记录**，**主机记录为www**，**记录值为你的仓库名**  
(我这里就是verumkey.github.io)  
**4个A记录**，**主机记录选@**  
**记录值填写GitHub的ip地址  
一.185.199.109.153  
二.185.199.111.153  
三.185.199.110.153  
四.	185.199.108.153  
解析请求来源和TTL默认即可**
![](/images/Jekyll-images/jekyll.36.png)
![](/images/Jekyll-images/jekyll.35.png)

2.然后去你的**仓库的Settings**的**Pages**里找到**Custon Domain**  
3.设置你刚才添加了DNS记录的域名的**主域名**  
4.等待验证成功
![](/images/Jekyll-images/jekyll.37.png)

---

# **九.完结**

---

**就我目前的理解：  
0.演示中只生成了最基础的Jekyll文件，像丰富网站内容的话，还有一些文件需要添加  
1.index.markdown是默认的页面，当你添加了一个index.html作为主页后，记得删除  index.markdown，否则还会显示原来的，因为它的优先级较高  
2.可以添加一个_layouts文件和_includes文件，再进行一些配置来添加页眉页脚  
3.chatgpt是个好工具，我对Jekyll的了解很大一部分缘于它  
4.关于具体怎么修改Jekyll项目，我也不是很清楚,~~所以我做的静态网站那么简陋~~  
可以去看看官方文档，或找找其它教学  
5.以后有经验了，我再回来** 
- [ ] 更新怎么丰富网站内容
