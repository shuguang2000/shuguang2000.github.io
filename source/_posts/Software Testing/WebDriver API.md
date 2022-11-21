---
title: WebDriver API
date: 2022-11-19 13:31:58
updated: {{ updated }}
categories:
- Software Testing
tags:
- WebDriver
author: shuguang2000
keywords: WebDriver API
comments: true
---
- WebDriver是一个用于实现Web自动化的第三方库，本文主要介绍WebDriver的用法及原理。
<!-- more -->

------

#### 定位元素

- WebDriver 提供了八种定位方法(tag 标签，partial局部的)
  - id -- name
  - class name -- tag name
  - link text -- partial link text
  - xpath -- css selector
  - find_element_by_id() -- find_element_by_name()
  - find_element_by_class_name() -- find_element_by_tag_name()
  - find_element_by_link_text() -- find_element_by_partial_link_text()
  - find_element_by_xpath() -- find_element_by_css_selector
</br>

- **Xpath定位**(find_element_by_xpath())
  - Xpath简介：**XPath 是一门在 XML 文档中查找信息的语言**
  - Xpath主要用：标签名的层级关系来定位元素的绝对路径。举例:div[2]代表当前层级下第二个div
  - **绝对路径定位**：使用XPath语言定位。
  - **利用元素属性定位**(XPath可使用**元素的任意属性**)

    ```Python
      find_element_by_xpath("//input[@id='kw']")
      find_element_by_xpath("//input[@name='wd']")
      find_element_by_xpath("//input[@class='s_ipt']")
      find_element_by_xpath("//*[@class='bg s_btn']")
      find_element_by_xpath("//input[@maxlength='100']")
      find_element_by_xpath("//input[@autocomplete='off']")
      find_element_by_xpath("//input[@type='submit']")
    ```

  - //**代表当前页面某个目录**
    - 不指定标签名，也可以用- 代替
  - **层级与属性结合**（元素本身没有唯一可标识的属性值）'

    ```Python
    find_element_by_xpath("//span[@class='bg s_ipt_wr']/input")
    find_element_by_xpath("//from[@id='from']/span/input")
    find_element_by_xpath("//from[@id='from']/sapn[2]/input")
    ```

  - 使用逻辑运算符(属性不能唯一得区分一个元素,连接多个属性)

    ```Python
    find_element_by_xpath("//input[@id='kw' and @class='su']/span/input")
    ```

  - FirePath插件直接生成Xpath语法
  - **使用starts-with方法**
    - `//*[starts-with(@attribute, "xxx")]`
  - **使用contains方法**

    ```Python
    # driver.find_element_by_xpath("//a[contains(text(),'一个很长的')]")
    driver.find_element_by_xpath("//span[contains(@class,'s_ipt_wr')]/input")
    ```

  - **使用text()方法**

    ```Python
    # //*[text()="xxx"]
    driver.find_element_by_xpath("//a[text(),'新闻')]")
    ```

</br>

- **CSS定位**(一般情况下速度要比XPath快)
  - 选择所有元素
    - `find_element_by_class_selector("*")`
  - 使用class属性定位
    - `find_element_by_class_selector(".s_ipt")`
  - 使用id属性来定位：
    - `find_element_by_class_selector("#kw")`
  - 使用标签名来定位元素
    - `find_element_by_class_selector("input")`
  - 通过父子关系来定位
    - span下的所有input
      - `find_element_by_class_selector("span>input")`
    - 同一级span之后的所有input
      - `find_element_by_class_selector("span+input")`
  - 通过属性定位
    - `find_element_by_class_selector("[name='kw']")`
  - 组合定位
    - `find_element_by_class_selector("span.bg si_sipt_wr>input.s_ipt")`
  - 使用属性的部分定位的CSS表达式：
    - 标签[属性^='值'] 属性开头包含
    - 标签[属性$='值'] 属性结尾包含
    - 标签[属性*='值'] 属性开头包含
  - 使用伪类选择器的CSS表达式
    - 伪类选择器（简称：伪类）通过冒号来定义，它定义了元素的状态，如点击按下，点击完成等，通过伪类可以为元素的状态修改样式。
    - div#div1:first-child
    - div#div1:nth-child
    - div#div1:last-child
    - input:focus
    - input:enabled
    - input:checked

  - 查找同级元素的CSS表达式
    - div#div1 - input + a
    - div#div1 - input + a + img
    - div#div1 - input + - + img
</br>

- 使用谷歌console验证
  - $('css表达式')验证css表达式
  - 输入$x('xpath表达式')验证xpath表达式
</br>

- **使用By定位**
  - 用By定位元素（统一调用find_element()方法）
  - 将By类导入: `from selenium.webdriver.common.by import By`

    ```Python
    find_element(By.ID,"kw")
    find_element(By.NAME,"wd")
    find_element(By.TAG_NAME,"input")
    find_element(By.LINK_TEXT,"新闻")
    find_element(By.PARTIAL-LINK-TEXT,"新")
    find_element(By.XPATH,"//*[@class='bg s_btn']")
    find_element(By.CSS_SELECTOR,"span.bg s_btn-wr>input#su")
    ```

  - 注意事项
    - WebDriver更加推荐前面介绍的写法（父子类）

------

#### 控制浏览器

- WebDriver 主要提供的是操作页面上各种元素的方法，但是也提供了操作浏览器的一些方法，例如控制浏览器的大小，操作浏览器的前进和后退等。
</br>

- 控制浏览窗口的大小
  - `set_window_size()`
  - `maximize_window()`方法打开浏览器的全屏显示
- 模拟浏览器刷新
  - `dirver.refresh()`   # 刷新当前页面
</br>

- 简单的元素操作
  - `driver.forword()`前进
  - `driver.back()`后退
  - `clear()`清除文本
  - `send_keys(*value)` 模拟按键输入
  - `click()`单击元素
  - `submit（）`方法用来提交表单
</br>

- **获取元素的属性**
  - size     返回元素的尺寸。
  - text     获取元素的文本
  - `get_attribute(name)`获得属性值
  - `is_displayed()`设置该元素是否用户可见。
</br>

- **鼠标事件**

  - 需要导入ActionChains类
  - ActionChains(driver)
  - perform()执行所有ActionChains的存储行为, 提交动作
  - context(right_click)模拟鼠标右键操作，需要元素定位
  - double_click()双击
  - drag_and_drop()拖动和释放
  - move_to_element()鼠标悬停
</br>

- **键盘事件**
  - Keys类几乎提供了键盘上的所有方法。
  - send_keys(Keys.BACK_SPACE) 删除键（BackSpace）
  - send_keys(Keys.SPACE) 空格键(Space)
  - send_keys(Keys.TAB) 制表键(Tab)
  - send_keys(Keys.ESCAPE) 回退键（Esc）
  - send_keys(Keys.ENTER) 回车键（Enter）
  - send_keys(Keys.CONTROL,'a') 全选（Ctrl+A）
  - send_keys(Keys.CONTROL,'c') 复制（Ctrl+C）
  - send_keys(Keys.CONTROL,'x') 剪切（Ctrl+X）
  - send_keys(Keys.CONTROL,'v') 粘贴（Ctrl+V）
  - send_keys(Keys.F1) 键盘 F1
  - send_keys(Keys.F12) 键盘 F12
</br>

- **获取验证信息**
  - 通常用的最多的验证信息（title、URL和text）
  - 获取当前页面的title
    - `driver.title`
  - 获取当前页面的url
    - `driver.current_url`
  - 获取标签的文本
    - `driver.find_element_by _id("kw").text`
</br>

- **设置元素等待**
  - 页面上元素可能并不是同时被加载完成的（web应用程序使用了大量的AJAX技术）这给定位增加了困难

  - **显示等待**（达到最大时限时抛出超时异常）
    - WebDriverWait类时WebDriver提供的等待方法，在设置时间内，默认每隔一段时间检测当前页面元素是否存在，如果超过设定时间检测不到则抛出异常。

    ```Python
    from `selenium.webdriver.support` import expected_conditions as EC
    from selenium.webdriver.common.by import By

    element = WebDriverWaitdriver(driver,5,0.5).until
    (EC.presence_of_element_located((By.ID,"kw")))
    element.send_keys("selenium")
    ```

  - **隐式等待**（抛出无此元素异常）

    - 超过设定时常元素还没有被加载，就抛出NoSuchElementException异常。

    - implicitly_wait()实现隐式等待

    - webdriver提供了implicitly_wait()来实现隐式等待, 默认为0 , 一般在元素定位操作之前设置

  - **强制等待**: `sleep()`
    - 通过Python内置time模块提供，通过sleep(n秒)强制等待来延迟执行下一个操作 （参数可以是小数）

  - 不同等待之间的区别
    - 强制等待的时间是固定的
    </br>
    - 显式等待是在等待时间内对条件轮询(0.5s),当超出等待时间条件仍不满足,抛出超时异常(TimeOutException), **建议在js异步和需要延时才能查找到元素的场景下使用显式等待.**（能够确定等待时间时使用）
    </br>
    - 隐式等待是在等待时间内对页面加载完毕的当前dom轮询,查看元素是否加载,当超出等待时间,抛出无此元素的异常(NoSuchElementException), 如有多个元素查找会创建多个隐式等待
    </br>
    - 若同时设置显示等待和隐式等待，当显示等待在设定的等待时间内条件满足,则停止等待,执行后面的操作(使用隐式等待),否则抛出超时异常。
    </br>
    - **显示等待会优先于隐式等待，当显式等待超时少于隐式等待超时,会继续进入隐式等待。**

------

#### WebDriver 常用操作

- **定位一组元素**

  - `find_elements_xxx("xx")`   定位一组元素

- **多表单切换**

  - `switch_to.frame()`  进入表单
  - `switch_to.default_content()`  退出表单至根页面

- **多窗口切换**

  - `switch_to.window()`切换窗口
  - current_window_handle 获得当前窗口的句柄
  - window_handles：返回所有窗口的句柄到当前会话

- **警告框**

  - text：返回 alert/confirm/prompt 中的文字信息。
  - accept()：接受现有警告框。
  - dismiss()：解散现有警告框。
  - send_keys(keysToSend)： 发送文本至警告框。

- **下拉框**

  - Select  操作select标签的下拉框。
  - select_by_value()  选择value属性选择。
  - select_by_visible_text() 通过选项名称选择。
  - select_by_index() 通过索引选择

- **文件上传**

  - **Chrome浏览器**

    ```Python
    """
    chrome浏览器实现下载
    """
    import os
    from selenium import webdriver
    options = webdriver.ChromeOptions() 
    prefs = {'profile.default_content_settings.popups': 0,
    'download.default_directory': os.getcwd()}
    options.add_experimental_option('prefs', prefs) 

    driver = webdriver.Chrome(chrome_options=options) 
    driver.get("https://pypi.org/project/selenium/#files")
    driver.find_element_by_partial_link_text("selenium-3.141.0.tar.gz").click()
    ```

  - **Firefox浏览器**

    ```Python
    """
    firefox浏览器实现下载
    """
    import os
    from selenium import webdriver
    fp = webdriver.FirefoxProfile()
    fp.set_preference("browser.download.folderList", 2)
    fp.set_preference("browser.download.dir", os.getcwd())
    fp.set_preference("browser.helperApps.neverAsk.saveToDisk", "binary/octet-stream")
    driver = webdriver.Firefox(firefox_profile=fp)
    driver.get("https://pypi.org/project/selenium/#files")
    driver.find_element_by_partial_link_text("selenium-3.141.0.tar.gz").click()
    ```

- **Cookie**

  - `driver.add_cookie(dict)`

  - `driver.get_cookies()`

- **调用js代码**

  - `driver.execute_script(js)`

- **窗口截图**

  - driver.get_screenshot_as_file("/Screenshots/foo.png")

- **关闭窗口**

  - `driver.close()`

- **使用logging模块basicCofig()方法**

  - 开启debug模块捕获客户端向服务器发送的post请求。

      ```Python
      import logging
      logging.basicConfig(level=logging.DEBUG)
      ```

------

##### WebDriver原理

- WebDriver启动目标浏览器，并绑定到指定的端口，将创建的浏览器实例作为WebDriver的Remote Server（远程服务器）

- Client端通过`CommandExcuter`发送`HTTPRequest`给Remote Server的侦听端口。

- Remote Server需要原生的浏览器组件（`chromdriver`，等来转换浏览器的本地（native）调用）
