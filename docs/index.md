# 0.未分类
* 所有的文件都保存在`docs/`的目录中
* 图片保存在文章的上一级目录，命名为`img`
* 文章保存在类别目录中(如关于GNURadio的保存在GNURadio的文件夹中)

# 1.文件结构
---
* docs
    * index.md(现在正看到的页面)
    * 大类(如SDR,IT,ANT,etc.)
        * 小类(GNURadio,Linux,Mkdocs,etc)   
            * `index_xxxx.md` //此处链接指向`posts`中的具体文章
            * `img/`
                * `xxxx/` //每一篇post创建一个单独文件夹存放对应的图片
            * `posts/` //文章写在这里

# 2.SoP
---
* 整个`CONTENT/`文件夹拖入`atom`
* 运行mkdocs serve，打开浏览器进入页面
* 根据文件结构，创建所有需要的文件夹和文件
* **（如果是文章属于新创建的小类）修改`mkdocs.yml`中的nav，指向小类中的`index_xxxx.md`** //*这样在浏览器里才会出现该小类目录*
* 修改`index_xxxx.md`，添加一条新的内容链接，指向`posts/`中准备要写的文章
* 在`posts/`中写文章，图片保存在其对应的`../img/xxx/`文件夹当中

# 3.模版
---
* index_xxxx.md
~~~
# Table of Content

* [学习GNURadio系列2-第一个项目](posts/学习GNURadio系列2-第一个项目.md)

~~~

* post当中的img路径

~~~
![x](../img/xxxx/x.jpeg)
#post所在文件夹的上一层目录->img/->xxxx/具体文件.jpeg
~~~

* post当中的结尾

~~~
---
欢迎关注我

我的微信公众号：LLY业余无线电那些事

我的知乎业余无线电专栏： https://www.zhihu.com/column/c_1392777577560424448

![n](../../../../n.png)
~~~
