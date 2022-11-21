---
title: 关于Git 的使用
date: 2022-11-01 13:31:58
updated: {{ updated }}
categories:
- Blog
tags:
- Git
author: shuguang2000
keywords: Git的使用,Git的原理
comments: true
---
- Git 是一个分布式版本控制系统，每个客户端都是一个完整的版本库。
</br>

- Git 本质上是一个**key-value的数据库**加上**默克尔树形成的有向无环图**（DAG）。
</br>

- 关于Git 更多内容，参考[Pro Git book](https://git-scm.com/book/zh/v2) 。
<!-- more -->

------

### Git 简述

- Git 背景
  - Git是创建之初是为了辅助Linux内核使用的。
</br>
- Git 简介
  - Git是一个分布式版本控制软件，主要用于**版本迭代**，每一个客户端都是包含整个版本控制过程中的完整镜像。
</br>
- Linux 基础命令

```linux
   # 基础命令
   1. cd <path>
   2. cd ... <返回上一级目录>
   3. pwd <当前路径>
   4. ls(ll) <列出当前目录所有文件>
   5. touch <filename> <新建文件>
   6. mkdir <folder> <新建文件夹>
   7. rm -f <folder> <删除文件夹>
   9. mv <filename> <folder> <移动文件到文件夹>

   # 扩展命令
   10. reset <初始化终端>
   11. clear <清屏>
   12. history <查看历史命令>
   13. help 
   14. exit
   15. #表示注释

```

------

#### Git 配置

- `git config --local -l`
  - 查看仓库配置 【优先级最高】
</br>
- `git config --global -l`
  - 查看用户配置 【优先级次之】
</br>
- `git config --system -l`
  - 查看系统配置 【优先级最低】
</br>
- `git config -l`
  - 查看所有的配置信息，依次是系统级别、用户级别、仓库级别
</br>
- Git对配置文件使用
  - 配置文件的权重是：仓库 > 全局 > 系统。
  - 配置文件的查找是：系统 > 全局 > 仓库。
</br>
- git config 的配置文件路径
  - 仓库配置
    - 路径：当前路径
  - 用户配置(全局)
    - 路径：`C:\Users\username\gitconfig`
  - 系统配置
    - 路径：`Git安装目录\etc\gitconfig`
</br>
- git config 常用配置
  - 编辑配置文件
    - `git config --local -e` 编辑仓库级别配置文件
    - `git config --global -e` 编辑用户级别配置文件
    - `git config --system -e` 编辑系统级别配置文件
  </br>
  - 配置全局的用户名和邮箱
    - `git config [--global] user.name "[name]"`
    - `git config [--global] user.email "[email address]"`
  </br>
  - 关于配置项的使用(默认都是在local配置中)
    - 增加配置项
      - `git config [--local|--global|--system] --add section.key value`
    - 获取配置项
      - `git config [--local|--global|--system] --get section.key`
    - 删除配置项
      - `git config [--local|--global|--system] --unset section.key`

------

##### Git 工作原理

- Git 工作区域
  - 本地工作区域
    - Workspace：工作区
      - 需要进行版本控制的区域
    - Index/Stage：暂存区
      - 用于临时存放工作区中的改动，只是一个文件。
    - Repository：仓库区
      - 本地仓库，保存提交文件的所有版本信息。其中Head指向最新放入的仓库版本。
  - 中心服务器
    - Remote：远程仓库
      - 托管代码的服务器，主要进行数据版本控制和多人协同开发。
</br>
- Git 的工作流程
  - 创建本地仓库
    - `git init [project-name]`
    - `git clone [url]`
  - 将需要进行版本控制的文件添加到暂存区
    - `git add .`
  - 将暂存区中的文件提交到本地仓库
    - `git commit -m [message]`
  - 将本地仓库的文件提交到远程
    - `git push [remote] [branch]`

- Git 文件状态
  - 已修改（modified）
  - 已暂存（staged）
  - 已提交(committed)

- Git 的key-value的数据库
  - git数据库存储文件时，只关心文件整体内容，不关心单个文件内容是否改变。

------

##### Git 使用

- Git 本地仓库搭建
  - 创建本地仓库
    - `git init` 初始化Git仓库
    - `git add .` 添加所有文件到暂存区
    - `git status [filename]` 查看文件状态
    - `git commit -m "message"` 提交暂存区内容到本地仓库
  - 克隆远程仓库
    - git push 提交本体仓库内容到远程服务器
</br>
- .gitignore文件的使用
  - 注释：`#`用于注释。
  - 通配符：`*`代表任意多个；`？`代表一个字符；`！`表示不被忽略。
  - `folder/`: 该目录下的所有文件，不包括该目录下的子目录。
  - `/folder`: 该目录下面的所有文件，默认文件和目录都忽略。
- .gitkeep文件
  - 使 Git 保留一个空文件夹
</br>
- 创建SSH密钥
  - `ssh-keygen -t rsa -C 'youremail@outlook.com'`
    - 创建的公私钥对默认位于：`C:\Users\username\.ssh`
</br>
- Git 分支
  - 所谓分支其实就是通过

------

##### Git 常用命令

- 来自[常用 Git 命令清单（阮一峰）](https://blog.51cto.com/u_14595972/4940805)

------

##### 关于Git在VScode中的使用

- pass

------

##### 致谢

- pass
