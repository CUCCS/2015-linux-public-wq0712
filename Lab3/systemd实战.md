# systemd实战
### 实验过程

- 命令篇  

  - [系统管理](https://asciinema.org/a/zMKd0Yh6ToWkqdvVRSv3Cwkf5)  
  - [Unit](https://asciinema.org/a/0GB53t3mkVfAB1PFMLwRfYo4a)  
  - [Unit 的配置文件](https://asciinema.org/a/FQ1kl0GKjg6KbZS26eol2NdZI)  
  - [Target](https://asciinema.org/a/0MlUdCg5eESh7xdDPiw9yV4TB)  
  - [日志管理](https://asciinema.org/a/eKdMfoLsv1qvBx0BR2cCnms4P)  
   
- 实战篇  
 
  - [基本任务](https://asciinema.org/a/r8OV088zlnmbd5IvawzT4ne4A) 
  

### 自查清单
- 如何添加一个用户并使其具备sudo执行程序的权限?

```
sudo adduser username
sudo usermod -a -G sudo username
```
- 如何将一个用户添加到一个用户组？

```
sudo usermod -a -G test username
```
- 如何查看当前系统的分区表和文件系统详细信息？

```
sudo fdisk -l
```
- 如何实现开机自动挂载Virtualbox的共享目录分区?  
  1.安装增强功能。  
  2.配置共享文件夹。  
  3.进入系统创建共享目录。  
  4.挂载。

- 基于LVM（逻辑分卷管理）的分区如何实现动态扩容和缩减容量？  

```
 1.扩容：sudo lvextend -L +10G /dev/vg/swap_1
 2.减容：sudo lvreduce -L -10G /dev/vg/swap_1
```
- 如何通过systemd设置实现在网络连通时运行一个指定脚本，在网络断开时运行另一个脚本？
  
  - 修改networking.service文件，添加两行。
  
```
ExecStarPre=/bin/bash /home/username/1.sh
ExecStopPost=/bin/bash /home/username/2.sh
```
- 如何通过systemd设置实现一个脚本在任何情况下被杀死之后会立即重新启动？实现杀不死？

  - 修改该脚本的配置文件的service部分，将Restart字段设置参数为always。

### 参考链接
[Systemd 入门教程：命令篇
](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)  
[Systemd 入门教程：实战篇
](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-part-two.html)
