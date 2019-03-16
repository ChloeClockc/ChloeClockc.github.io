---
layout: post
title: "使用Jekyll和github搭建博客遇到的一些问题"
subtitle: "Jekyll and github building blog problem"
author: "ChloeClockc"
header-img: "img/post-bg-desk.jpg"
header-mask: 0.4
tags:
  - Jekyll
  - blog
---


## 起源

首先，最近比较闲，也在复习java的知识和写排序算法等小demo，就想着把这些记录下来。之前也有在csdn写，但是总觉着有个自己的博客比较cool。自建域名的话还得买域名，比较麻烦，所以就用github的io域名建博客了。基本上参照[柏荧大大的这篇文章](https://www.jianshu.com/p/e68fba58f75c)进行搭建的,可以说写的非常详细了，在此非常感谢！

## 修改CNAME

因为之前接触github的比较少，所以遇到的几个问题可能属于比较小白的。不过鉴于费的时间挺长，还是记下来吧。首先我是从[github]([github](https://github.com/qiubaiying/qiubaiying.github.io))上直接fork了柏荧的项目到我仓库，这时候出现了第一个问题，因为他博客不是用的io域名，而是自己的域名，所以他的项目里CNAME这项是有值的，fork时候这项也过来了，但是因为不能和他的域名重复，所以这边会提交报错。后来我把这个文件里内容删除后就好了。这个其实也会导致访问自己域名时候跳转的还是原博客。

## 修改_config.yml

那篇博客基本把要修改的地方都说了，其实还包括博客右上角的about需要修改，也就是说还要改index.xml，about.xml等，其他的想改也可以，重点提这个是因为这里有原作者的信息在这，你自己博客出现别人信息再怎么说也不太妙吧。

## 网页背景图片修改和刷新机制

除了图片以外，这里还有一个坑，就是在_config.yml，是有description:的，很容易让人以为是网页blog下面那一行字，其实不是的，真正的是在index里的description。

![]({{https://chloeclockc.github.io/}}\assets\1552664371995.png)

![]({{https://chloeclockc.github.io/}}\assets\config.jpg)

![]({{https://chloeclockc.github.io/}}\assets\index.jpg)

这些修改之后，push到github上，是需要一段时间，博客才会有反馈效果出来的。即使ctrl F5刷新也需要时间。

然后说图片修改，我是直接在git拉下来的本地工程文件夹里修改头图的，也就是post-bg-desk.jpg（这个_config.yml里面有写）。但是改完之后push到git发现，刷新后没有生效，还是之前默认那个图。后面尝试把这个名字改了，换了个别的图片，然后发现博客刷新之后首页图没有了。仔细找了下发现，我本地工程里面这个图是红色的，在仓库一看，果然没有传上去这个图。原来是我删除后添加这个图之后，没有在文件和目录上add，然后push时候没有把这个加上去。归根结底因为往git上push代码操作的太少吧，很多不熟练，以为传上去了结果没有，浪费了不少时间。

## 总结

虽然这次搭建博客，没有用自建域名，也没有自己去写后台，用的别人模板改的。但是还是暴露出了使用git不熟的短板，今后要多往git上写代码，加强自己的编程能力。