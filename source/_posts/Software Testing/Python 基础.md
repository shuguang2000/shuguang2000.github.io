---
title: Python 基础
date: 2022-11-19 13:31:58
updated: {{ updated }}
categories:
- Software Testing
tags:
- Python
author: shuguang2000
keywords: Python基础
comments: true
---
- 本文主要介绍自动化测试环境搭建、Python相关概念和pip包管理工具。
<!-- more -->

#### 环境搭建

- 安装[Python](https://www.python.org/)
- 更换国内源镜像源
  - `pip install selenium==xx.xx -i http://pypi.douban.com/simple --trusted-host pypi.douban.com`
</br>

- 安装Selenium包
  - 运行命令 `pip install --user selenium`
</br>

- pip国内软件源可供安装的地址：
  - `https://pypi.tuna.tsinghua.edu.cn/simple/`
  - `https://pypi.doubanio.com/simple/`
</br>

- 安装[浏览器驱动](http://www.seleniumhq.org/download/)放于Python安装目录下。
  - [chrome浏览器驱动下载](http://chromedriver.storage.googleapis.com/index.html)

- pip的常用命令
  - `pip freeze` 或`pip list` 列举已安装的包
    - 导出requirements.txt(用于生成记录所有依赖包及其精确的版本号。以便新环境部署。)
  - `pip freeze`  <目录>/requirements.txt
  - `pip install` <目录>/<文件名>
  - `pip intstall -upgrade` 或 `pip install -U` <包名>升级包
  - `pip pip install -U pip` 升级
  - `pip show` <包名-现实指定包版本 
  - `pip show -f` <包名-显示包所在目录
  - `pip search` <搜索关键字>
  - `pip list -o` 查询可升级的包
  - `pip install` <包名--d <目录-或 `pip install -d` <目录--r requirements.txt 下载包而不安装
  - `pip wheel` <包名-打包
  - `pip install` 软件名称 == 很大的数字 查看全部可安装版本
  - `ctrl + c` 打断
</br>

- `Chrome Driver`下载
  - `chromedriver`的版本一定要与Chrome的版本一致，不然就不起作用。
  - 有两个下载地址：
    - `http://chromedriver.storage.googleapis.com/index.html`
    - `https://npm.taobao.org/mirrors/chromedriver`
  - `Firefox Driver` 下载
    - `https://github.com/mozilla/geckodriver/releases`

------

#### Python 基础

- print函数
  - 转换说明符
  - %s  字符串，采用str()
  - %r  采用repr()显示
  - %c  Unicode 码点
  - %d  十进制整数
  - %i  十进制整数
  - %o  八进制整数
  - %x  十六进制整数
  - %e  指数（基底为e）
  - %E  指数（基底为E）
  - %f  浮点数
  - %F  浮点数
  - %g  指数（e）或浮点数
  - %G  指数（e）或浮点数
  - 格式化输出

  ```python
    # 格式化输出
    print("{} {}".format("hello", "world"))
    print("{0} {1}".format("hello", "world"))
    print("{1} {0} {1}".format("hello", "world"))
    print("{:.2f}".format(3.1415926))  # 保留两位小数
  ```

</br>

- 引号与注释
  - 单行注释 #
  - 多行注释 \```注释内容\```
  - 支持三引号（不论单双）

- 引用模块import  
  - 如果确定不会从把不同模块导入同名函数
    - from 模块名称 import -
  - 注意：自定函数名与导入函数同名会覆盖原函数。
  - 理解执行import，Python到底做了那些操作
    - 创建一个`module`（可能包含多个`module`）
    - 把这个`module`插入到`sys.module`中
    - 装载`module`的代码（如果需要，则必须先编译）
    - 创建对象，插入对象，装载要执行的代码，执行对应代码。
  - 装载代码过程：
    - 当前路径（以及从当前目录指定的`sys.path`）
    - Python的PATH
    - Python安装时的默认路径。
    - 执行新的module中对应的代码

  - 补充
    - ./ 代表当前目录
    - ../ 代表上一级目录
    - /是根目录
</br>

- 异常
  - 异常抛出机制
    - 程序运行时发生异常，解释器会查询相应处理语句（称为handler）
    - 如果再当前函数理没有找到就会将异常传递给上层调用函数
    - 如果再最外层（全局“main”）中还是未找到，解释器就会退出，同时打印Traceback，方便用户找到错误产生原因。
    - 所有异常都继承Exception，所以可以使用它来接受所有类型的异常。
    - Python2.5后所有的异常类都继承与基类`BaseException`，Exception同样继承与`BaseException`
</br>

- Python运算符优先级表
![image-20200325204946064](https://cdn.jsdelivr.net/gh/shuguang2000/cdn/images/image-20200325204946064.png)
