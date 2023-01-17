# 前言

## 重要

这里只提供了config文件，不用管，直接往下看本教程即可。

## 闲聊

牺牲10%的体验（不能拥有100%的白苹果体验），节省50%的钱（可以去咸鱼购置配置不错的二手笔记本），这就是我选择黑苹果的理由（不是，本质是没钱哈哈哈）。

这台电脑还是相对比较好弄的，体验可以。

* 第一次用final cut pro，我超，太流畅了（相比于win下的pr）
* PS、PR、AU、AI打开速度都比win要快一些，舒服

* Office三件套冷启动（开机第一次启动）有点慢啊，不如win，不过好像白苹果也这样。wps打开比较快，但不喜欢用。
* QQ 微信 vscode 打开速度都很快。注意vscode使用command+q退出下次才能自动打开之前项目，直接用左上角x号关闭就不行。

## 电脑基本信息

* 型号：联想YOGA-S740
* cpu：i5-1035G1
* 显卡：核显（bios内屏蔽独显mx250）
* 内存：原装，海力士16G、 3733频率
* 硬盘：非原装，更换为西数SN570 1T（原装三星pm981a不行的，一定要换硬盘）
* 网卡：原装，英特尔AX201
* 系统：目前win10专业版和MacOS 13.0 Ventura双系统

# 黑苹果情况

## 已知功能异常

* 电脑内置麦克风（英特尔麦克风阵列）不能驱动，可以用耳机的耳麦替代
* 人脸识别不能使用，mac不支持人脸识别
* 如果插了有扬声器的副屏，副屏的扬声器无法识别到，切换音频输出那里只有内置扬声器的选项。（可能是个问题？还是说mac就是这样的？不知道）

# 如何使用？

## 安装系统

### 针对非小白的简略教程

**首先、制作mac启动盘**

1. 此github仓库只有config.plist文件，可以不用管，直接去网盘下载我分享的完整的EFI文件
   * [天翼网盘链接](https://cloud.189.cn/t/z2qMJfyMvaMf)（访问码：9hsa）
   * 下载后解压
2. 制作mac启动盘。下载mac镜像，插入u盘，使用balena制作启动盘 [下载地址](https://www.balena.io/etcher/)
   * mac镜像下载 [天翼网盘链接](https://cloud.189.cn/t/nQz2EfMzI77b) （访问码：4khw）
   * balena软件下载 [官网链接](https://www.balena.io/etcher/)
3. 使用DiskGenius将你制作好的mac启动盘（u盘）的efi分区内容全部删掉，将刚才解压出来的EFI复制进去。

**其次、调整bios**

1. 开启时狂按F2进入bios

2. 找到并关闭scrue boot
3. 部分隐藏项（DVMT、CFD-LOCK、GPIO）需要进入win后用软件调整
   * 下载准备软件和教程提示：[天翼云盘链接](https://cloud.189.cn/t/326fQrUZZV3m) （访问码：vgi6）
   * 按照里面的图片提示和教程，修改DVMT和CFG-LOCK以及GPIO，（无需知道是什么，按着文件内教程和图片操作即可）

**然后、开始安装系统**

1. 关机重启，在bios中把BOOT顺序调整为u盘最先
2. 然后进入启动盘，跑码，跑码结束选择install XXXX（卡在跑码界面或苹果logo界面说明之前的步骤有问题）
3. 根据你的情况进行抹盘操作（必须要把你要装mac的分区擦除成afpx格式！），按提示进行安装
4. 电脑在安装过程中会进行数次重启，每次重启之后都要选择install XXX选项

**最后，将U盘的EFI搞到硬盘里**

1. 安装完成能进入系统确认无异常能使用之后，重启进入win系统下，用DiskGenius给磁盘再分出一个300MB的EFI分区，将u盘的EFI文件复制到改EFI分区
2. 拔掉优盘，调整bios顺序，建议将新建的EFI设为第一启动项，然后正常开机，完成。

**如果有问题联系邮箱lsc369@foxmail.com**

### 针对小白的详细教程

1. 观看b站大佬的yoga s740 i7版本黑苹果教程（注意他是i7版本，不可完全套用）[B站链接](https://www.bilibili.com/video/BV1RL4y1W7iw/?share_source=copy_web&vd_source=e12669299d41a343bc4b7a143cb161f2)
2. i5版本和i7版本只有一个不同，就是显卡的platform-id需要修改
3. 也就是视频教程里99%都不需要修改，只需要在大约3：55之后操作OC Auxiliary Tool时，需要多操作一步
4. 点击左侧DP栏，再点击PciRoot(0x0)/Pci(0x2,0x0)，修改platform-id的值，尾数修改为518A
5. 其他照着视频做即可，不难。
6. 有问题联系邮箱lsc369@foxmail.com

# 优化使用体验

1. 破解软件不好找啊
   * 我用的资源网站是[马可菠萝](https://www.macbl.com/)

2. 字体图标太小，字体发虚模糊

   * 开启1600x900的hidpi分辨率即可改善

   * 开启方法，参考国光大佬的教程：[直达链接](https://apple.sqlsec.com/6-%E5%AE%9E%E7%94%A8%E5%A7%BF%E5%8A%BF/6-5/)，

   * 选项依次选择1，3，6，然后输入1600x900

   * 重启后在设置-显示器-选择1600x900即可

3. 如果发现 聚焦功能能耗过高 或 “mds”、“mds store”以及其他系统进程占用大量cpu资源，风扇狂转

   * 原因：一般都是因为聚焦功能的离谱bug

   * 一般mac系统下不开大型软件的情况下风扇都很安静，且运行流畅。如果发现没开啥东西风扇呼呼转，还卡，那就去看看活动监视器，是不是有如上所说的那两个进程占用大量cpu资源。

   * 解决方法：在设置——Siri与聚焦，取消勾选所有搜索结果，并在 聚焦隐私 选项中，将整个**<u>所有</u>**磁盘分区，包括win系统所在盘和mac所在盘加进去即可

   * 解决原理：原理是不让聚焦扫描文件，不让其建立索引。也就是说现在聚焦啥也搜不到了。个人认为聚焦功能不必要。

# 鸣谢

* 参考过 *nan1jueze* 大佬的EFI：[nan1jueze大佬github链接](https://github.com/nan1jueze/YOGA_S740-14IIL_i5-1035G1_OpenCore)
* 参考过*frozenzero123*大佬的EFI：[frozenzero123大佬github链接](https://github.com/frozenzero123/YOGA-S740)
* 参考了*frozenzero123*大佬b站视频：[大佬b站视频链接](https://www.bilibili.com/video/BV1RL4y1W7iw/?share_source=copy_web&vd_source=e12669299d41a343bc4b7a143cb161f2)

# 联系方式

邮箱：lsc369@foxmail.com

