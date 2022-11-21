---
<!--页面（Page）变量-->
title: {{ title }}  //文章标题
date: {{ date }}    //文章创建时间
updated: {{ updated }}//页面更新日期	
comments:           //是否展示评论系统
layout:             //布局名称             
content:            //页面的完整内容
excerpt:            //页面摘要
more:               //除了页面摘要的其余内容
source:             //页面原始路径	
full_source:        //页面的完整原始路径
path:               //页面网址（不含根路径）。我们通常在主题中使用 url_for(page.path)。		
permalink:          //页面的完整网址
prev:               //上一个页面。如果此为第一个页面则为 null。
next:               //下一个页面。如果此为最后一个页面则为 null。
raw:                //文章的原始内容
photos:             //文章的照片（用于相簿）
links:              //文章的外部链接（用于链接文章）

<!--同页面（Page）变量，文章（Post）特有变量-->
published:          //如果该文章已发布则为 true
categories:         //文章分类目录
tags:               //文章标签，多个用[]，内部用，隔开

<!--首页（index）-->
per_page:           //每页显示的文章数量
total:              //总页数	
current:            //目前页数	
current_url:        //目前分页的网址	
posts:              //本页文章 (Data Model)	
prev:             ` //上一页的页数。如果此页是第一页的话则为 0。	
prev_link:          //上一页的网址。如果此页是第一页的话则为 ''。	
next:               //下一页的页数。如果此页是最后一页的话则为 0。	
next_link:          //下一页的网址。如果此页是最后一页的话则为 ''。	
path:               //当前页面的路径（不含根目录）。我们通常在主题中使用 url_for(page.path)。

<!--同首页（index）归档 (archive)特有变量-->
archive:            //true or false
year:               //年份归档 (4位)
month:              //月份归档 (没有前导零的2位数)

<!--同首页（index）分类 (category)特有变量-->
category:           //分类名称

<!--同首页（index）标签 (tag)特有变量-->
tag:                //标签名称	

<!--其他通用变量-->
author: shuguang2000
keywords:           //文章关键字
description:        //文章描述，用于seo，建议包含关键字
image:              //自定义的文章摘要图片，只在页面展示，文章内消失
# <img src="https://shuguang2000.github.io/images/avatar.jpg" width=50% />
toc:                //是否显示toc
toc_number:         //是否显示toc数字
copyright: true     //增加底部的版权信息（需要配置）
disableNunjucks:    //启用时禁用 Nunjucks 标签 {{ }}/{% %} 和标签插件的呈现
lang:               //设置语言以覆盖自动检测
top:	            //推荐文章（文章是否置顶），如果 top 值为 true，则会作为首页推荐文章
summary:	        //文章摘要，自定义的文章摘要内容
mathjax:	        //是否开启数学公式支持 ，本文章是否开启 mathjax，且需要在主题的 _config.yml 文件中也需要开启才行
password:           //文章阅读密码，如果要对文章设置阅读验证密码的话，就可以设置 password 的值，该值必须是用 SHA256 加密后的密码，防止被他人识破。前提是在主题的 config.yml 中激活了 verifyPassword 选项
img:                //文章特征图，推荐使用图床
# <!-- more -->和fontmatter之间的内容作为摘要。
---
- pass
<!-- more -->

------
