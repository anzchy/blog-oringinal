---
title: 重建了博客网站
date: 2024-04-19 23:56:25
tags:
---

根据 github 上记录上次建站是 7 年前，今天终于重启了建站，这几天下班后专门搭建网站：基于 hexo 博客+ butterfly，部署在 Vercel 第三方平台上，尝试了好几次，终于部署成功了，这里记录下，作为博客的第一篇文章。

# 1、建站记录

这次建站初始步骤借用了 `GPT-4`，写了如下 prompt 辅助我完成操作：

>你是一个非常厉害的网页设计师，请问如何用 hexo 建立一个博客，我本地的是 Mac Pro，搭载 MacOS 14.2.1 的版本，请按照步骤给出搭建具体的过程，步骤包括 ：
>
>1、本地 hexo init生成本地 blog 文件；
>
>2、更换 hexo 主题为[Butterfly主题](https://github.com/jerryc127/hexo-theme-butterfly) ；
>
>3、创建 SSH 私钥和公钥，从而可以每次不用输入密码就可以 pull repo；
>
>4、然后用 hexo deploy从本地将 hexo博客的源文件（通常是 markdown ，config.yml 等文件）pull 到 github 上的到xxx.github.io，博客的静态网页文件(通过 hexo generate 生成的文件，在本地博客根目录 pulic 文件夹）不上传；
>
>5、通过 github pages 来生成网页文件，但是不能影响 repo 上的源文件，来设定域名。
>
>6、以后每次写文章，更新博客，怎么操作。



以下是具体本地 terminal 的命令行，只记录我这边的输入命令，如果出现了 bug，将 bug 复制给 GPT-4，让其帮忙纠错。

```bash
➜ cd '/Users/xxxx/Documents/01_Coding/blog/'
➜ hexo init anzchy.github.io
➜ cd anzchy.github.io
➜ npm install

#此处参考官方butterfly教程，注意博客根目录下_config.yml 的 theme：要更换，还有根目录#要创建_config_butterfly.yml
➜ git clone -b master https://github.com/jerryc127/hexo-theme-butterfly.git themes/butterfly
➜ npm install hexo-renderer-pug hexo-renderer-stylus --save #别忘了安装

#用于 hexo d，记得部署前更改博客根目录下_config.yml的 deploy 选项，添加自己的 #github.io 地址和 branch 地址
➜ npm install hexo-deployer-git --save
➜ hexo clean
➜ hexo g 
➜ hexo server
➜ hexo deploy #此处是将生成的静态网页（public文件夹下)上传到 github.io 的库中

#下面是将对应的非网页文件，多是 md 格式文件，保存到另一个 repo 中，下面两命令第一次用 #git 时使用
➜ git init
➜ git remote add origin git@github.com:anzchy/blog-original.git

#下面的命令，之后每次更改本地电脑的博客文件，都要执行一遍
➜ git add .
➜ git commit -m "Initial commit of Hexo blog source files"
➜ git push -u origin main 

```

# 2、容易犯错误的点

1、更改主题，要把主题文件夹下的 config.yml 复制出来，放到根目录下，名字通常改成_config.themename.yml，譬如我的目录，具体要看 theme 对应的 使用说明书。

![image-20240420000907299](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/image-20240420000907299.png)

2、换主题的话，最好第一次建站时就能配置好，否则之后无论如何配置，都会有各种各样的 bug，本地主题显示更新了，但是部署到网页，发现没有加载主题。

3、看官方的 hexo.io 和 git相关 docs 很重要，后面要补上。

4、绑定自定义域名要在三个地方设置好，第一个地方，github 自己的博客代码库 myname.github.io的 setting 中，设置`Deploy from a branch`，![image-20240420090339809](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/image-20240420090339809.png)

在仓库的根目录要添加 `cname`，方法之一是：可以在本地博客根目录的 `/source` 文件夹手动创建一个 cname 文件（不带任何后缀），其中填上你自己的域名即可。当然，Vercel 上托管时，vercel 也可以给你创建 cname 的 commit。

![image-20240420090856086](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/image-20240420090856086.png)

第二个地方，Vercel 代码托管平台上，新建 project，不需要选任何 framework，直接默认，重要的是 domain 设置。

![image-20240420085939020](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/image-20240420085939020.png)

第三个地方，在我的腾讯云解析中，根据 vercel 第三方托管网站的DNS 解析指导，添加 CNAME和 A 记录。

![image-20240420090107866](https://picbox-1313243162.cos.ap-nanjing.myqcloud.com/image-20240420090107866.png)

# 3、后续计划



之后还要尝试着：

1、继续添加文章到博客，丰富博客内容；

2、了解 theme 的 DIY，更改下 theme 的一些设置；

3、写了博客后，自动更新给微信公众号，我看到已经有人开源了代码，后面尝试部署下。

