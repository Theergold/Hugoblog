---
title: 利用Cloudflare R2搭建自己的免费图床
date: 2022-10-16
slug: Cloudflare_R2_Free_Image_Hosting
image: https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/Cloudflare-R2-Storage-OG.jpg
categories:
    - 技术
---

最近闲的没事干刷 Cloudflare Dashboard 的时候发现 Cloudflare 有个叫 R2 的对象存储,好像还有点免费额度,那我的Blog正好也是丢在 Cloudflare Pages 上想着说顺手把图床也一并丢过来

# 0.Cloudflare R2

Cloudflare R2 是 Cloudflare 在21年9月推出的一项兼容S3的对象存储服务,每月可**免费**使用10GB储存空间 ,一百万次Class  A(大概就是写入)请求一百万次Class B请求(大概就是读取)一千万次

并且在不知道什么时候,这项曾经只开放给Workers的服务可以直接外链请求了,会生成一个 `https://pub-****.r2.dev` 的二级域名提供给外部访问(当然你也可以绑定自己的域名)

# 1.准备工作

那么在正式开始之前,你需要提前准备以下东西:
一个 Cloudflare 账号
一张拥有 CCV 的 Visa/Mastercard/AMEX 银行卡

# 2.搭建 Cloudflare R2

然后在 Cloudflare Dashboard 里点开 [R2](https://www.cloudflare.com/zh-cn/products/r2/) 页面

开始并绑定自己的银行卡和账单地址,之后进入 R2 DashBoard 页面

点击左上角的创建储存桶

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/3WghB0AhTd.png)

输入储存桶的名字,并点击设置

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/EQ1yHGjXfq.png)

找到 `存储桶访问` - `公开访问` 点击后面的允许访问

这时候就会生成一个 `https://pub-****.r2.dev` 的二级域名,可以尝试点击`对象`并手动上传文件然后访问 https://pub-****.r2.dev/文件名.png 试试看是否能访问,如果可以的话那么就算搭好图床了.

# 3.使用 ShareX 上传文件

由于通过上面的步骤,我们的图床时搭建好了,但是通过传统的方法向 Cloudflare R2 上传图片太麻烦了,这里我们推荐使用一个开源图床工具 [ShareX](https://getsharex.com/) 来作为我们的图片上传工具

我们通过 Cloudflare R2 兼容的 S3 API 来链接到 Cloudflare R2 ,要使用这个 API 我们先要获得 R2 API Token

首先打开 R2 Dashboard 点击右上角的`管理 R2 API 令牌` - `创建API令牌`

修改权限为`编辑`

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/xleWHZNaiz.png)

然后点击 `创建API令牌` , 记下 `访问密钥 ID`和 `机密访问密钥`

然后打开 ShareX , 选择 `目标` - `上传目标设置` 之后下拉找到 `Amazon S3`

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/yiRv6e8vag.png)

在 `访问密钥 ID` 处填写前面的 `访问密钥 ID` 

在 `密钥` 处填写前面的 `机密访问密钥`

第一个节点留空

第二个节点填写`你的账户ID.r2.cloudflarestorage.com` , 账户ID在 R2 DashBoard 页面获取 , 后面的区域填写 `auto`

储存桶名称填写自己设置的储存桶

上传路径自己设置

选择使用自定义域,填入之前的 `https://pub-****.r2.dev` 二级域名

然后取消选择 `在文件上设置公开 ACL`

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/vHeJM2J7aE.png)

然后退出到主页面 , 点击 `目标` - `图片上传` - `文件上传` - `Amazon S3` 完成上传目标设置之后就可以使用 ShareX 上传图片到 Cloudflare R2 了, 上传完成的链接会自动复制到剪贴板里面

![](https://pub-0ae159ad201e408fbc67e31384002f68.r2.dev/2022/Ve2QGBCIHd.png)
