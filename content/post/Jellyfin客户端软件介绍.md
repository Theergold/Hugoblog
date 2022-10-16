---
title: Jellyfin客户端软件介绍
date: 2022-01-29
slug: Jellyfin_clients
image: https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/jpg.jpg
categories:
    - 影音
---

> 客户端来自:https://jellyfin.org/clients/

# 桌面端:
## Jellyfin for Kodi : Kodi + Jellyfin 插件
### 优点:

- 全平台都可以用(特别是在TV端)

- 适合手柄/遥控器操作

- KODI本地解码效果好

### 缺点:

- Kodi只会把内容分为电影/电视节目/音乐三大类,想访问不同媒体库需要进入插件页面

- 无法查看演员列表/演员信息

- 需要时间进行同步

## Jellyfin Media Player
### 优点:

- 可以本地解码视频/字幕

- 基于嵌入式MPV

- 可以体验到Jellyfin Web同款UI
### 缺点:

- 就是一WebUI+嵌入式MPV,还不是用MPV的原生UI
## Jellyfin MPV Shim
### 优点:

- 直接调用MPV来解码,可以用MadVR

- 相比起复制直链URL可以同步数据和自动加载字幕
### 缺点:

- MPV界面难用
- 操作逻辑比较奇怪,需要在本地后台登录之后在Web端远程推送播放

## Videotape

### 优点:

- UWP原生应用,Windows Pad用起来舒服
- 解码用起来也不错

### 缺点:

- 要用傻逼MS Store下载算不算缺点?
- 会给你绑定上所有的字幕文件
- 如果服务器IP换了得快手快脚删除掉原来的地址,不然开始链接之后会直接卡死

# 移动端:
## Jellyfin Android
### 优点:

- 可以调用外部播放器和应用自带一个本地播放器

- 可以下载视频
### 缺点:

- UI就Web套壳
## Jellyfin Android TV
   优点:

- UI是原生UI

- 可以用媒体库分类(隔壁Kodi只有两大类
### 缺点:

- 本地解码难用

- 字幕加载会出问题

## Jellyfin IOS
这个纯纯套壳,别用,隔壁 Infuse 不香吗?

## Infuse
IOS下免费能用的客户端,能本地解码能正确加载字幕

但是首页还是分成电影电视两大类,没法加载电影电视以外的内容,高级服务贵,不买Pro没法看4K,还有就是媒体库加载速度稍微有点慢

## Gelli
音乐客户端,个人觉得不如隔壁 Finamp 好用

## Finamp
能用,反正就一听歌的,能串流高码率,Android/IOS双平台都能用

## MrMC
没钱

## Sailfin
没有Sailfish OS设备
