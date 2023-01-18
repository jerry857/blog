kali linux 是基于 Debian 系统的。所以命令基本通用。
其实内容上也只是Linux 系统，但是工具内置好了，不用随便动就好
制作一下牢饭模拟器

## 前期准备
一个好的 u 盘，很重要，我的快废了，读写速度慢的一批
* kali Linux 镜像文件 [官网](https//www.kali.org/
* 磁盘烧录工具 [rufus](http://rufus.ie/zh/)) 
* 分区工具[MiniTool Partition Wizard | Best partition magic alternative for Windows PC and Server](https://www.partitionwizard.com/)

## 安装步骤
### 制作启动盘
1. 下载kali linux，下载live boot ，64位发行版即可![image.png](https://gitee.com/jerry-857/images/raw/master/20230115010423.png)![image.png](https://gitee.com/jerry-857/images/raw/master/20230115010609.png)
2. 打开 rufus 分区类型选择GPT，主要看你u盘支持那种类型，其他默认即可，后续一路默认即可![image.png](https://gitee.com/jerry-857/images/raw/master/20230115011650.png)
3. 调整分区大小，打开MiniTool Partition Wizard分区工具，选择要分区的u盘。  右键，选择 Move/Resize 选项设置分区大小![image.png](https://gitee.com/jerry-857/images/raw/master/20230115012219.png) 系统盘分6G也行。对于灰色区域，点击右键，选择create 选项创建分区。 分区类型选择为ext4，当然选择Unformatted(不格式化)也成，大概也是能快一点。50多个分区创建的快墨迹死了。全部设置完后，点击 apply提交修改。至此分区调整完毕
4. 加密并持久化 。重启，进入BIOS界面，选择u盘启动
	1. 选择第一项以 LIVE 模式启动
	2. 设置加密分区
		1. 打开终端，选择红色图标的终端，root的，省的还要加 sudo su
		2. 输入 `fdisk -l`，看到磁盘情况，找到u盘位置，记下名称一般为 `/dev/sda`,找到加密分区的位置，按照上面的来的话，一般为 `/dev/sda2`。当然名字是最后一个字母是不固定的
		3. 使用 luks 命令为分区加密 `cryptsetup --verbose --verify-passphrase luksFormat /dev/sda2`，提示确定选项，输入 `YES` 大写的。提示输入密码，luks加密完成
		4. 使用 luksOpen 命令输入密码打开加密分区并创建可挂载的逻辑分区 kali
			1. `cryptsetup luksOpen /dev/sda2 kali`
			2. 将分区格式化为 Ext4 ,并将卷标设置为 persistence ，`mkfs.ext4 -L persistence /dev/mapper/kali`
			3. 分区持久化，操作为创建一个目录，将分区挂载到目录下，创建persistence.conf 文件到目录下，并为persistence.conf 写入参数
				1. 创建目录，`mkdir -p /kali/usb`
				2. 将加密分区挂载 `mount /dev/mapper/kali /kali/usb`
				3. 写入配置文件到目录下 `echo "/union" ? /kali/usb/persistence.conf`
				4. 卸载挂载 `umount /dev/mapper/kali`
				5. 退出 luks加密 `cryptsetup luksClose /dev/mapper/kali`
## 测试是否持久化
重启电脑，在 grub菜单中选择持久化模式启动。有两个模式 ，`Live USB Persistence` 使用未加密分区，`Live USB Encrypted Persistence` 使用加密分区，也叫加密持久化模式，进入到 加密分区。进入创建个文件，在重启看看，是否存在，如果存在就是持久化了，要不然就重新开始吧，反正也习惯了
### kali 设置中文
还是用命令行，进入到终端，输入 `sudo su` 切换到root 模式
1. 输入 `cd ~`
2. dpkg-reconfigure locales
3. 用小键盘方向键来上下选择，空格来表示选中和消除
4. 选择两个语言，`en_US.UTF-8 UTF-8`，和`zh_CN.UTF-8 UTF-8`
5. 敲两下回车，最后选择 zh_CN.UTF-8 ，就会显示载入界面，最后reboot即可
## 其他
至于其他的，应该是没啥了，其他的就是kali的使用，在官方文档里看就好了，反正也是要学一大堆的攻击工具，至于什么破解 wifi 或者攻击网站什么的，就最好不要干了，便携式牢饭模拟器，玩的花的都在牢里

参考文章
	 :  <https://b23.tv/k9BXLgV>
	 :[USB | Kali Linux Documentation](https://www.kali.org/docs/usb/)
另外吐槽一句，官方文档没有中文版，so 骚年，慢慢啃吧




