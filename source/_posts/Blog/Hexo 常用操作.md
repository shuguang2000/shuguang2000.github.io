---
title: Hexo 常用操作
date: 2022-11-12 16:31:58
updated: {{ updated }}
categories:
- Blog
tags:
- Hexo
- Next
author: shuguang2000
keywords: Hexo 常用操作
comments: true
---
- 本文主要介绍了关于Hexo**基础知识**、**常用命令**、**自定义**以及**标签插件**四个方面内容。
</br>

- 更多相关内容参考：[Hexo文档](https://hexo.io/zh-cn/docs/)

<!--more-->

------

### Hexo基础

- **Hexo文档**：<https://hexo.io/zh-cn/docs/>
</br>

- **Hexo目录结构**
  - _config.yml
    - 网站的配置信息。
  - package.json
    - 应用程序的信息（依赖）。
  - scaffolds
    - 模版文件夹，Hexo 会根据 scaffold 来建立文章。
  - source
    - 资源文件夹是存放用户资源的地方。
    - 除_posts文件夹之外，开头命名为_(下划线)的文件 | 文件夹和隐藏的文件将会被忽略。
    - Markdown 和 HTML 文件会被解析并放到 public 文件夹，而其他文件会被拷贝过去。
  - themes
    - 主题文件夹。Hexo 会根据主题来生成静态页面。
</br>

- **Hexo基础知识**
  - Hexo 支持以任何格式书写文章，只要安装了相应的渲染插件。（如默认可渲染mark down和ejs格式文章：hexo-renderer-marked 和 hexo-renderer-ejs）
  </br>
  - Hexo相关配置：<https://hexo.io/zh-cn/docs/configuration>
  </br>
  - Hexo 有三种默认布局：post、page 和 draft。
    - page将储存到source，draft将储存到source/_drafts；而自定义的其他布局和 post 相同（默认）储存到 source/_posts 文件夹。
  </br>
  - Front-matter 是文件最上方以 --- 分隔的区域，用于指定个别文件的变量。（这也是Hexo文章于普通Markdown文章的区别）
  </br>
  - 分类和标签
    - 分类具有顺序性和层次性，而标签没有顺序和层次。(不允许指定多个同级分类)
    - 为文章添加多个分类，可以尝试使用list，每个列表是该文章一个分类，list中除第一个元素外其余元素都是该list的子分类。
  </br>
  - 标签插件
    - 用于在文章中快速插入特定内容的插件。
    - 标签插件不应包含在Markdown语法中。
  </br>
  - 关于相对路径中引用的标签插件
    - 使用相对路径的常规 markdown语法资源不会出现在首页上。（但是它会在文章中按你期待的方式工作）
    - 但使用标签插件后资源会同时出现在文章和主页以及归档页中。
  </br>
  - 数据文件
    - 有时可能需要在主题中使用某些资料，而这些资料并不在文章内，并且是需要重复使用的。此功能会载入 source/_data 内的 YAML 或 JSON 文件，如此一来您便能在网站中复用这些文件了。
    - 如：next主题配置文件中存在相关配置，只需要在source/_data下创建对应的YAML 或 JSON 文件即可。
  </br>

- **Hexo自定义**
  - 永久链接
    - _config.yml 配置中或者在每篇文章的 Front-matter 中，均可调整网站的永久链接（permalink）。
    - [permalink参数变量](https://hexo.io/zh-cn/docs/permalinks)
      - :title文件名称 (relative to “source/_posts/“ folder)
      - :name文件名称
      - :post_title文章标题
  </br>
  - 多语种支持
    - 修改 new_post_name 和 permalink 参数
    - 在新建文章时指定`--lang language`

    ```yml
    new_post_name: :lang/:title.md
    permalink: :lang/:title/
    ```

  </br>
  - 变量
    - 全局变量
    - 网站变量
    - 页面变量（page）
      - 文章（post）
      - 首页（index）
      - 归档 (archive)
      - 分类 (category)
      - 标签 (tag)
    - 更多参考：<https://hexo.io/zh-cn/docs/variables>
  </br>
  - 更多内容（主题、模板、辅助函数、国际化、代码高亮、插件）参考：<https://hexo.io/zh-cn/docs/>

</br>

- **Hexo扩展**
  - Hexo API
    - <https://hexo.bootcss.com/api/>
  - 补充URL中的相关知识
    - “#”表示网页中的一个位置，被称之为锚点，常用于某个网页间不同位置的跳转。
    - ?，问号：常用于动态网站，实现不同的参数值而生成不同的页面或者返回不同的结果。

------

#### Hexo常用命令

- **部署**
  - `hexo init [folder]`
    - 新建一个网站（git远程克隆hexo-starter 和 hexo-theme-landscape主题，并使用包管理器下载依赖）
  </br>
  - `hexo clean`
    - 清除缓存文件 db.json 和已生成的静态文件 public。
  </br>
  - `hexo generate | hexo g`
    - 生成静态文件到public（默认）文件夹。
      - `-w, --watch` 监视文件变动
      - `-b, --bail` 生成过程中如果发生任何未处理的异常则抛出异常
      - `-f, --force` 强制重新生成文件，Hexo 引入了差分机制，如果 public 目录存在，那么 hexo g 只会重新生成改动的文件。使用该参数的效果接近 hexo clean && hexo generate
      - 如果使用自动部署（使用插件hexo-deployer-git），不需要先执行该命令。
  </br>
  - `hexo server`
    - 启动本地服务器，用于预览主题
      - `-p, --port` 重设端口
      - `-s, --static` 只使用静态文件
        - 在静态模式下，服务器只处理 public 文件夹内的文件，而不会处理文件变动（通常用于生产环境（production mode）下。）
      - `-l, --log` 启动日记记录，使用覆盖记录格式
  </br>
  - `hexo deploy | hexo d`
    - 部署网站。
  </br>
  - `hexo clean && hexo g && hexo s`
    - 建议使用。
    - 不建议使用 `hexo g -d` 或者 `hexo d -g` 这类组合命令

- **写作**
  - `hexo new [layout] <title>`
    - Hexo 有三种默认布局：**post**、**page** 和 **draft**。在创建这三种不同类型的文件时，它们将会被保存到不同的路径；而您自定义的其他布局和 post 相同，都将储存到 source/_posts 文件夹。
    - 新建一篇文章（布局默认使用default_layout参数代替）
    - 若标题包含空格，需使用**引号括起来**。默认情况下，Hexo 会使用文章的标题来决定文章文件的路径。(title/index.md)。
    - `-p, --path <path> <title>` 自定义新文章的路径，指定路径后(默认会在source/_posts下创建)，Hexo 会使用路径下当前文件夹作为文件名称。（path/current_dir.md）
    - `-r, --replace` 如果存在同名文章，将其替换
    - `--lang <language>` 创建指定语言文件夹下的文章，文章的标题将不再决定文章的路径（language/title.md）
  </br>
  - `hexo render <file1> [file2] ...`
    - 渲染文件。
    - `-o, --output` 设置输出路径
  </br>
  - `hexo publish [layout] <filename>`
    - 通过 publish 命令将草稿移动到 source/_posts 文件夹。
    - 草稿默认不会显示在页面中，可在执行时加上 `--draft` 参数，或是把 render_drafts 参数设为 true 来预览草稿。

- **扩展**
  - `hexo --draft`
    - 显示 source/_drafts 文件夹中的草稿文章。
  - `hexo list <type>`
    - 列出网站资料。
  - `hexo version`
    - 显示 Hexo 版本
  - `hexo --cwd /path/to/cwdp`
    - 自定义当前工作目录（Current working directory）的路径。
  - `hexo --debug`
    - 在终端中显示调试信息并记录到 debug.log。
  - `hexo --safe`
    - 在安全模式下，不会载入插件和脚本。当在安装新插件遭遇问题时，可以尝试以安全模式重新执行。
  - `hexo migrate <type>`
    - 从其他博客系统 [迁移内容](https://hexo.io/zh-cn/docs/migration)。
  - `hexo help`

------

#### Hexo标签插件

- Hexo 使用内建 [Nunjucks](https://mozilla.github.io/nunjucks/) 模板引擎。
</br>
- 标签插件和 Front-matter 中的标签不同，它们是用于在文章中快速插入特定内容的插件。
</br>
- 虽然可以使用任何格式书写你的文章，但是**标签插件永远可用**，且语法也都是一致的。
</br>
- 常用标签插件

  - 引用块

    ```JavaScript
      {% blockquote [author[, source]] [link] [source_link_title] %}
      content
      {% endblockquote %}
    ```

  - 代码块

    ```JavaScript
      {% codeblock [title] [lang:language] [url] [link text] [additional options] %}
      code snippet
      {% endcodeblock %}
    ```

  - 反引号代码块

    ``` JavaScript
    [language] [title] [url] [link text] code snippet 
    ```

  - 引用文章

    ```JavaScript
      {% post_path filename %}
      {% post_link filename [title] [escape] %}
    ```

  - 引用资源

    ```JavaScript
      {% asset_path filename %}
      {% asset_img [class names] slug [width] [height] [title text [alt text]] %}
      {% asset_link filename [title] [escape] %}
    ```

  - Pull Quote

    ``` JavaScript
      {% pullquote [class] %}
      content
      {% endpullquote %}
    ```

  - jsFiddle

    ```JavaScript
      {% jsfiddle shorttag [tabs] [skin] [width] [height] %}
    ```

  - Gist

    ```JavaScript
      {% gist gist_id [filename] %}
    ```

  - iframe

    ```JavaScript
      {% iframe url [width] [height] %}
    ```

  - Image

    ```JavaScript
      {% img [class names] /path/to/image [width] [height] '"title text" "alt text"' %}
    ```

  - Link

    ```JavaScript
      {% link text url [external] [title] %}
    ```

  - Include Code

    ```JavaScript
      {% include_code [title] [lang:language] [from:line] [to:line] path/to/file %}
    ```

- 完整的标签列表参考：<https://hexo.io/docs/tag-plugins.html>

------
