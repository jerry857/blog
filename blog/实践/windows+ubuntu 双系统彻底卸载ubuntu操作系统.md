在Windows下卸载Ubuntu
1. 删除 Ubuntu 系统分区
	1. 【win】+【R】，输入cmd
	2. 输入diskpart
	3. 查看所有磁盘，选中 Ubuntu 分区删除，命令如下
	```cmd
	list disk
	select disk * (所在磁盘)
	list partition 
	select partition #(所在分区)
	delect partition override
	一直重复即可
	```
2. 删除 Ubuntu 系统启动项
	1. 进入 cmd 
	2. 输入
```cmd
* diskpart
* list disk 
* select disk $(Windows安装所在盘)
* lsit partition 
* select partition 1
* assign letter=p
```

   3. 用管理员权限访问记事本
   4. 文件选择，打开磁盘p
   5. 不需要打开，找到 Ubuntu 文件夹删除即可
   6. 进入到第一步的操作界面，输入 remove letter=p; 删除p盘
   7. 重启
