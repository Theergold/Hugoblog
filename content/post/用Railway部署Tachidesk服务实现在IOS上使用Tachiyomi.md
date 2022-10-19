---
title: 用Railway部署Tachidesk服务实现在IOS上使用Tachiyomi
date: 2022-10-18
slug: Use_Railway_build_Tachidesk
image: https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/cov.jpg
categories:
    - 技术
    - 漫画
---

# 0. Tachidesk

## 1.什么是Tachidesk

众所周知 Android 上有一款非常优秀的开源在线漫画阅读软件 **Tachiyomi** 可以通过插件的形式方便的订阅并聚合漫画源

而 Tachidesk 是一个免费,开源的漫画阅读器服务器,并且兼容 Tachiyomi 的各种插件,并且致力于可以实现多平台使用

## 2.为什么要使用Tachidesk

由于 Tachidesk 是一款可以 Self-host 的服务,所以可以在 Tachiyomi 并不支持的平台使用 Tachiyomi 的插件(比如**IOS**)

# 1. 为什么要用Railway

Tachidesk 作为一款 JAVA 编写的软件自然拥有全平台部署的能力,但是由于"某些网络原因",在中国大陆地区部署的 Tachidesk 会出现各种网络问题,所以将 Tachidesk 部署在中国大陆以外的服务器可以解决各种网络问题

而 Railway 作为一款方便快捷的 PaaS 平台,并且提供了 5 刀的免费额度所以成为了我这次的选择

# 2. 开始部署

Railway 支持 使用读取 Github 仓库里的 Dockerfile 文件自动部署 Docker 任务

所以我们先 Fork [docker-tachidesk](https://github.com/Suwayomi/docker-tachidesk) 项目

然后打开 Railway 绑定自己的 Github , 创建一个 `New Project` , 添加 `Github Repo` 选择前面Fork的 docker-tachidesk 项目

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/Oat392lF7o.png)

之后打开 `Variables` 添加一个变量 `PORT` = 4567

然后再选择`Settings` - `Environment` - `Domains` 获取或者绑定自己的域名,等待Railway重新编译之后打开域名就可以看到 Tachidesk 主页了

# 3.**[Tachidesk-Sorayomi](https://github.com/Suwayomi/Tachidesk-Sorayomi)**

Sorayomi 是一款基于 Flutter 的 Tachidesk 客户端,基于 Flutter的多平台特性使得 Sorayomi 可以运行在 Windows/MacOS/Linux Desktop/Web Server/Android/IOS的环境下

![最新版的Releases列表](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/w4L6F3TlRf.png)

下面以Windows版本为例(你把IPA安装到IOS设备上之后也是一样的)介绍怎么配置客户端

1. 先打开Sorayomi
2. 点击 `More` - `Server URL`
3. 将前面的网址填写在 `Server URL` 选项内

然后此时打开 `Browse` - `Extensions` 看到 Tachiyomi 官方库的插件了

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/MPDmP3ctLW.png)

然后点击右上角的按钮出现 `languages` 面板 往下翻打开中文的选择,这时才能看到中文插件

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/5OKkPw4N0A.png)

安装完插件之后点击 `Sources` 页面,再点击右上角的搜索按钮就可以搜索漫画了

# 相关链接

[Tachidesk-Server](https://github.com/Suwayomi/Tachidesk-Server)
[Tachiyomi](https://tachiyomi.org/)
[Tachidesk-Sorayomi](https://github.com/Suwayomi/Tachidesk-Sorayomi)
