# MOVE共学营基础课程之- VS Code 零基础使用笔记

视频课程地址：https://www.bilibili.com/video/BV1ty4y1S7mC

# VS Code 零基础教程

### 安装
1. 访问 [VS Code 官方网站](https://code.visualstudio.com/)。
2. 下载适用于您操作系统的安装包。
3. 运行安装程序并按照提示完成安装。

### 实践代码
```bash
# 打开VS Code
code .
```

## 更改语言 & 了解菜单内容
### 更改语言
1. 打开VS Code。
2. 按 `Ctrl + ,` 打开设置。
3. 搜索 `locale`。
4. 选择你想要的语言（例如 `zh-CN`）。
5. 重启VS Code使更改生效。

### 菜单内容
- **文件**：新建、打开、保存等文件操作。
- **编辑**：剪切、复制、粘贴等编辑操作。
- **选择**：选择文本的各种方式。
- **查看**：切换不同的视图。
- **终端**：打开或关闭集成终端。
- **帮助**：访问文档和反馈问题。

### 实践代码
```bash
# 打开集成终端
Ctrl + `
```

## 交互式演练场
### 使用交互式演练场
1. 打开VS Code。
2. 按 `Ctrl + Shift + P` 打开命令面板。
3. 输入 `>Interactive Playground` 并选择它。
4. 在交互式演练场中学习基本操作。

### 实践代码
```javascript
// 交互式演练场示例
console.log("Hello, World!");
```

## 基础配置
### 自定义设置
1. 打开VS Code。
2. 按 `Ctrl + ,` 打开设置。
3. 可以通过JSON格式自定义各种设置，例如字体大小、主题等。

### 实践代码
```json
{
    "editor.fontSize": 14,
    "workbench.colorTheme": "Default Dark+"
}
```

## 前端开发效率利器 Emmet
### 使用Emmet
1. 打开HTML文件。
2. 输入Emmet缩写，例如 `div>ul>li*3`。
3. 按 `Tab` 键展开缩写。

### 实践代码
```html
<!-- Emmet 示例 -->
<div>
    <ul>
        <li></li>
        <li></li>
        <li></li>
    </ul>
</div>
```

## 插件 - Live Server
### 安装Live Server插件
1. 打开VS Code。
2. 按 `Ctrl + Shift + X` 打开扩展市场。
3. 搜索 `Live Server` 并安装。
4. 打开一个HTML文件，右键选择 `Open with Live Server`。

### 实践代码
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Server Example</title>
</head>
<body>
    <h1>Hello, World!</h1>
</body>
</html>
```

## 从源代码编译属于自己的VS Code
### 编译VS Code
1. 克隆VS Code源码仓库：
   ```bash
   git clone https://github.com/microsoft/vscode.git
   ```
2. 进入项目目录：
   ```bash
   cd vscode
   ```
3. 安装依赖：
   ```bash
   npm install
   ```
4. 构建项目：
   ```bash
   npm run compile
   ```
5. 启动VS Code：
   ```bash
   ./scripts/code.sh
   ```

### 实践代码
```bash
# 克隆VS Code源码仓库
git clone https://github.com/microsoft/vscode.git

# 进入项目目录
cd vscode

# 安装依赖
npm install

# 构建项目
npm run compile

# 启动VS Code
./scripts/code.sh
```

## 灵活运用代码片段
### 创建代码片段
1. 打开VS Code。
2. 按 `Ctrl + Shift + P` 打开命令面板。
3. 输入 `>Preferences: Configure User Snippets` 并选择它。
4. 选择或创建一个新的代码片段文件。
5. 添加代码片段，例如：
   ```json
   {
       "Print to console": {
           "prefix": "log",
           "body": [
               "console.log('$1');",
               "$2"
           ],
           "description": "Log output to console"
       }
   }
   ```

### 实践代码
```json
{
    "Print to console": {
        "prefix": "log",
        "body": [
            "console.log('$1');",
            "$2"
        ],
        "description": "Log output to console"
    }
}
```

## 多光标功能
### 使用多光标
1. 打开一个文件。
2. 按住 `Alt` 键并点击多个位置，可以添加多个光标。
3. 按 `Ctrl + Alt + ↓` 或 `↑` 可以在当前行下方或上方添加新的光标。
4. 按 `Ctrl + D` 可以选择下一个相同的单词并添加光标。

### 实践代码
```javascript
// 多光标示例
const items = ['apple', 'banana', 'cherry'];
items.forEach(item => console.log(item));
```

## 鼠标操作技巧
### 常用鼠标操作
- **双击**：选择一个词。
- **三击**：选择一行。
- **拖动选择**：选择一段文本。
- **右键**：弹出上下文菜单。
- **滚轮**：滚动代码。
- **中键**：关闭标签页。

### 实践代码
```javascript
// 鼠标操作示例
const message = "Hello, World!";
console.log(message);
```
