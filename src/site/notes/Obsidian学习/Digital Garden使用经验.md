---
{"dg-publish":true,"permalink":"/Obsidian学习/Digital Garden使用经验/","dgPassFrontmatter":true}
---


## 基本知识
一、digital garden是什么？
从本质上来说，digital garden是obsidian的一个插件，通过这个插件，我们可以将我们的obsidian库形成一个网站并发布。

二、如何使用digital garden插件？
你需要这些条件：
1. 科学上网工具，主要涉及插件的下载以及GitHub相关；
2. 一个GitHub账号
3. 一个域名
关于域名，可以一些静态网站部署工具所提供的默认域名，比如 `https://自己随便取.github.io` 或者 `https://自己随便取.netlify.app` 等等。这里推荐netlify。
[Scale & Ship Faster with a Composable Web Architecture | Netlify](https://www.netlify.com/)
有了这些前期准备以后，我们就可以开始使用该插件了！

具体教程链接：[[主页#^2aa95b\|主页#^2aa95b]]
https://www.bilibili.com/video/BV1HF411173m/?spm_id_from=333.1007.top_right_bar_window_history.content.click

## 使用经验
一、有图片的笔记怎么办？2023年12月5日
根据我的经验，在发布的时候，如果图片的引用格式是obsidian的默认格式的话
比如：\![学期课程/images/Pasted image 20231117223539.png](/img/user/%E5%AD%A6%E6%9C%9F%E8%AF%BE%E7%A8%8B/images/Pasted%20image%2020231117223539.png)
这样在发布时，会自动将图片也上传至GitHub的仓库中并调用。我们应该避免使用绝对路径
如果我们想修改图片的大小，标题，亲测在obsidian中使用html语法没有作用。我们可以去到GitHub的仓库中，找到我们要修改的文件。
文件位置一般在：GitHub-项目名称（我的就是digitalgardenforJunwenZhou）-src-site-note里面，在这里对我们的markdown文件进行修改（这里可以使用HTML语法）

二：我们在obsidian中对已经发布的笔记进行删除、位置移动等操作时，会出现一个问题：网页上会保留原来的文件组织模式。
比如：我把math文件夹移动到epidemiology文件夹下了，这时，我们的网页上就会出现两个math文件夹，一个在原来的位置，一个在epidemiology文件夹下。这时我们需要删除原来的那个文件夹。但是我们在GitHub中是不能删除文件or文件夹的，这时我们需要通过Git来操作。

第一步：安装Git并与Github建立连接
可以参考这位博主的教程：[Github——git本地仓库建立与远程连接（最详细清晰版本！附简化步骤与常见错误）_github本地仓库创建-CSDN博客](https://blog.csdn.net/qq_29493173/article/details/113094143)
我们一般会在这一步出现问题
```git
$ ssh -T git@github.com
```

有可能会报错：
我参考的是这篇教程中的第一种方法解决的
[坑：ssh: connect to host github.com port 22: Connection refused - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/521340971)
我了解了一下，可能是在建立连接的过程中，使用了科学上网工具，所以建议全程不要使用科学上网工具。
或者报错时先输入命令：
```
$ ping github.com
```
看能不能ping上GitHub，如果能（显示类似于以下的内容时）
```
Pinging github.com [20.205.243.166] with 32 bytes of data:
Reply from 20.205.243.166: bytes=32 time=125ms TTL=105
Reply from 20.205.243.166: bytes=32 time=125ms TTL=105
Reply from 20.205.243.166: bytes=32 time=125ms TTL=105
Reply from 20.205.243.166: bytes=32 time=126ms TTL=105

Ping statistics for 20.205.243.166:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 125ms, Maximum = 126ms, Average = 125ms

```
那么可以多尝试几次$ ssh -T git\@github.com命令
或者简单粗暴，重启电脑试试，实在不行就用上面的教程中提到的方法

第二步：删除文件/文件夹：
参考下面这篇教程：
[Git 删除 GitHub仓库的文件——详细操作_github怎么删除文件-CSDN博客](https://blog.csdn.net/Seciss/article/details/120957382)
下面就是我删除文件的一个例子：
```scss
zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ dir
Principles\ of\ Biostatistics.md  卫生统计学
math                              卫生统计学.md
modelling_infectious_diseases     卫生统计学学习.md

zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ git rm 卫生统计学.md
rm 'src/site/notes/Epidemiology_and_Health_Statistics/卫生统计学.md'

zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ git rm 卫生统计学学习.md
rm 'src/site/notes/Epidemiology_and_Health_Statistics/卫生统计学学习.md'

zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ git rm Principles\ of\ Biostatistics.md
rm 'src/site/notes/Epidemiology_and_Health_Statistics/Principles of Biostatistics.md'

zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ git commit -m "重复"
[main b565232] 重复
 3 files changed, 311 deletions(-)
 delete mode 100644 src/site/notes/Epidemiology_and_Health_Statistics/Principles of Biostatistics.md
 delete mode 100644 "src/site/notes/Epidemiology_and_Health_Statistics/\345\215\253\347\224\237\347\273\237\350\256\241\345\255\246.md"
 delete mode 100644 "src/site/notes/Epidemiology_and_Health_Statistics/\345\215\253\347\224\237\347\273\237\350\256\241\345\255\246\345\255\246\344\271\240.md"

zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ git checkout
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

zhouj@zhou MINGW64 ~/Desktop/GitHub/digitalgardenforJunwenZhou/src/site/notes/Epidemiology_and_Health_Statistics (main)
$ git push
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 8 threads
Compressing objects: 100% (6/6), done.
Writing objects: 100% (6/6), 487 bytes | 487.00 KiB/s, done.
Total 6 (delta 4), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (4/4), completed with 4 local objects.
To https://github.com/Zhoujuanwang/digitalgardenforJunwenZhou
   2659601..b565232  main -> main

```
