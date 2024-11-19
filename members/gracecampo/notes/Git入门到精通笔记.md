# MOVE共建营之Git入门到精通笔记
教程视频地址：https://www.bilibili.com/video/BV1vy4y1s7k6


## Git概述
### 版本控制
- **版本控制**：记录文件或项目的历史变更，方便回滚和管理。
- **分布式版本控制**：每个开发者都有完整的仓库副本，支持离线工作。
- **集中式版本控制**：所有版本数据集中存放在一个服务器中，需要联网才能访问。

### 发展历史
- Git由Linus Torvalds于2005年创建，用于Linux内核开发。
- Git是一个开源的分布式版本控制系统，广泛应用于软件开发领域。

### 工作机制
- **本地仓库**：存储在本地计算机上的完整版本库。
- **远程仓库**：存储在网络服务器上的版本库，可以是GitHub、Gitee码云或GitLab等。
- **提交**：将更改保存到本地仓库。
- **推送**：将本地仓库的更改推送到远程仓库。
- **拉取**：从远程仓库获取最新的更改并合并到本地仓库。

### 代码托管中心
- **GitHub**：全球最大的代码托管平台。
- **Gitee码云**：国内知名的代码托管平台。
- **GitLab**：提供私有化部署的代码托管平台。

## 安装和客户端使用
### 安装Git
1. 访问 [Git官网](https://git-scm.com/)。
2. 下载适用于您操作系统的安装包。
3. 运行安装程序并按照提示完成安装。

### 设置用户签名
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### 初始化本地库
```bash
mkdir myproject
cd myproject
git init
```

### 查看本地库状态
```bash
git status
```

### 添加暂存区
```bash
git add filename
```

### 提交本地库
```bash
git commit -m "Initial commit"
```

### 修改文件
```bash
# 修改文件内容后
git add filename
git commit -m "Update filename"
```

### 版本穿梭
```bash
# 查看提交历史
git log

# 回退到某个提交
git checkout <commit-hash>

# 回退到最新版本
git checkout master
```

## 分支管理
### 概述和优点
- **分支**：独立的工作线，可以并行开发不同的功能。
- **优点**：隔离开发环境，避免冲突，便于管理和合并。

### 查看&创建&切换分支
```bash
# 查看所有分支
git branch

# 创建新分支
git branch newbranch

# 切换到新分支
git checkout newbranch

# 创建并切换到新分支
git checkout -b newbranch
```

### 合并分支
#### 正常合并
```bash
# 切换到主分支
git checkout master

# 合并新分支
git merge newbranch
```

#### 冲突合并
```bash
# 解决冲突后
git add conflicted-file
git commit -m "Resolve conflict"
```

## 团队协作
### GitHub
#### 创建远程库&创建别名
```bash
# 创建远程库
# 在GitHub上创建一个新的仓库

# 添加远程库别名
git remote add origin https://github.com/username/repo.git
```

#### 推送本地库到远程库
```bash
git push -u origin master
```

#### 拉取远程库到本地库
```bash
git pull origin master
```

#### 克隆远程库到本地
```bash
git clone https://github.com/username/repo.git
```

#### 团队内协作
- **推送和拉取**：确保团队成员之间的代码同步。
- **分支管理**：使用分支进行并行开发，定期合并。

### Gitee码云
#### 账号注册登录&创建远程库
- 在Gitee码云网站上注册账号并创建新的仓库。

#### IDEA集成Gitee码云
- 在IDEA中配置Gitee码云的SSH密钥。
- 使用IDEA的VCS功能克隆和管理仓库。

### GitLab
#### 简介和安装环境准备
- GitLab可以在本地服务器上私有化部署。
- 安装Docker并运行GitLab容器。

#### 安装&初始化服务&启动服务
```bash
# 使用Docker安装GitLab
docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --name gitlab \
  --restart always \
  --volume /srv/gitlab/config:/etc/gitlab \
  --volume /srv/gitlab/logs:/var/log/gitlab \
  --volume /srv/gitlab/data:/var/opt/gitlab \
  gitlab/gitlab-ce:latest
```

#### 登录GitLab并创建远程库
- 在浏览器中访问 `http://<your-server-ip>` 并登录GitLab。
- 创建新的项目仓库。

#### IDEA集成GitLab
- 在IDEA中配置GitLab的SSH密钥。
- 使用IDEA的VCS功能克隆和管理仓库。

## IDEA集成Git
### 环境准备
- 安装IntelliJ IDEA。
- 配置Git路径。

### 初始化&添加&提交
```bash
# 初始化仓库
git init

# 添加文件
git add filename

# 提交更改
git commit -m "Initial commit"
```

### 切换版本
```bash
# 查看提交历史
git log

# 回退到某个提交
git checkout <commit-hash>
```

### 创建分支&切换分支
```bash
# 创建新分支
git branch newbranch

# 切换到新分支
git checkout newbranch
```

### 合并分支
#### 正常合并
```bash
# 切换到主分支
git checkout master

# 合并新分支
git merge newbranch
```

#### 冲突合并
```bash
# 解决冲突后
git add conflicted-file
git commit -m "Resolve conflict"
```

### 设置GitHub账号
- 在GitHub上创建个人账户。
- 配置SSH密钥以便无密码访问。

### 分享项目到GitHub
- 在IDEA中右键点击项目，选择 `Share Project on GitHub`。
- 按照向导完成分享过程。

### 推送代码到远程库
```bash
git push -u origin master
```

### 拉取远程库代码合并本地库
```bash
git pull origin master
```

### 克隆代码到本地
```bash
git clone https://github.com/username/repo.git
```
