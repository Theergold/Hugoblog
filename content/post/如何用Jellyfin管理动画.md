---
title: 如何用Jellyfin管理动画
date: 2022-02-04
slug: Jellyfin_Anime
image: https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/p0KElsKRHX.png
categories:
    - Anime
    - 影音
---

用Jellyfin管理日本动画是一个需要一定技巧才能完美运行的东西,如果啥都不做在网上随便下一个RIP然后丢进Jellyfin就会发生这样的"惨剧"

![image-20220204005543624](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/photo_2022-02-04_01-55-01.jpg)

# 确认自己的网络情况

如果我们想在Jellyfin里面看到好看的海报墙,演员图片,影片资讯那些东西,我们还是需要从互联网上获取数据的,Jellyfin自带 , [The Movie Database (TMDB)](https://www.themoviedb.org/?language=zh-CN) , [TVDB](https://thetvdb.com/) , 这两个数据源,并且个人建议再安装[Fanart插件](https://github.com/jellyfin/jellyfin-plugin-fanart)来支持获取[Fanart.tv](https://fanart.tv/)数据

之后就要确认自己的网络是否能连上这两个网站,一般来说这些网站在中国大陆地区都有或多或少的访问困难,一般情况来说都是DNS劫持的问题,自己添加一条Hosts解析就好了

> ```text
> 13.224.161.90 api.themoviedb.org
> 104.16.61.155 image.themoviedb.org
> 13.35.67.86 api.themoviedb.org
> 54.192.151.79 www.themoviedb.org
> ```

# 确定自己下载了啥

我们以这部VCB-Studio的冰菓为例,除了我们要的动画本体和字幕,还有CDs,SPs,Scans三个文件夹和Fonts.zip,以及一个关于WebP的txt文档,如果你现在Jellyfin里面呈现出最完美的效果,CDs和Scans肯定是不需要的,因为没有地方给你展示这些东西(当然你丢去别的地方用Jellyfin别的模块展示我管不着),然后SPs需要选择性删除,另外两个文件删不删随你,这两个倒是没啥影响

# 从数据源确定数据

很多人都是随便丢进去就完事了的类型,但是我是建议至少要去数据源瞅瞅,能避免很多问题,我主要用[The Movie Database (TMDB)](https://www.themoviedb.org/?language=zh-CN) 这个数据源,打开[冰菓](https://www.themoviedb.org/tv/65329)的页面,首先先浏览一下内容是否完整(不完整可以注册个账号自己添加捏),然后直奔季列表,确定一下自己下载的内容哪些是属于[特别篇](https://www.themoviedb.org/tv/65329/season/0) 的,我们可以看到11.5集是被分入特别篇里面的,所以我们需要吧11.5级单列出来

# 改名

是的,如果你想用Jellyfin就乖乖听人家话把文件名改成人家想要的样子的样子,这里是官方的[命名规则](https://docs.jellyfin.org/general/server/media/shows.html),要是闲的没事干能去翻一翻

简单来说就是需要改成"SxxExx",然后数据源里面分列出来的特别篇要命名成"S00Exx"

# 最后一些强迫症需要动一动的地方

比如我习惯图片都是日文的,所以需要后面手动动一动,还有就是软字幕,Jellyfin是会把xxxx.zh.ass中间夹着的zh识别成基于[ISO639-2]([jellyfin/iso6392.txt at 45ceba7ad152de85956af51272c53c29cbbd5a70 · jellyfin/jellyfin (github.com)](https://github.com/jellyfin/jellyfin/blob/45ceba7ad152de85956af51272c53c29cbbd5a70/Emby.Server.Implementations/Localization/iso6392.txt))的语言,所以对于中文来说是没有简繁之分的,所以简单一点的方法就是改成中文让它没办法识别,或者用MKV打包进去

顺便也逼逼一点我对于哪些"全自动"操作的吐槽,至少在我看来要实现全自动操作就是用10倍调试的成本获得80分的效果...那我宁可手动动一动来获得98分的效果(你问我两分扣在哪?那自然是演员名字不是中文/日文的,但是我瞅了瞅TMDB好像也没啥办法改过来)



> 所以我特么瞎鸡巴写了一大通超简单两句话就能解释清楚并且网上同类文章超多的内容,可能所谓的"个人Blog"就是这样子的浆糊味吧
>
> SP1:从这篇文章开头的时候开始下的冰菓到现在刚刚下完
