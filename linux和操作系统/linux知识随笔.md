---
title:  LINUX 知识随笔
categories: [linux系统, 随笔]
tags: [linux系统, 随笔]
---
# LINUX 知识随笔

## 如何在两台linux主机间同步目录或文件？

Linux的Rsync服务（远程同步）

参考：[《rsync同步的艺术》–linux命令五分钟系列之四十二](http://roclinux.cn/?p=2643)、[rsync命令](http://man.linuxde.net/rsync)

rsync命令是一个远程数据同步工具，可通过LAN/WAN（本地或者远程）快速同步多台主机间的文件。所谓的同步，并不是实时的同步，需要执行命令来保证数据的同步。

Rsync命令的一些优点和功能：

- 有效地将文件复制到远程系统或从远程系统同步。
- 支持复制链接，设备，所有者，组和权限。
- 比SCP（安全复制）更快，因为rsync使用远程更新协议，允许转让只是**两套文件之间的差异**。 第一次，它从源到目标复制文件或目录的整个内容，但从下一次，它只将已更改的块和字节复制到目标。
- rsync的消耗更少的带宽 ，因为它使用压缩和解压缩方法在发送和接收数据两端。

rsync在使用的时候主要是熟悉使用方法和参数命令，在使用参数命令的时候需要主要考虑下面几点。
- rsync的quick check是否需要起作用，哪些参数在使用的使用quick check是默认开启的？
- 文件的modify time是否需要同步？
- 文件的权限是否需要同步？
- 是否需要保持目的端文件的属主和属组保持一致（rsync不具备这个能力，除非使用root用户权限）？
- 同步文件时是否需要压缩？
- 同步文件夹的时候，是否需要recursive？
- 同步中断是需要删除重新同步还是需要在中断时的基础上继续同步？
- 软链接和硬链接如何同步？
- 同步时，源端没有的文件是否在目的端删除？

以上都可以在 [《rsync同步的艺术》–linux命令五分钟系列之四十二](http://roclinux.cn/?p=2643)中或者使用 `man rsync` 中找到解决方案。

## 两台Linux系统主机间传输文件的方法有哪些？
参考：[Linux 上的常用文件传输方式介绍与比较](https://www.ibm.com/developerworks/cn/linux/l-cn-filetransfer/)
- ftp
- rcp
- scp
- wget
- curl
- rsync

**总结与比较**
- 传输性能

wget 通过支持后台执行及断点续传提高文件传输效率 ； rsync 则以其高效的传输及压缩算法达到快传输的目的。
- 配置难度

rcp 只需进行简单的配置，创建 .rhost 文件以及设置 /etc/hosts 文件中主机名与 IP 地址列表； wget 
设置设置方便简单，只需在客户端指定参数执行命令即可； rsync 在使用前需要对服务端 /etc/rsyncd.conf 进行参数设定，配置内容相对复杂。
- 安全性能

ftp、rcp 不保证传输的安全性，scp、rsync 则均可基于 ssh 认证进行传输，提供了较强的安全保障。 wget 也可通过指定安全协议做到安全传输。

通过上述的对比不难发现，每种文件传输方法基于其自身的特点与优势均有其典型的适用场景：
- ftp 作为最常用的入门式的文件传输方法，使用简单，易于理解，并且可以实现脚本自动化；
- rcp 相对于 ftp 可以保留文件属性并可递归的拷贝子目录；
- scp 利用 ssh 传输数据，并使用与 ssh 相同的认证模式，相对于 rcp 提供更强的安全保障；
- wget，实现递归下载，可跟踪 HTML 页面上的链接依次下载来创建远程服务器的本地版本，完全重建原始站点的目录结构，适合实现远程网站的镜像；
- curl 则适合用来进行自动的文件传输或操作序列，是一个很好的模拟用户在网页浏览器上的行为的工具；
- rsync 更适用于大数据量的每日同步，拷贝的速度很快，相对 wget 来说速度快且安全高效。


## 文件传输过程中如何限速？
限速的原因：有些机房会限制机器的流量，为了不触及底线，在使用scp和rsync的时候都要注意。为了避免你的scp或者rsync因为无良/懒惰的OPS设置防火墙的偷懒而造成的断流现象，我们必须对自己的数据传输进行一定的限流措施，慢一点总比被掐了的好。

参考：[Linux 命令 SCP 远程复制](http://www.nathanyan.com/2016/04/10/Linux-%E5%91%BD%E4%BB%A4-SCP-%E8%BF%9C%E7%A8%8B%E5%A4%8D%E5%88%B6/)、[scp和rsync的限制流量（速度）方法](http://www.54chen.com/life/%E5%A6%82%E4%BD%95%E5%AF%B9%E4%BB%98%E6%97%A0%E8%89%AF%E6%87%92%E6%83%B0ops%E7%9A%84%E5%8F%AF%E8%80%BB%E7%9A%84%E9%99%90%E6%B5%81%E6%8E%AA%E6%96%BD.html)
- SCP限制带宽使用

>“-l”参数能限制使用带宽。如果你为了拷贝很多文件而去执行了一份自动化脚本又不希望带宽被SCP进程耗尽，那这个参数会非常管用。  
>
> 在“-l”参数后面的这个400值意思是我们给SCP进程限制了带宽为50 KB/秒。有一点要记住，带宽是以千比特/秒 (kbps)表示的，而8 比特等于1 字节。 
>
> 因为SCP是用千字节/秒 (KB/s)计算的，所以如果你想要限制SCP的最大带宽只有50 KB/s，你就需要设置成50 x 8 = 400。
```shell
scp -l 400 ib_logfile2 root@mysql-2:/tmp
```

- rsync带宽限速

使用 --bwlimit 参数，例如限制为 60k Bytes/s
```shell
  rsync -auvz --progress --delete --bwlimit=60 远程的文件  本地的文件
  rsync -auvz --progress --delete --bwlimit=60 本地的文件  远程的文件
```

## 查看文件大小并排序
参考资料
- [Linux命令之查看文件占用空间大小-du,df](https://blog.csdn.net/wangjunjun2008/article/details/19840671)
- [du命令 实现Linux 某个文件夹下的文件按大小排序](http://www.cnblogs.com/mfryf/p/3243211.html)

```sh
df -lh

# 按字节排序
du -s /usr/* | sort -rn

# 按兆（M）来排序
du -sh /usr/* | sort -rn

# 选出排在前面的10个
du -s /usr/* | sort -rn | head

# 选出排在后面的10个
du -s /usr/* | sort -rn | tail

du -h –-max-depth=0 user
du -sh –-max-depth=2 | more
```

## 进程间通信方式
参考：[Inter Process Communication(IPC)](https://www.tutorialspoint.com/inter_process_communication/index.htm)
### 为什么需要进程间通信？
### pipes
### named pipes
### shared memory
### message queue
### semaphore
关于[semaphore的作用以及semaphore和lock的区别](https://blog.csdn.net/zm1_1zm/article/details/76128701)，还是要好好考虑下。互斥量用于线程的互斥，信号量用于线程的同步。互斥量用于解决线程间共享资源的问题，信号量用于调度线程的问题。线程调度就是通过一些机制使得线程按照顺序对资源进行访问。以上是lock和semaphore最核心的区别，另外锁代表了对资源的所有权，所以锁的释放必须由持有锁的线程完成，但是semaphore的释放可以由其他线程完成。
### signals
### memory mapping