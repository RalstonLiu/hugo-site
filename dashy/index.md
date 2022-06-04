# Dashy


<!--more-->

## 前言

之前咕咕也折腾过几个面板程序，比如像[Heimdall](https://heimdall.site/)、[Flare](https://soulteary.com/2022/01/19/flare-production-record-application-frontend-and-backend-performance-optimization.html) 

![image-20220602174601025](https://img.laoda.de/i/2022/06/02/svjovg-0.webp)

![Flare 的向导小工具](https://img.laoda.de/i/2022/06/02/suci2u-0.webp)





但是都是用了一段时间就没用了，原因是自己发现了一个宝藏的Chrome插件——[iTab](https://itab.link/install/chrome.html)，这段时间正好也是疫情在家，基本上很少在手机上浏览网页，iTab对我来说就足够用了。

![image-20220602223358087](https://img.laoda.de/i/2022/06/02/10y2r97-0.webp)



不过，就在前俩天，发现一个面板程序，惊艳到了我（放一张我自己搭建的图）：

![image-20220602175035525](https://img.laoda.de/i/2022/06/02/sy4r7q-0.webp)

![image-20220602175109103](https://img.laoda.de/i/2022/06/02/sykgsx-0.webp)



看起来非常炫酷，今天就和大家分享一下。

## 1. 介绍

这个面板的名字叫做——Dashy，是一个功能非常非常强大的面板，而且如果你查看他的文档，会发现写的非常非常详细。

### 1.1 特点

咕咕这边简单在网上~~抄~~搜集了一些特点，供大家参考：

- 🚦 对您的每个应用程序/链接进行实时状态监测
- 📊 使用小工具来显示来自自我托管服务的信息和动态内容
- 🔎 按名称、域名或标签进行即时搜索 + 可定制的热键和键盘快捷方式
- 🎨 许多内置的颜色主题，带有UI颜色编辑器并支持自定义CSS
- 🧸 许多图标选项 - Font-Awesome、homelab图标、自动获取Favicon、图像、表情符号等。
- 💂 可选的认证，包括多用户访问、可配置的权限和SSO支持
- 🌎 多语言支持，有10多种人工翻译的语言，还有更多的语言正在开发中
- ☁ 可选的、加密的、免费的异地云备份和恢复功能
- 💼 工作区视图，可同时在多个应用程序之间轻松切换
- 🛩️ 一个最小的视图，可作为快速加载的浏览器起始页使用
- 🖱️ 选择应用程序的启动方式：新标签、同一标签、剪贴板、弹出式模式或在工作区视图中打开
- 📏️可定制布局、尺寸、文本、组件可见性、排序顺序、行为等。
- 🖼️全屏背景图片、自定义导航栏链接、HTML页脚、标题等选项。
- 🚀️容易用Docker设置，或在裸机上，或用一键云部署
- ⚙️简单的基于YAML的单文件配置，以及通过UI配置应用程序的选项。
- ✨ 正在积极开发，定期添加改进和新功能
- ᾐ极小的软件包，完全响应的UI，和PWA的基本离线访问。
- 🆓 100%免费和开放源代码
- 🔐 高度重视隐私问题
- 🌈 还有更多......



关键，他还能添加很多小的组件，比如配合`glances`，监控你系统运行情况，像咕咕这样：

![image-20220602180211100](https://img.laoda.de/i/2022/06/02/tsy3u0-0.webp)

总之，非常适合搭建在自己的Nas上，作为一个“主控”面板，当然，咕咕没有搭建Nas，我们就在VPS上来动手搞一个玩玩吧～

## 2. 项目展示

咕咕的Demo：http://dashy.ml2u.ml/

GitHub原项目地址（感谢作者的付出）：[https://github.com/Lissy93/dashy](https://github.com/Lissy93/dashy)（2.8k star）

官网地址：https://dashy.to/

Demo地址：https://demo.dashy.to/

文档地址：https://dashy.to/docs/





直接丢几个图片：

![image-20220602180347196](https://img.laoda.de/i/2022/06/02/ttrftt-0.webp)

![image-20220602180423796](https://img.laoda.de/i/2022/06/02/tu7pnl-0.webp)



## 3. 搭建环境

- 服务器：~~腾讯香港轻量应用服务器24元/月VPS一台~~展示用的服务器是[Netcup](https://netcup-sonderangebote.de/)特价款，本期搭建用的是[Vultr](https://loll.cc/vultr)的服务器，按小时计费，可随时销毁（最好是选**非大陆的服务器**）（[腾讯轻量购买链接](https://loll.cc/tx)）[Hetzner注册免费得25欧试用金有效期一个月](https://loll.cc/hz)
- 系统：Debian 10（[DD脚本](https://blog.laoda.de/archives/useful-script#dd%E7%9B%B8%E5%85%B3) 非必需DD用原来的系统也OK）
- 域名一枚，并做好解析到服务器上（[域名购买、域名解析](https://blog.laoda.de/archives/namesilo) [视频教程](https://www.bilibili.com/video/BV1Sy4y1k7kZ/)）
- 安装好Docker、Docker-compose（[相关脚本](https://blog.laoda.de/archives/hello-docker#5%E5%AE%89%E8%A3%85dockerdocker-compose)）
- 【非必需】提前安装好宝塔面板海外版本aapanel，并安装好Nginx（[安装地址](https://forum.aapanel.com/d/9-aapanel-linux-panel-6812-installation-tutorial)）
- 【非必需本教程采用】安装好Nginx Proxy Manager（[相关教程](https://blog.laoda.de/archives/nginxproxymanager)）



> 注意：如果要配合`glances`搭建监控，建议VPS最好是`2核2G`以上配置，低配置实测无法运行！

## 4. 搭建视频

YouTube：

哔哩哔哩【高清版本可以点击去吐槽到B站观看】：<joe-bilibili bvid=""></joe-bilibili>

## 5. 搭建方式

### 5.1 搭建

服务器初始设置，参考

[**新买了一台服务器“必须”要做的6件小事**](https://blog.laoda.de/archives/vps-script)

[【Docker系列】不用宝塔面板，小白一样可以玩转VPS服务器！](https://blog.laoda.de/archives/hello-docker)


> 注意：VPS的内存如果过小，建议设置一下SWAP，一般为内存的1-1.5倍即可，可以让运行更流畅！

设置SWAP可以用脚本:

```bash
wget -O box.sh https://raw.githubusercontent.com/BlueSkyXN/SKY-BOX/main/box.sh && chmod +x box.sh && clear && ./box.sh
```

![image-20220528185512488](https://img.laoda.de/i/2022/05/28/uoikkd-0.webp)

选择`18`，然后输入你想要扩容的数值即可。

![image-20220528185604586](https://img.laoda.de/i/2022/05/28/up2dkf-0.webp)

```bash
sudo -i # 切换到root用户

apt update -y  # 升级packages

apt install wget curl sudo vim git  # Debian系统比较干净，安装常用的软件
```



创建一下安装的目录：

```bash
mkdir -p /root/data/docker_data/dashy/{icons,public}

cd /root/data/docker_data/dashy

nano docker-compose.yml
```



`docker-compose.yml`填入以下内容：

```bash
version: '3.3'
services:
    dashy:
        ports:
            - '8395:80'
        volumes:
            - '/root/data/docker_data/dashy/public/conf.yml:/app/public/conf.yml'
            - '/root/data/docker_data/dashy/icons:/app/public/item-icons/icons'
        container_name: dashy
        restart: unless-stopped
        image: 'lissy93/dashy:latest'
```



没问题的话，`ctrl+x`退出，按`y`保存，`enter`确认。

查看端口是否被占用，输入：

```bash
lsof -i:8395  #查看8395端口是否被占用，如果被占用，重新自定义一个端口
```

如果出现：

```bash
-bash: lsof: command not found
```

运行：

```bash
apt install lsof  #安装lsof
```

如果端口没有被占用，我们接着可以运行：

```bash
cd public/

nano conf.yml
```

粘贴如下官方Demo的内容：

```bash
---
# Page meta info, like heading, footer text and nav links
pageInfo:
  title: Dashy
  description: Welcome to your new dashboard!
  navLinks:
  - title: GitHub
    path: https://github.com/Lissy93/dashy
  - title: Documentation
    path: https://dashy.to/docs

# Optional app settings and configuration
appConfig:
  theme: colorful
  layout: auto
  iconSize: medium
  language: en
  auth:
    users:
      - user: your-preferred-username    # 改成自己的用户名
        hash: hash-of-a-password-you-choose-using-sha256-hashing  # cha256 哈希加密，地址用这个： https://emn178.github.io/online-tools/sha256.html
        type: admin
# Main content - An array of sections, each containing an array of items
sections:
- name: Getting Started
  icon: fas fa-rocket
  items:
  - title: Dashy Live
    description: Development a project management links for Dashy
    icon: https://i.ibb.co/qWWpD0v/astro-dab-128.png
    url: https://live.dashy.to/
    target: newtab
  - title: GitHub
    description: Source Code, Issues and Pull Requests
    url: https://github.com/lissy93/dashy
    icon: favicon
  - title: Docs
    description: Configuring & Usage Documentation
    provider: Dashy.to
    icon: far fa-book
    url: https://dashy.to/docs
  - title: Showcase
    description: See how others are using Dashy
    url: https://github.com/Lissy93/dashy/blob/master/docs/showcase.md
    icon: far fa-grin-hearts
  - title: Config Guide
    description: See full list of configuration options
    url: https://github.com/Lissy93/dashy/blob/master/docs/configuring.md
    icon: fas fa-wrench
  - title: Support
    description: Get help with Dashy, raise a bug, or get in contact
    url: https://github.com/Lissy93/dashy/blob/master/.github/SUPPORT.md
    icon: far fa-hands-helping
```

没问题的话，`ctrl+x`退出，按`y`保存，`enter`确认。



之后，我们：

```bash
cd /root/data/docker_data/dashy/icons

git clone https://github.com/walkxcode/dashboard-icons.git  # 下载icons，新版的好像系统自带，咕咕没有尝试，就先用这个了。

cd /root/data/docker_data/dashy

docker-compose up -d  
```



访问：`http:服务ip:8395` 即可。

> **注意：**
>
> 1、不知道服务器IP，可以直接在命令行输入：`curl ip.sb`，会显示当前服务器的IP。
>
> 2、遇到访问不了的情况，请在宝塔面板的防火墙和服务商的后台防火墙里打开对应端口。



### 5.2 更新



```bash
cp -r /root/data/docker_data/dashy /root/data/docker_data/dashy.archive  # 万事先备份，以防万一

cd /root/data/docker_data/dashy  # 进入docker-compose所在的文件夹

docker-compose pull    # 拉取最新的镜像

docker-compose up -d   # 重新更新当前镜像
```

利用Docker-compose搭建的应用，更新非常容易～



### 5.3 卸载

```bash
cd /root/data/docker_data/dashy  # 进入docker-compose所在的文件夹

docker-compose down    # 停止容器，此时不会删除映射到本地的数据

rm -rf /root/data/docker_data/dashy  # 完全删除映射到本地的数据
```



## 6. 反向代理



### 6.1 利用Nginx Proxy Manager



在添加反向代理之前，确保你已经完成了域名解析，不会的可以看这个：**域名一枚，并做好解析到服务器上**（[域名购买、域名解析](https://blog.laoda.de/archives/namesilo) [视频教程](https://www.bilibili.com/video/BV1Sy4y1k7kZ/)）



之后，登陆Nginx Proxy Manager（不会的看这个：**安装Nginx Proxy Manager**（[相关教程](https://blog.laoda.de/archives/nginxproxymanager)））

> **注意：**
>
> Nginx Proxy Manager（以下简称NPM）会用到`80`、`443`端口，所以本机不能占用（比如原来就有Nginx）



直接丢几张图：

<img src="https://img.laoda.de/i/2022/03/20/wenk4d.webp" style="zoom:33%;" />



<img src="https://img.laoda.de/i/2022/03/20/x2w60n.webp" style="zoom:33%;" />



<img src="https://img.laoda.de/i/2022/06/02/10zgq7g-0.webp" alt="image-20220602223632735" style="zoom:50%;" />



>  注意填写对应的`域名`和`端口`，按文章来的话，应该是`8395`



这边我们不打开SSL，然后就可以用域名来安装访问了。

## 7. 使用教程

### 7.1 安装和配置

见咕咕鸽的视频

> 注意：Dashy重启之后，大概需要`1-2分钟`才能激活，可以通过`docker logs dashy`查看日志情况。

### 7.2 安装服务器监控插件

### 7.2.0 几个问题（有解决的欢迎评论区留言）

咕咕折腾了很久，发现安装服务器监控会有几个问题：

- 打开SSL，监控数据无法读取
- 只能读取本机的数据，无法读取外部机器的数据



如果有小伙伴解决了，欢迎评论区留言交流！

#### 7.2.1 安装glances

![image-20220602212229824](https://img.laoda.de/i/2022/06/02/z3ohrw-0.webp)

![image-20220602213427835](https://img.laoda.de/i/2022/06/02/zasnnr-0.webp)

![image-20220602211921431](https://img.laoda.de/i/2022/06/02/z1qqc3-0.webp)

服务器监控插件里面调用的数据，其实是从glances里面获得的。

> Glances 是一个跨平台的、基于命令行的系统监控工具，由 Python 语言编写，使用 Python 的 **psutil** 库来抓取系统数据。可以监控 CPU、负载均衡、内存、网络设备、磁盘 I/O、进程和文件系统使用等。
>
> 
>
> 作者：rollingstarky
> 链接：https://www.jianshu.com/p/799e8ccbe15f
> 来源：简书
> 著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。



```bash
apt install python3 python3-pip -y 

pip3 install bottle 

pip3 install glances 
```



> Bottle是一个用于Python编程语言的WSGI微web框架。它被设计为快速、简单和轻量的，可以容易的和快速的开发web应用。它被作为一个单一文件模块发行，不依赖于其他的Python标准库。同一个模块可运行于Python 2.7和3.x。
>
> 来源：[维基百科](https://zh.wikipedia.org/zh-cn/Bottle)



这个时候，你直接输入

```bash
glances
```

就可以显示服务器系统信息了。

输入：

```bash
glances -w
```

就可以利用网页来打开。



不过，只要我们`ctrl + c`服务就停止了，所以我们需要给他弄成后台启动，写一个`service`

```bash
sudo nano /etc/systemd/system/glances.service    # 名字就叫 glances.service
```

输入下面这个（默认你是root用户）：

 ```bash
[Unit]
Description = Glances in Web Server Mode
After = network.target

[Service]
ExecStart = /usr/local/bin/glances  -w  -t  5

[Install]
WantedBy = multi-user.target
 ```



保存退出。

```bash
systemctl enable glances.service  # 开机自动启动glances

systemctl start glances.service  # 启动glances

systemctl status glances.service  # 查看glances状态

systemctl restart glances.service  # 重启glances
```



#### 7.2.2 安装监控插件



接下来，配置一下`conf.yml`文件，这边为了省事，贴一个咕咕自己的配置给大家参考，更多的配置可以看[文档](https://dashy.to/docs/widgets)：

```bash
appConfig:
  theme: dashy-docs
  layout: auto
  iconSize: medium
  language: cn
  auth:
    users:
      - user: Roy
        hash: 6477fd513dcd82a78866654f9d064e8fea54a9d95e65c95ce6aee0699bf0948c
        type: admin
      - user: gugu
        hash: 8b2d38b789e90bb18567c2be4abbd4295f461f6453dd0447a3bf248a75eb0ae7
        type: normal
    enableGuestAccess: true
pageInfo:
  title: GuGu's Dashboard
  description: 生命不息，折腾不止！咕～
  navLinks:
    - title: 咕咕的博客
      path: https://blog.laoda.de
      target: newtab
    - title: B站
      path: https://space.bilibili.com/19956596
      target: newtab
    - title: YouTube
      path: https://www.youtube.com/channel/UCJeNmdZBL8QahqCbzxj4l3Q
      target: newtab
    - title: Telegram群
      path: https://t.me/laodade
      target: newtab
    - title: 请喝咖啡
      path: https://blog.laoda.de/s/buy-me-a-coffee
      target: newtab
  footerText: 欢迎来找咕咕玩～
sections:
  - name: Memory Usage
    icon: fas fa-memory
    widgets:
      - type: gl-current-mem
        options:
          hostname: http://95.179.242.122:61208
        id: 0_1166_glcurrentmem
  - name: Getting Started
    icon: fas fa-rocket
    items:
      - title: Dashy Live
        description: Development a project management links for Dashy
        icon: https://i.ibb.co/qWWpD0v/astro-dab-128.png
        url: https://live.dashy.to/
        target: newtab
        id: 0_1481_dashylive
      - title: GitHub
        description: Source Code, Issues and Pull Requests
        url: https://github.com/lissy93/dashy
        icon: favicon
        id: 1_1481_github
      - title: Docs
        description: Configuring & Usage Documentation
        provider: Dashy.to
        icon: far fa-book
        url: https://dashy.to/docs
        id: 2_1481_docs
      - title: Showcase
        description: See how others are using Dashy
        url: https://github.com/Lissy93/dashy/blob/master/docs/showcase.md
        icon: far fa-grin-hearts
        id: 3_1481_showcase
      - title: Config Guide
        description: See full list of configuration options
        url: https://github.com/Lissy93/dashy/blob/master/docs/configuring.md
        icon: fas fa-wrench
        id: 4_1481_configguide
      - title: Support
        description: Get help with Dashy, raise a bug, or get in contact
        url: https://github.com/Lissy93/dashy/blob/master/.github/SUPPORT.md
        icon: far fa-hands-helping
        id: 5_1481_support
  - name: 服务器相关
    icon: fas fa-server
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: false
      hideForGuests: false
    items:
      - title: Nginx Proxy Manager
        description: 反向代理神器
        icon: icons/dashboard-icons/png/nginxproxymanager.png
        url: https://la-npm.laoda.de/
        target: newtab
        statusCheck: true
        id: 0_120961_nginxproxymanager
      - title: Portainer
        description: 容器管理神器
        icon: icons/dashboard-icons/png/portainer.png
        url: https://portainer.laoda.de/
        target: newtab
        statusCheck: true
        id: 1_120961_portainer
      - title: qBittorrent
        description: 下载神器
        icon: icons/dashboard-icons/png/qbittorrent.png
        url: http://193.29.62.197:8081/
        target: newtab
        statusCheck: true
        id: 2_120961_qbittorrent
      - title: UptimeKuma
        icon: icons/dashboard-icons/png/uptime-kuma.png
        url: https://uptime.laoda.de/
        target: newtab
        statusCheck: true
        id: 3_120961_uptimekuma
  - name: CPU Usage
    icon: fas fa-tachometer
    displayData:
      rows: 2
    widgets:
      - type: gl-current-cpu
        options:
          hostname: http://95.179.242.122:61208
        id: 0_765_glcurrentcpu
      - type: gl-current-cores
        options:
          hostname: http://95.179.242.122:61208
        id: 1_765_glcurrentcores
  - name: 效率工具
    icon: fas fa-battery-full
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: false
      hideForGuests: false
    items:
      - title: Tinytiny RSS
        description: RSS阅读
        icon: icons/dashboard-icons/png/tinytinyrss.png
        url: ''
        target: newtab
        statusCheck: true
        id: 0_100395_tinytinyrss
      - title: Yourls
        icon: icons/dashboard-icons/png/yourls.png
        url: ''
        target: newtab
        statusCheck: true
        id: 1_100395_yourls
      - title: EasyImages
        icon: fas fa-image
        url: ''
        target: newtab
        statusCheck: true
        id: 2_100395_easyimages
      - title: Joplin Server
        icon: icons/dashboard-icons/png/joplin.png
        url: ''
        target: newtab
        statusCheck: true
        id: 3_100395_joplinserver
      - title: Vaultwarden
        icon: icons/dashboard-icons/png/bitwarden.png
        url: ''
        target: newtab
        statusCheck: true
        id: 4_100395_vaultwarden
      - title: Wallabag
        icon: icons/dashboard-icons/png/wallabag.png
        url: ''
        target: newtab
        statusCheck: true
        id: 5_100395_wallabag
  - name: 文件管理
    icon: fas fa-file
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: false
      hideForGuests: false
    items:
      - title: Nextcloud
        description: ''
        icon: icons/dashboard-icons/png/nextcloud.png
        url: ''
        target: newtab
        statusCheck: true
        id: 0_107556_nextcloud
      - title: Alist
        icon: fas fa-file
        url: ''
        target: newtab
        statusCheck: true
        id: 1_107556_alist
      - title: Wordpress
        icon: icons/dashboard-icons/png/wordpress.png
        id: 2_107556_wordpress
      - title: Wikijs
        icon: icons/dashboard-icons/png/wikijs.png
        id: 3_107556_wikijs
      - title: gugu
        icon: icons/dashboard-icons/png/webdav.png
        id: 4_107556_gugu
  - name: 娱乐
    icon: fas fa-film
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: false
      hideForGuests: false
    items:
      - title: Navidrome
        icon: icons/dashboard-icons/png/navidrome.png
        url: ''
        target: newtab
        statusCheck: true
        id: 0_43137_navidrome
      - title: Jellyfin
        icon: icons/dashboard-icons/png/jellyfin.png
        url: ''
        target: newtab
        statusCheck: true
        id: 1_43137_jellyfin
      - title: xmrig
        icon: icons/dashboard-icons/png/xmrig.png
        id: 2_43137_xmrig
      - title: Speedtest-tracker
        icon: icons/dashboard-icons/png/speedtest-tracker.png
        id: 3_43137_speedtesttracker
  - name: Disk Space
    icon: fas fa-hdd
    widgets:
      - type: gl-disk-space
        options:
          hostname: http://95.179.242.122:61208
        id: 0_919_gldiskspace
  - name: CPU History
    icon: fas fa-microchip
    displayData:
      cols: 2
    widgets:
      - type: gl-cpu-history
        options:
          hostname: http://95.179.242.122:61208
          limit: 60
        id: 0_1018_glcpuhistory
  - name: System Alerts
    icon: fas fa-sensor-alert
    widgets:
      - type: gl-alerts
        options:
          hostname: http://95.179.242.122:61208
        id: 0_1296_glalerts
  - name: System Load
    icon: fas fa-tasks-alt
    widgets:
      - type: gl-system-load
        options:
          hostname: http://95.179.242.122:61208
        id: 0_1061_glsystemload
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: true
      hideForGuests: false
  - name: Network Interfaces
    icon: fas fa-ethernet
    widgets:
      - type: gl-network-interfaces
        options:
          hostname: http://95.179.242.122:61208
          limit: 500
        id: 0_1806_glnetworkinterfaces
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: true
      hideForGuests: false
  - name: Disk IO
    icon: fas fa-disc-drive
    widgets:
      - type: gl-disk-io
        options:
          hostname: http://95.179.242.122:61208
        id: 0_579_gldiskio
    displayData:
      sortBy: default
      rows: 1
      cols: 1
      collapsed: true
      hideForGuests: false
```



注意观察，其实`yml`文件都是有规律的，灵活变通。

Font Awesome：http://www.fontawesome.com.cn/



修改完之后之后再重新运行 Dashy 即可：

```bash
cd cd /root/data/docker_data/dashy

docker-compose restart
```




> 对于上述问题，有解决的小伙伴欢迎在评论区留言交流！

## 8. 结尾

祝大家用得开心，有问题可以去GitHub提[Issues](https://github.com/Lissy93/dashy/issues)，也可以在评论区互相交流探讨。

同时，有能力给项目做贡献的同学，也欢迎积极加入到[项目](https://github.com/Lissy93/dashy)中来，贡献自己的一份力量！

## 9. 参考资料

https://shownotes.opensourceisawesome.com/dashy-powerful-informative/

https://github.com/Lissy93/dashy

https://dashy.to/

https://demo.dashy.to/

https://dashy.to/docs/





【好玩儿的Docker项目】给你的自建服务整一个炫酷的面板——Dashy 一个功能非常强大的面板，可以监控服务状态！


iTab 标签页面：https://itab.link/install/chrome.html


Dashy
Docker
好玩儿的Docker项目
服务器监控
Nas
自建服务
glances
python3


代码在这：https://gao.ee/dashy-yt

https://gao.ee/dashy-bili

00:00 Dashy演示
02:22 Dashy简单介绍
07:42 搭建环境介绍
09:40 感谢支持的小伙伴
10:56 安装Docker和docker compose
12:27 开始搭建
19:42 登陆及前台配置
23:20 配置域名和反向代理（不开SSL）
24:48 安装glances
28:03 修改conf.yml
30:09 大功告成！
32:02 欢迎贡献自己的力量
33:05 下期预告




youtube



00:00 Dashy演示
02:22 Dashy简单介绍
07:42 搭建环境介绍
09:40 感谢支持的小伙伴
10:56 安装Docker和docker compose
12:27 开始搭建Dashy
19:42 Dashy登陆及前台配置
23:20 配置域名和反向代理（不开SSL）
24:48 安装glances
28:03 修改conf.yml
30:09 大功告成！
32:02 欢迎贡献自己的力量
33:05 下期预告


https://youtu.be/OAt_wFU6Nwc






---

> 作者: Roy  
> http://localhost:1313/dashy/
