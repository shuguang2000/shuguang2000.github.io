---
title: Markdown使用教程
date: 2022-09-29 17:32:58
updated: {{ updated }}
categories:
- Blog
tags:
- Markdown
author: shuguang2000
keywords: Markdown,Markdown语法
comments: true
---
- 关于Markdown语法的使用的梳理，方便总结和回顾使用。
</br>
- 也可以自行通过[Markdown官网](https://markdown.com.cn/)来学习。
<!--more-->

------

### Markdown简介

1. Markdown 的简述
    - Markdown 是一种轻量级的**标记语言**[^1]，可用于在纯文本文档中添加格式化元素。
    - Markdown 的**语法**被设计为**可读性强**且不显眼，因此即使 Markdown 文件中的文本未经过渲染也易于阅读。
    - Markdown 优点
      1. **专注于文字**内容；
      2. **纯文本，易读易写**，可以方便地纳入版本控制；
      3. **语法简单**，没有什么学习成本，能轻松在码字的同时做出美观大方的排版。
</br>

2. 使用 Markdown 原因
    - Markdown 的语法是可读性强且不显眼的
    - Markdown 是纯文本可移植的
    - Markdown 是独立于平台的
    - Markdown 能适应未来的变化
</br>

3. Markdown 的工作原理
    - Markdown 应用程序使用一种称为 Markdown 处理器（也通常称为“解析器”或“实现”）的东西将获取到的 **Markdown 格式**的文本输出为 **HTML 格式**
    - **注意**： Markdown 应用程序和处理器是两个单独的组件（解析，渲染）。
</br>

4. Markdown 的用途
    - 做笔记、为网站创建内容以及生成可打印文档的快速、简便的方法（书籍、网站、文档、笔记等）
</br>

5. Markdown 的其它资源
    - [John Gruber’s Markdown documentation](https://daringfireball.net/projects/markdown/). Markdown 的创建者编写的原始指南。
    - [Markdown Tutorial](https://www.markdowntutorial.com/). 一个开源网站，你能用浏览器在这个网站上尝试 Markdown。
    - [Awesome Markdown](https://github.com/mundimark/awesome-markdown). Markdown 工具和学习资源列表。
    - [Typesetting Markdown](https://dave.autonoma.ca/blog/2019/05/22/typesetting-markdown-part-1). 这是一个系列教程，介绍了使用 pandoc 和 ConTeXt 对 Markdown 文档进行排版的系统。

------

#### Markdown基础语法

##### 标题

> 用法如下：

    为了兼容考虑，请用一个空格在 # 和标题之间进行分隔。

    # Heading level 1
    ## Heading level 2
    ### Heading level 3
    #### Heading level 4
    ##### Heading level 5
    ###### Heading level 6

    可选语法：

    Heading level 1 
    ==============
    Heading level 2
    --------------  

------

##### 段落

> 用法如下：

    不要用空格（spaces）或制表符（ tabs）缩进段落。

    使用一个空白行来表示重新开始一个段落。

------

##### 换行

> 两种用法如下：

    1. 使用两个或两个以上空格（spaces）加上回车（return）。
    
    2. 使用html语法`</br>`

------

##### 强调语法

> 用法如下：

   由于Markdown 应用程序在如何处理单词或短语中间的下划线上并不一致，为了兼容性，应优先使用*

    *斜体文本*  
    
    _斜体文本_  
    
    **粗体文本**  
    
    __粗体文本__  
    
    ***粗斜体文本***  
    
    ___粗斜体文本___ 

------

##### 块引用

> 用法如下：

    块引用: 在段落开头使用 > 符号, 后面紧跟一个空格。

    多个段落的块引用：为段落之间的空白行添加一个 > 符号。

    嵌套块引用: > > 加上空格代表二级嵌套, 依此类推。  

    块引用中使用其它元素：

    1. 块引用中使用列表: 先使用区块，再使用列表。  
    2. 列表中的块引用: 在`>`前面缩进四个空格或者一个制表符(Tab键)。
    3. 块引用中使用粗体、斜体、粗斜体。
   
    1.块的引用
    > Markdown区块
    
    2. 多个段落的块引用
    > 第一段
    > 
    > 第二段
    
    3. 块引用的嵌套
    > 最外层
    > > 第一层嵌套
    > > > 第二层嵌套
    
    4.块引用中使用列表
    > 区块中使用列表
    > 1. 第一项
    > 2. 第二项
    > 3. 第三项
    
    > - 第一项
    > - 第二项
    > - 第三项
    >   - 第四项

    5.列表中的块引用
    - 第一项
        > 第一项第一个元素
        > 第一项第二个元素
    
    - 第二项
        > 第二项第一个元素
        > 第二项第二个元素

------

##### 有序和无序列表

> 用法如下：

    有序列表：有序列表使用数字并加上 . 号来表示列表标记。数字不必按数学顺序排列，但是列表应当以数字 1 起始。

    无序列表：使用星号(*),加号(+)或是破折号号(-) 作为列表标记。（每篇文章最好只使用一种符号）

    列表嵌套其他元素：只需在子列表中的添加四个空格或者一个制表符(Tab键)。

    列表中的代码块|图片：代码块|图片通常采用四个空格或一个制表符缩进。在列表中时应该缩进八个空格或两个制表符。（使用前后还需留有空白行）

    为了兼容性，不要在同一个列表中混合和匹配分隔符 ，选择一个并坚持使用它。

    1. 有序列表
        1. 第一项
        2. 第二项
        3. 第三项
    
    2. 无序列表
        + 第一项
        + 第二项
        + 第三项

        - 第一项
        - 第二项
        - 第三项

        * 第一项
        * 第二项
        * 第三项
       
    3. 列表嵌套
        1. First item
        2. Second item
        3. Third item
            1. Indented item
            2. Indented item
        4. Fourth item

        - First item
        - Second item
        - Third item
            - Indented item
            - Indented item
        - Fourth ite

        1. First item
        2. Second item
        3. Third item
            - Indented item
            - Indented item
        4. Fourth item

    4. 列表中的代码块
    - 第一项

            <HTML>
            <head>
            <title>Test</title>
            </head>
            </HTML>

    - 第二项

    1. 列表中的图片
    - 第一项

        ![马克思](https://bkimg.cdn.bcebos.com/pic/a8ec8a13632762d04187f99baeec08fa513dc65d?x-bce-process=image/resize,m_lfit,w_536,limit_1/format,f_jpg)
    
    - 第二项

------

##### 代码

> 用法如下：

    函数或代码片段：使用反引号(`)包裹起来  

    转义反引号：使用双反引号(``)为代码的单词或短语中包含一个或多个反引号

    代码块：缩进 4 个空格或者一个制表符(Tab 键)  

    1. 函数或片段代码 
    `printf()` 函数  
    
    2. 转义反引号
    ``Use `code` in your Markdown file.``
    
    3. 代码块  
    制表符或者4个空格 + 文本数据。

        <html>
          <head>
          </head>
        </html>  

------

##### 分割线

> 用法如下：

    在一行中使用：三个及以上的星号(***)、破折号(---) 、下划线 (___) 建立分割线。

    或者使用HTML中的<hr>标签

    为了兼容性，在分隔线的前后均添加空白行。

    ***
    
    * * *
    
    *****
    
    ---

    - - -
    
    ------

    _ _ _

    ___

    ______

------

##### 链接

> 用法如下：

    语法：[链接名称](链接地址 "超链接title")

    对应的HTML代码：<a href="超链接地址" title="超链接title">超链接显示名</a>

    补充：链接title是当鼠标悬停在链接上时会出现的文字，title是可选的。

    可点击的链接：使用尖括号可以很方便地把URL或者email地址变成可点击的链接。

    带格式的链接： 
    
    1. 强调链接：在链接语法前后增加星号。（双星号粗体链接，单星号斜体链接）
    2. 将链接表示为代码：在方括号中添加反引号。
   
    引用类型链接：用脚注的方式书写链接，换言之链接也可以用变量代替。（引用位置可以放在Markdown文档中的任何位置。例如：尾注或脚注）

    Tips：不同的 Markdown 应用程序处理URL中间的空格方式不一样。为了兼容性，尽量使用%20代替空格 

    1. 超链接
    这是一个链接[谷歌](http://www.google.com)
    这是一个带Title的链接[谷歌](http://www.google.com "好的浏览器")

    2. 可点击的链接（网址和Email地址）
    <http://www.google.com>
    <fake@example.com> 

    3. 带格式化的链接

        强调链接：
        
        双星号：粗体
        I love supporting the **[EFF](https://eff.org)**.
        单星号：斜体
        This is the *[Markdown Guide](https://www.markdownguide.org)*.

        将链接表示为代码：
        See the section on [`https://markdown.com.cn/`](#code).

    4. 引用类型链接

    用变量（标签）来代替文档末尾附带变量（标签）、链接(可以选择将其括在尖括号中)和链接的可选标题（可以将其括在双引号，单引号或括号中）：

    这个链接用 1 作为网址变量 [Google] [1]
    这个链接用 chrome 作为网址变量 [Google] [chrome]
    这个链接用 to 作为网址变量 [Google] [to]

    然后在文档的结尾为变量赋值（链接）
    [1]: http://www.google.com/ "Google"
    [chrome]: http://www.google.com/ 'Google'
    [to]: <http://www.google.com/> (Google)

------

##### 图片  

> 用法如下：

    1. 语法
    ![alt 属性文本](图片地址)  
    
    ![alt 属性文本](图片地址 "图片的可选标题")
    对应的HTML代码：<img src="图片链接" alt="图片alt" title="图片title">  

    2.链接图片
    将图像的Markdown 括在方括号中，然后将链接添加在圆括号中。

    [![Avatar]([/assets/img/shiprock.jpg](https://shuguang2000.github.io/blog/images/avatar.jpg) "Avatar")](https://shuguang2000.github.io/blog/)
    
    3. 给图片添加引用链接
    这个链接用 1 作为网址变量 [Avatar][1].
    
    [1]: https://shuguang2000.github.io/blog/images/avatar.jpg

------

##### 转义字符反斜杠

> 用法如下：

    要显示原本用于格式化 Markdown 文档的字符，在字符前面添加反斜杠字符 \ 。

    1. 实例：
    **文本加粗** 
    \*\* 正常显示星号 \*\*  
    
    2. Markdown 支持使用反斜杠字符转译以下符号
    \   反斜线
    `   反引号
    *   星号
    _   下划线
    {}  花括号
    []  方括号
    ()  小括号
    #   井字号
    +   加号
    -   减号
    .   英文句点
    !   感叹号

    3. 特殊字符自动转义

    在 HTML 文件中，有两个字符需要特殊处理： < 和 & 。 < 符号用于起始标签，& 符号则用于标记 HTML 实体，如果你只是想要使用这些符号，你必须要使用实体的形式，像是 &lt; 和 &amp;。

    Markdown 允许你直接使用这些符号，它帮你自动转义字符。如果你使用 & 符号的作为 HTML 实体的一部分(比如：“<u>”作为HTML标签)，那么它不会被转换，而在其它情况下（比如：“4 < 5”），它则会被转换成 &lt;。

    Tips: 需要特别注意的是，在 Markdown 的块级元素和内联元素中， < 和 & 两个符号都会被自动转换成 HTML 实体，这项特性让你可以很容易地用 Markdown 写 HTML。（但在 HTML 语法中，你要手动把所有的 < 和 & 都转换为 HTML 实体。）

------

##### 内嵌HTML标签

> 用法如下：

    注意: 出于安全原因，并非所有 Markdown 应用程序都支持在 Markdown 文档中添加 HTML。

    对于 Markdown 涵盖范围之外的标签，都可以直接在文件里面用 HTML 本身。

    1. 行级内联标签（内联元素也叫行内元素）
    HTML 的行级内联标签如 <span>、<cite>、<del>、<strong> 不受限制，可以在 Markdown 的段落、列表或是标题里任意使用。

    Tips：HTML 行级内联标签和区块标签不同，在内联标签的范围内， Markdown 的语法是可以解析的。

    <strong>*word*</strong>

    2. 区块标签
    区块元素──比如 <div>、<table>、<pre>、<p> 等标签，必须在前后加上空行，以便于内容区分。

    而且这些元素的开始与结尾标签，不可以用 tab 或是空白来缩进。Markdown 会自动识别这区块元素，避免在区块标签前后加上没有必要的 <p> 标签。

    Tips：Markdown 语法在 HTML 区块标签中将不会被进行处理。

    This is a regular paragraph.

    <table>
        <tr>
            <td>Foo</td>
        </tr>
    </table>

    This is another regular paragraph.

------

#### Markdown扩展语法

- 并非所有Markdown应用程序都支持扩展语法元素。

- 轻量标记语言：有几种轻量级标记语言是Markdown的超集。
  - [CommonMark](https://commonmark.org/)
  - [GitHub Flavo red Markdown (GFM)](https://github.github.com/gfm/)
  - [Markdown Extra](https://michelf.ca/projects/php-markdown/extra/)
  - [MultiMarkdown](https://michelf.ca/projects/php-markdown/extra/)
  - [R Markdown](https://rmarkdown.rstudio.com/)
</br>
- Markdown 处理器：

  - 有许多[Markdown处理器](https://github.com/markdown/markdown.github.com/wiki/Implementations) 可用。它们中的许多允许添加启用扩展语法元素的扩展。

------

##### 表格

> 用法如下：

    使用三个或多个连字符（---）创建每列的标题，并使用管道（|）分隔每列。

    使用连字符和管道创建表可能很麻烦。为了加快该过程，请尝试使用[Markdown Tables Generator](https://www.tablesgenerator.com/markdown_tables)创建列表。

    1. 语法
    | Syntax      | Description |
    | ----------- | ----------- |
    | Header      | Title       |
    | Paragraph   | Text        |
     
    2. 单元格宽度可以变化
    | Syntax | Description |
    | --- | ----------- |
    | Header | Title |
    | Paragraph | Text |

    3. 对齐
    -: 设置内容和标题栏居右对齐。
    :- 设置内容和标题栏居左对齐。
    :-: 设置内容和标题栏居中对齐。 

    | 左对齐 | 右对齐 | 居中对齐 |
    | :----- | ----:  | :----: |
    | 单元格 | 单元格 | 单元格 |
    | 单元格 | 单元格 | 单元格 |

    4. 格式化表格中的文字
    可以在表格中设置文本格式。例如：
    
    添加：链接，代码（仅反引号（`）中的单词或短语，而不是代码块）和强调。

    不能添加：标题，块引用，列表，水平规则，图像或HTML标签。

    5. 在表中转义管道字符
    在表中显示竖线（|）字符：使用表格的HTML字符代码（&#124;）。

------

##### 围栏代码块

> 用法如下：

    使用三个反引号（(```）或三个波浪号（~~~）包裹一段代码。
    
    在三个反引号旁边指定一种语言即可实现语法高亮。

    ```javascript
    $(document).ready(function () {
        alert('run');
    });
    ```

------

##### 脚注

> 用法如下：

    [^标识符] 

    [^标识符]: My footnote.

    标识符可以是数字或单词，但不能包含空格或制表符。

    不必在文档末尾添加脚注。可以将它们放在除列表，块引号和表之类的其他元素之外的任何位置。

    应用举例：

    随机存取存储器RAM(Random Access Memory)[^sola]。
    [^sola]:又称作“随机存储器”，是与CPU直接交换数据的内部存储器，也叫主存(一般指的是内存)  
    
    只读存储器(Read Only Memory，ROM)[^sola1]。  
    [^sola1]: ROM所存数据，一般是装入整机前事先写好的，整机工作过程中只能读出，而不像随机存储器那样能快速地、方便地加以改写。ROM所存数据稳定，断电后所存数据也不会改变  
    
    RAM与ROM都是内存，而硬盘是外存，所以ROM不等于硬盘。计算机中的ROM主要是用来存储一些系统信息，或者启动程序BIOS程序，这些都是非常重要的，只可以读一般不能修改，断电也不会消失

------

##### 标题编号

> 用法如下：

    许多Markdown处理器支持标题的自定义ID，一些Markdown处理器会自动添加它们。

    添加自定义ID：允许直接链接到标题并使用CSS对其进行修改。
    
    自定义标题ID：在与标题相同的行上用大括号括起该自定义ID。

    应用举例：

    ```html
    ### My Great Heading {#custom-id}
    对应html代码:
    <h3 id="custom-id">My Great Heading</h3>


    链接到标题ID(#headid)：

    [Heading-ids](#heading-ids)

    对应html代码：
    <a href="#heading-ids">Heading-ids</a>
    ```

    作用：通过将自定义标题ID添加到网页的完整URL，能快速链接到网页标题内容，作用类似于书签。

    <https://markdown.com.cn/extended-syntax/heading-ids.html#headid>

------

##### 定义列表

> 用法如下：

    一些Markdown处理器允许您创建术语及其对应定义的定义列表。

    在第一行上键入术语。在下一行，键入一个冒号，后跟一个空格和定义。

    First Term
    : This is the definition of the first term.

    Second Term
    : This is one definition of the second term.
    : This is another definition of the second term.

    对应HTML代码:

    <dl>
        <dt>First Term</dt>
        <dd>This is the definition of the first term.</dd>
        <dt>Second Term</dt>
        <dd>This is one definition of the second term. </dd>
        <dd>This is another definition of the second term.</dd>
    </dl>


------

##### 删除线

> 用法如下：

    在单词前后使用两个波浪号~~。
    
    BAIDU.COM  
    ~~BAIDU.COM~~

------

##### 任务列表

> 用法如下：

    任务列表使您可以创建带有复选框的项目列表。

    破折号+空格+方括号（方括号中必须有空格（未完成）或者x（已完成））

    ```
    - [x] Write the press release
    - [ ] Update the website
    - [ ] Contact the media
    ```

------

##### Emoji表情

> 用法如下：

    将表情符号复制并粘贴到Markdown格式的文本中，或者键入emoji shortcodes。

    1. 复制和粘贴表情符号

        从Emojipedia: <https://emojipedia.org/> 等来源复制表情符号并将其粘贴到文档中。

        Tip: 如果使用的是静态网站生成器，确保将HTML页面编码为UTF-8。

    2. 使用表情符号简码

        一些Markdown应用程序允许通过键入表情符号短代码来插入表情符号

        去露营了！ :tent: 很快回来。
        真好笑！ :joy:

        注意：可以使用此表情符号简码列表:<https://gist.github.com/rxaviers/7360908>，表情符号简码因应用程序而异。

------

##### 自动网址链接

> 用法如下：

    许多Markdown处理器会自动将URL转换为链接，即使未使用方括号。
    http://www.example.com

    禁用自动URL链接(也就是改写为代码)
    `http://www.example.com`

------

##### 下划线

> 用法如下：

    使用HTML的`<u>`标签 

    <u>带下划线文本</u>

------

##### 链接本地文件

> 用法如下：

    ​[Markdown使用教程](./Markdown使用教程.md)

------

##### 添加目录  

> 两种用法如下：

    1. 自动生成目录
        - 用法：`[toc]`
        - TOC (Table of Content)
          - 部分平台支持
            - Visual Studio Code + TOC 扩展插件支持
            - Typora支持
       - 要在TOC排除一个标题：在其后面添加 {ignore=true}
    2. 手动书写目录
        - Visual Studio Code + vscode-Markdown All in One插件（生成与手写目录基本一样，都是id选择器）
          - 用法：快捷键 Ctrl + Shift + P -> markdown all in one create table of contents
        - 手写目录
          - 用法：[目录名](#标题链接)
          - 注意：
            - 标题链接中大写字母用小写字母代替
            - 标题链接中空格用 - 代替

------

##### 返回目录

> 两种用法如下：

    1. 以目录为锚点进行跳转
    [加入跳转的文字](#目录)
    
    2. 结合 html 语法
    
    ```html
    <a href="#目录" class="top_e"><img src="../Resource/Top.png" style="position:fixed;right:30px;bottom:40px;
            cursor:pointer;
            width:40px;
            height:40px;"/></a>
    ```

[^1]: 标记语言: 是一种将文本以及文本相关的其他信息结合起来，展现出关于文档结构和数据处理细节的电脑文字编码
