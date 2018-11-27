# 基于Python的自动化登录数据爬取

- Python是什么
- Python能做什么
- Python快速入门
- Python环境搭建
- 基于Python的自动化登录数据爬取

> **Python是什么**

- Python是一种面向对象的解释型计算机程序设计语言，由荷兰人Guido van Rossum于1989年发明，第一个公开发行版发行于1991年。
- Python是纯粹的自由软件， 源代码和解释器CPython遵循 GPL(GNU General Public License)协议。Python语法简洁清晰，特色之一是强制用空白符(white space)作为语句缩进。
- Python具有丰富和强大的库。它常被昵称为胶水语言，能够把用其他语言制作的各种模块（尤其是C/C++）很轻松地联结在一起。常见的一种应用情形是，使用Python快速生成程序的原型（有时甚至是程序的最终界面），然后对其中有特别要求的部分，用更合适的语言改写，比如3D游戏中的图形渲染模块，性能要求特别高，就可以用C/C++重写，而后封装为Python可以调用的扩展类库。需要注意的是在您使用扩展类库时可能需要考虑平台问题，某些可能不提供跨平台的实现。

> **Python发展趋势图**

![image](http://www.nongshanie.com/develop.png)


> **Python语言特点**

- 开发效率高
- 上手简单,易用
- 丰富的库
- 免费开源
- ......

> **Python能做什么**

- 爬虫 Scrapy  Request  urllib
- 人工智能和数据分析  pandas  numpy  Mastsplotlig  scipy
- 自动化运维  python  shell
- 云计算  OpenStack
- WEB开发 内容管理系统,后台管理系统 Django Tornado web2py

> **定义变量**

```
#数据类型 变量名称 = 值
a = "test"
a = 100
a,b = 100,200 #定义两个变量且赋值为100,200
print(a,b)
```
> **定义一个函数**


```
def work():
    print("人生苦短,我用python")
work();
```

> **定义一个类**

```
#在python中,可以多继承
class Student(object):
    #1 创建一个对象
    def __new__(cls,name,age):
        return object.__new__(cls)
    #2 进行初始化操作
    def __init__(self,name,age): #self:相当于java中的this命令,当前创建的对象
        self.name = name
        self.age = age
    def study(self):
        print("人生苦短,我用Python")
        
s1 = Student("zxx","17")
s1.study()
    
```

> **Python环境搭建**

- Python的安装

    根据你的Windows版本（64位还是32位）从Python的官方网站下载Python 3.6对应的[64位安装程序](https://www.python.org/ftp/python/3.6.3/python-3.6.3-amd64.exe)或[32位安装程序](https://www.python.org/ftp/python/3.6.3/python-3.6.3.exe)，然后，运行下载的EXE安装包:
    ![image](http://www.nongshanie.com/pyghon36.png)
   注意勾上Add Python 3.6 to PATH，然后点“Install Now”即可完成安装。
   
- Anaconda的安装

    > 什么是Anaconda
    
    anaconda指的是一个开源的Python发行版本，其包含了conda、Python等180多个科学包及其依赖项。   因为包含了大量的科学包，Anaconda 的下载文件比较大（约 515 MB），如果只需要某些包，或者需要节省带宽或存储空间，也可以使用Miniconda这个较小的发行版（仅包含conda和 Python）。
    
    > 安装Anaconda
    
    可以从[Anaconda官网](https://www.anaconda.com/download/)下载GUI安装包，安装包有500~600M，需要耐心等待下载。下载后直接安装，Anaconda会把系统Path中的python指向自己自带的Python，并且，Anaconda安装的第三方模块会安装在Anaconda自己的路径下，不影响系统已安装的Python目录。
    注意:![image](http://www.nongshanie.com/Anaconda.png)选择"All Users",意思是全局安装,可以减少不少的烦恼.
    
            
- PyCharm的安装

    1. 到[PyCharm官网](https://www.jetbrains.com/pycharm/)下载PyCharm安装.
    2. 到[lanyus](http://idea.lanyus.com/)获取激活码激活.
    3. license server激活:
        
    ```
      http://intellij.mandroid.cn/
    　http://idea.imsxm.com/
    　http://idea.iteblog.com/key.php
    ```
    
>   **如何使用python修改电脑环境变量?**
> **基于Python的自动登录数据爬取**

- 发送请求
- 获取数据
- 数据解析

- 什么是爬虫?

    网络爬虫（又被称为网页蜘蛛，网络机器人，在FOAF社区中间，更经常的称为网页追逐者），是一种按照一定的规则，自动地抓取万维网信息的程序或者脚本。另外一些不常使用的名字还有蚂蚁、自动索引、模拟程序或者蠕虫。

-  selenium是什么?

    Selenium是一个用于Web应用程序测试的工具。Selenium测试直接运行在浏览器中，就像真正的用户在操作一样。支持的浏览器包括IE（7, 8, 9, 10,11），Mozilla,Firefox，Safari，Google Chrome，Opera等。这个工具的主要功能包括：测试与浏览器的兼容性——测试你的应用程序看是否能够很好得工作在不同浏览器和操作系统之上。测试系统功能——创建回归测试检验软件功能和用户需求。支持自动录制动作和自动生成 .Net、Java、Perl等不同语言的测试脚本。

###### demo

```
# -*- coding=utf-8 -*-
from selenium import webdriver
import time


class DispatchSpider(object):
    def doSpider(self,url,username,password):
        print("人生苦短,我用Python")
        driver = webdriver.Firefox()
        driver.maximize_window()
        driver.get(url)
        # 等待2秒页面加载完毕
        time.sleep(2)
        input_user = driver.find_element_by_id('j_username')
        input_user.clear()
        input_user.send_keys(username) # 输入用户名
        time.sleep(2)
        password_rsainput = driver.find_element_by_id('j_password') # 输入密码
        password_rsainput.clear()
        password_rsainput.send_keys(password)
        time.sleep(2)
        driver.find_element_by_css_selector('a.easyui-linkbutton:nth-child(1)').click() # 点击登录按钮
        time.sleep(2)
        driver.find_element_by_css_selector('#tree1 > li:nth-child(7) > div:nth-child(1)').click() # 点击定时任务按钮
        time.sleep(2)
        data_tbody = driver.find_element_by_xpath('/html/body/div[3]/div[2]/div/div[2]/div/div/div[1]/div/div[2]/div[2]/div[2]/table/tbody')  #获取数据表格tbody
        data_trs = data_tbody.find_elements_by_tag_name('tr')  #获取数据表格tr
        for data_tr in data_trs:
            data_result = ''
            data_str = ''
            data_tds = data_tr.find_elements_by_tag_name('td')  #获取数据表格td
            for data_td in  data_tds:
                data_result = data_result+'---'+data_td.text
            print(data_result)  #输出定时任务


sp = DispatchSpider()
sp.doSpider("url","username","password")


```

> **java项目如何集成selenium进行自动登录数据获取?**

>  **扩展**
- selenium ui可记录自动化测试录像
- Scrapy,webmegic
- 正则表达式
