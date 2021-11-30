# Git

[TOC]

Git的一些基本使用

## Git

### 1. git 查看修改用户名与密码

- 查看用户名

```git
git config --global user.name
```

- 修改用户名

```git
git config --global user.name "your name"
```

- 查看邮箱地址

```git
git config --global user.email
```

- 修改邮箱地址

```git
git config --global user.email "your email address"
```

### 2. git 本地与远程仓库关联与解除

- 查看远程仓库信息

```git
git remote -v
```

- 建立新仓库

```git
在github中建立一个新的仓库
可以不要README.md文件
```

- 关联

```git
git remote add origin git@github.com:your_name/repository_name.git
```

- 解除关联

```bash
git remote remove origin
```

### 3. GitHub快速更换绑定邮箱

(1)点击头像
(2)setting
(3)Email
(4)Add email address
(5)新邮箱验证，返回github，将新邮箱验证Set Primary.

### 4. git 推送

```git
git push -u origin master
```

### 5. github 如何删除仓库

（1）settings
（2）页面最下方'Delete this repository'

### 6. 查看本地与远程的连接

```bash
ssh -T git@github.com
```

### 7. 在本地配置公钥

```bash
ssh-keygen -t rsa -C email_address
```

### 8. 重命名

- git mv: move or rename a file, a directory.

- description

```bash
git mv <source> <destination>
git mv <source> <destination directory>
```

*暂时还没看懂重命名文件夹是怎么做的。*

### 9. github刷新

在自己电脑本地`push`完文件后，想要在github中看看效果，

*不要直接按F5进行整个网页的刷新*，

点击自己**仓库的名称链接**进行刷新，这样会比较快。

### 10. git基本操作

```bash
# 初始化仓库
git init
# 取消初始化仓库
rm -rf .git/
# 查看仓库状态（哪些文件提交了，哪些文件未提交）
git status
# 添加文件至提交列表
git add filename
## 同时添加多个文件
git add filename1 filename2 (中间以空格区分)
```

### 11. git删除add中的文件（缓存文件）

```bash
git rm --cached file_name
```

### 12. Git每次push都需要输入用户名与密码

首先，如果我们git clone的下载代码的时候是连接的`https://而不是git@git` (ssh)的形
式，当我们操作git pull/push到远程的时候，总是提示我们输入账号和密码才能操作成功
，频繁的输入账号和密码会很麻烦，也特别烦恼。

解决办法

```bash
git bash进入你的项目目录，输入:
git config --global credential.helper store
```

此项会在本地生成一个文本，上边记录你的账号和密码。

然后你使用上述的命令配置好之后，再操作一次git pull，然后它会提示你输入账号密码
，这一次之后就不需要再次输入密码了。

### 发现github上的绿色格子几天没有亮了

原因：之前github的邮箱更换了，但是本地主机的邮箱忘记更换。

使用`git config user.email`查看是否和github上保留的邮箱是否一致，

如果不一致，使用`git config user.email "your_address”`进行本地邮箱的更换。

以上，完毕。

### git status显示中文乱码

解决办法：`git config --global core.quotepath false`

### 重写最后一个commit信息

```bash
git commit --amend
```

### 恢复git rm的文件

First in the bash: `git reset`
And second: `git checkout the_file_deleted`

### 大大减少git clone下载数据量

```bash
git clone --depth=1
```

### .gitignore文件配置

1. 文件作用: 告诉git哪些文件是不需要管理的.
2. 配置语法

    ```text
    /开头表示目录
    *开头通配
    ?单个字符
    !不忽略某个文件或是目录
    ```

3. 需要自己创建.gitignore文件

注意:

```text
最后需要强调的一点是，如果你不慎在创建.gitignore文件之前就push了项目，那么即使你在.gitignore文件中写入新的过滤规则，这些规则也不会起作用，Git仍然会对所有文件进行版本管理。
简单来说，出现这种问题的原因就是Git已经开始管理这些文件了，所以你无法再通过过滤规则过滤它们。因此一定要养成在项目开始就创建.gitignore文件的习惯，否则一旦push，处理起来会非常麻烦。

From: https://www.jianshu.com/p/699ed86028c2
```

### git log

查看提交历史。

简洁的查看: `git log --oneline`

或者使用`git reflog`,这个每一行都有一个编号。

### Git commit 规范

1. 好的提交信息应该是一个完整的句子。
2. 首字母要大写!

### git获取更新到本地仓库

#### 查看远程分支

```bash
git remote -v
```

#### 从远程分支获取最新版本到本地

```bash
git fetch origin master:temp
```

在本地新建一个temp分支，并将远程仓库的master分支的代码下载到本地分支上面

#### 比较temp和本地仓库

```bash
git diff temp
```

#### 更新本地仓库

确认修改之处后就可以更新本地仓库了，使用`git merge temp`即可更新本地仓库。
