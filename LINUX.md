[TOC]

## Linux简介

LAMP 支撑互联网的开源技术
	Linux 操作系统
	Apache Web服务器
	MySQL 数据库
	PHP 编程语言

## Linux系统的安装

### VMware虚拟机的安装

### 系统分区

**主分区**：最多只能又4个

扩展分区：就是用来包含逻辑分区
	-最多只能又1个
	-主分区加扩展分区最多有4个
	-不能写入数据格式化，只能包含逻辑分区

逻辑分区：可以写入数据与格式化

![image-20210301144037041](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210301144037041.png)

注释:1 2 3是主分区 4是扩展分区 5 6是逻辑分区

**格式化**：在硬盘中写入文件系统
	1.将硬盘分割成一个一个等大小的数据块
	2.建立一个inode列表用来读取数据

**硬件设备文件名**

![image-20210301150123844](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210301150123844.png)

注释：
	/表示Linux中的根目录，可以想象成windows中的我的电脑，所有的数据都保存在根目录下
	dev一级子目录，在这个子目录下存放的所有文件都是硬件文件
	/hd[a-d]表示的就是硬盘名，比如第一个IDE硬盘叫/dev/hda，第二个IDE硬盘叫/dev/hdb

**分区设备文件名**

直接在硬盘文件名后面加分区号
	/dev/hda 1 表示第一个IDE硬盘下的第一个分区
	/dev/hda 2 表示第一个IDE硬盘下的第二个分区
	逻辑分区只能从5开始往后

**挂载**

给每个分区分配挂载点

总结：
	1.分区：给一个硬盘划分几个小的逻辑分区
	2.格式化：将每一个分区划分成小的数据块，写入文件系统
	3.分区设备文件名：给每一个分区定义文件名
	4.挂载：给每个分区分配挂载点

### Linux系统安装

### 远程登陆管理工具

网络连接
	—桥接：虚拟机会利用本机的真实网卡进行通信，好处是只要设置虚拟机和本机相同网段的ip地址，就可以直接实现虚拟机与本机的通信，而且虚拟机还可以和处于同一网段的其他计算机进行通信，坏处就是需要占用网段的一个ip
	—NAT：虚拟机通过VMnet8虚拟网卡跟真实机通信，虚拟机只能和本机通信，但是如果真实机可以访问互联网，那么虚拟机也可以
	—hostonly：虚拟机通过VMnet1虚拟网卡跟真实机通信，虚拟机只能和本机通信

ifconfig 命令可以查看当前虚拟机网卡的一个ip地址

ifconfig ens33 +ip地址 可以修改虚拟机网卡的ip

## 给初学者的建议

### 注意事项

Linux严格区分大小写

Linux中所有内容都以文件形式保存，包括所有的硬件如硬盘

Linux不靠扩展名区分文件类型，但是为了便于使用也会用到一些扩展名

Linux所有存储设备必须挂载后才能使用，包括硬盘、U盘和光盘

Windows下的程序不能直接在Linux中安装和运行

### 服务器的管理和维护建议

Linux下各个目录的作用

![image-20210302195113336](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210302195113336.png)

![image-20210302195331225](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210302195331225.png)

![image-20210302195928312](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210302195928312.png)

服务器注意事项
	—远程服务器不允许关机，只能重启。服务器大多数情况下不在身边
	—重启时应该关闭正在运行的服务
	—不要再服务器访问高峰运行高负载命令
	—远程配置防火墙时不要把自己踢出服务器
	—指定合理的密码规范并定期更新
	—合理分配权限
	—定期备份重要数据和日志

## Linux常用命令

### 命令格式与目录处理命令ls

命令格式：命令 [-选项] [参数]
例如：ls -la /etc

Linux中文件对用户的关系：u 所有者 g 所属组 o 其他人
	—创建这个文件的用户就是这个文件的所有者，所有者只能有一个，但是所有者是可以变换的
	—把一些用户编为一个组，只有这个组的成员才有文件的权限，这个组就叫所属组
	—文件对不属于所有者和所属组的用户叫做其他人

#### 目录处理命令：ls

![image-20210302205331664](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210302205331664.png)

![image-20210302205444101](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210302205444101.png)

后六个参数分别代表： 文件计数，所有者，所属组，文件大小，文件最后修改时间，文件名

ls -i 可以查看文件的i节点

第一个参数：

![image-20210302205745744](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210302205745744.png)

#### 目录处理命令：mkdir

![image-20210303141720226](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303141720226.png)

#### 目录处理命令：cd

![image-20210303143906633](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303143906633.png)

#### 目录处理命令：pwd

![image-20210303144311569](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303144311569.png)

 注释：. 表示当前目录  .. 表示当前目录的上一级目录

#### 文件处理命令：rmdir

![image-20210303144639120](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303144639120.png)

 注释：只能删除空目录，如果目录非空就不能删除

#### 目录处理命令：cp

![image-20210303144944441](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303144944441.png)

#### 目录处理命令：mv

![image-20210303150124890](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303150124890.png)

#### 目录处理命令：rm

![image-20210303150750685](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303150750685.png)

#### 文件处理命令：touch

![image-20210303155530088](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303155530088.png)

#### 文件处理命令：cat

![image-20210303160344191](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303160344191.png)

#### 文件处理命令：more

![image-20210303160731137](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303160731137.png)

注释：按B返回上一页；/ 字符串 可以搜索字符串所在的位置

#### 文件处理命令：less

![image-20210303161656661](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303161656661.png)

注释：
	—pageup可以向上翻一页
	—上箭头可以翻一行
	—/+索引 可以用来查找文件中的索引 按n（next）来查找下一个

#### 文件处理命令：head

![image-20210303162218322](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303162218322.png)

注释：如果不指定行数，默认就是前10行

#### 文件处理命令：tail

![image-20210303162715309](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303162715309.png)

#### 文件处理命令：ln

![image-20210303191159368](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303191159368.png)

ln -s 源文件 目标文件   将源文件生成一个目标文件

ln 源文件 目标文件 将源文件生成一个硬文件

注释：软连接类似Windows快捷方式
	—软连接的权限一定是 lrwxrwxrwx
	—文件大小很小，本身只是一个符号连接
	—箭头指向源文件

注释：硬连接类似于对源文件进行拷贝
	—拷贝 cp -p +同步更新，比cp -p命令很加强，对源文件的操作同时会更新到硬链接上，但是如果删除源文件，硬链接仍然能够访问
	—通过i节点识别，硬链接的i节点和源文件的i节点是相同的，但是软连接的i节点和源文件是不同的
	—不能跨分区
	—不能针对目录使用

### 权限管理命令

#### 权限管理命令：chmod

![image-20210303201848489](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303201848489.png)

注释：
	—权限的数字表示：r=4  w=2 x=1  例如rwxrw-r-- 就代表764
	—只有两个人可以更改文件的权限 所有者和root

对于文件的权限：
	—r 读权限 是指可以查看文件的内容 例如cat more less head tail等命令
	—w 写权限 是指可以修改该文件的内容 例如vim命令
	—x 执行权限 是指可以执行这个文件 例如一个脚本文件、一个命令文件

对于目录的权限：
	—r 读权限 是指可以显示出该目录下的内容 例如ls 命令
	—w 写权限 是指可以修改或者删除该目录下的文件 例如touch rm mkdir
	—x 执行权限 是指可以进入目录例如cd

注释：
	—对一个文件有写权限只是代表你有修改这个文件内容的权限，但是如果你想要删除这个文件，你需要对这个文件所在的目录有写权限
	—一般来说目录的r和x权限一般是一起出现的

#### 权限管理命令：chown

![image-20210303203642086](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210303203642086.png)

### 文件搜索命令

#### 文件搜索命令：find

![image-20210309092824631](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210309092824631.png)

注释：
	—find /etc -name init  在/etc目录中查找init文件* init*查找文件中有init的 *代表通配符 ？匹配单个字符 -iname不区分大小写
	—find / -size +204800 在根目录下寻找大于100MB的文件 +表示大于 -表示小于  1数据块=0.5k  100MB=102400k=204800数据块
	—find /home -user shenchao 在家目录下查找所有者为shenchao的文件-group 根据所属组查找
	—find /etc -size +163840 -a -size -204800 在/etc目录下寻找大于80mb小于100mb的文件 -a 表示and  -o 表示or  
	—-type根据文件类型查找 f文件 d目录 l软连接 -inum 根据i节点查找

#### 其他文件搜索命令：locate

![image-20210309101721271](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210309101721271.png)

#### 文件搜索命令：which

![image-20210309103309662](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210309103309662.png)

### 帮助命令

#### 帮助命令：man

![image-20210406090101728](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406090101728.png)

注释：
	—查看命令，一般看这个命令是做什么用的 name行，这个命令的某个选项是做什么用的 /+选项   1表示命令
	—查看配置文件，这个配置文件时做什么用的，这个配置文件的格式是怎样的     5表示配置文件
	—如果一个名字即对应命令，也对应一个配置文件，那么man 1 passwd表示passwd命令的帮助，man 5 passwd表示passwd配置文件的帮助

命令 --help：查看命令的所有选项

#### 帮助命令:help

![image-20210406093644711](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406093644711.png)

#### 总结

![image-20210406095504640](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406095504640.png)



### 用户管理命令

#### 用户管理命令：useradd

![image-20210406095643662](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406095643662.png)

#### 用户管理命令:passwd

![image-20210406100545043](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406100545043.png)

#### 用户管理命令：who

![image-20210406100609073](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406100609073.png)

![image-20210406100851299](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406100851299.png)



注释：第一个表示登陆用户名，第二个是登陆终端 tty表示本地登陆 pts表示远程终端，第三个表示登陆时间，第四个表示登陆的ip

#### 总结

![image-20210406101808378](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406101808378.png)



### 压缩解压命令

#### 压缩命令：gzip

![image-20210406103038017](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406103038017.png)

注释：只能压缩文件，不能压缩目录；压缩之后原文件会消失，只会留下压缩文件

#### 解压缩命令：gunzip

![image-20210406103111000](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406103111000.png)

#### 压缩解压命令：tar

![image-20210406104110924](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406104110924.png)



![image-20210406105203123](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406105203123.png)

#### 压缩解压命令：bzip2

![image-20210406105838447](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406105838447.png)

注释：压缩比惊人，一般用来压缩数据量大的文件

#### 总结

![image-20210406110653713](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210406110653713.png)



### 网络命令

#### 网络命令：write

![image-20210407150627131](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407150627131.png)

#### 网络命令：wall

![image-20210407150956207](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407150956207.png)

#### 网络命令：ping

![image-20210407151249879](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407151249879.png)

#### 网络命令：ifconfig

![image-20210407152150948](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407152150948.png)

#### 网络命令：mail

![image-20210407152656201](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407152656201.png)

#### 网络命令：last

![image-20210407153046371](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407153046371.png)

注释：lastlog 显示出所有用户最后一次登陆的时间

#### 网络命令：traceroute

![image-20210407154011760](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210407154011760.png)

注释：可以显示你登陆到某个网站，你访问了那些节点

#### 网络命令：netstat

传输协议：
	—TCP 传输控制协议 类似于打电话，打通之后要询问你是谁，我是某某某，你又是谁等，三次握手协议。这个协议要求传输双方都在线，信息能够即时传输，发错了也可以即时回传，是面向连接的协议
	—UDP协议 用户数据报协议 类似于发短信，直接就把短信发过去了，不要求双方都在线，优点是传输速度快，缺点是可能接收不到信息

![image-20210409091223084](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409091223084.png)

![image-20210409091320987](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409091320987.png)

#### 网络命令：setup

![image-20210409092229528](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409092229528.png)

#### 网络命令：mount

![image-20210409092629301](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409092629301.png)

umount 卸载

注释：iso9660表示光盘  设备文件名+挂载点

光盘的使用方法：装入光盘后记得要通电（已连接）；插入光盘后首先要做的是给光盘找一个挂载点；弹出光盘的时候记得要先把挂载点卸掉

### 关机重启命令

#### 关机重启命令：shutdown

![image-20210409094327133](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409094327133.png)

#### 查询系统运行级别：runlevel

0-关机 1-单用户 2-不完全多用户（不包含NFS）3-完全多用户 4-未分配 5-图形界面 6-重启

#### 用户退出命令：logout

## 文本编辑器Vim

### Vim常用操作

#### Vim工作模式

![image-20210416142309975](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416142309975.png)

命令模式的标志：

插入模式的标志：下面有INSERT   就相当与记事本

编辑模式的标志：“：“

#### 插入命令

![image-20210416143726876](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416143726876.png)

#### 定位命令

![image-20210416143818300](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416143818300.png)

#### 删除命令

![image-20210416144354956](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416144354956.png)

#### 复制和剪切命令

![image-20210416145000727](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416145000727.png)

#### 替换和取消命令

![image-20210416145053102](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416145053102.png)

#### 搜索命令

![image-20210416145146701](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416145146701.png)

注释：n表示搜索下一个

#### 保存退出命令

![image-20210416145333120](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416145333120.png)



### Vim使用技巧

## 软件包管理

### 软件包管理简介

#### 软件包分类

**源码包**：在Linux中源码包一般是.c结尾的c语言包，特点是开源，在Linux 中安装源码包要先编译，速度很慢

![image-20210409112604603](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409112604603.png)

![image-20210409112624694](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409112624694.png)

**二进制（RPM）包**：在Linux中以.rpm结尾的，这种二进制包是源码包编译之后的包，特点是安装速度很快，但是不开源

![image-20210409112645234](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409112645234.png)

![image-20210409112653804](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210409112653804.png)

### RPM命令管理

#### 包命名与依赖性

##### rpm包命名规则

![image-20210410183402400](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410183402400.png)

##### rpm包依赖性

![image-20210410184853888](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410184853888.png)

注释：

​	—树形依赖是指你要安装a包，必须先安装b包，必须先安装c包
​	—环形依赖是指你要安装a，必须先安装b，先安装c，但是又要安装a
​	—模块（库文件）依赖是指你要安装a，必须先安装b中的某一个文件，但是你不知道这个文件属于哪一个包，库文件依赖一般以.so.数字结尾

#### 包全名与包名

![image-20210410185255366](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410185255366.png)



#### rpm安装命令

![image-20210410185445990](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410185445990.png)

#### rpm包升级

![image-20210410190314568](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410190314568.png)

#### rpm包卸载

![image-20210410190424771](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410190424771.png)

#### RPM命令管理-查询

![image-20210410190848668](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410190848668.png)

![image-20210410191136319](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410191136319.png)

![image-20210410192933963](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410192933963.png)

![image-20210410193234047](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410193234047.png)

![image-20210410193417635](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410193417635.png)

#### RPM命令管理-校验和文件提取

![image-20210410194311818](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410194311818.png)

注释：主要是用来查询文件是否呗他人修改

修改项

![image-20210410194859086](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410194859086.png)

![image-20210410195233241](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210410195233241.png)

### RPM包-yum在线管理

#### IP地址配置和网络yum源

##### IP地址配置

##### 网络yum源

![image-20210416183401865](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416183401865.png)

#### yum命令

##### 查询命令

![image-20210416185036065](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416185036065.png)

##### 安装

![image-20210416185119109](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416185119109.png)

##### 升级

![image-20210416185609330](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416185609330.png)

#### 光盘yum源搭建

![image-20210416192521908](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416192521908.png)

![image-20210416192529594](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416192529594.png)

### 源码包管理

#### 源码包和RPM包的区别

安装之前的区别：概念上的区别

安装之后的区别：安装位置的区别

​	—RPM包安装在默认位置，不需要认为去调整
​	—源码包人为手工确定安装位置

#### RPM包安装位置

![image-20210416193112230](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416193112230.png)

#### 源码包安装位置

![image-20210416193839868](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416193839868.png)

#### 安装位置不同带来的影响

![image-20210416194110241](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210416194110241.png)

源码包只能通过绝对路径安装

### 源码包安装过程

下载源码包

#### 安装注意事项

![image-20210419103603765](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210419103603765.png)

#### 安装过程

1.下载源码包（windows）并且把它上传到Linux中

2.

## Shell编程基础

### Shell概述

Shell 命令解释器：把类似ls命令转换成0101给到内核，所以叫命令解释器；强大的变成语言，易编写调试

Linux中支持的shell：vim /etc/shells

### 脚本执行方式

#### echo输出命令

![image-20210421095830830](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210421095830830.png)

![image-20210421100017912](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210421100017912.png)

#### 第一个脚本

![image-20210421100654190](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210421100654190.png)

#!/bin/Bash 这个不是一个注释，它相当于一个标识符，告诉你这是一个shell脚本，一般来说shell脚本第一行必须写这一句

#### 执行脚本

1.赋予执行权限，直接运行
	—chmod 755 hello.sh
	—./hello.sh  #相对路径或者绝对路径来调用

2.通过bash调用
	bash hello.sh

dos2unix命令可以把windows下的shell脚本格式转化成Linux下的脚本格式

### bash的基本功能

#### bash基本功能-历史命令与补全

##### 历史命令：history

![image-20210421102755471](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210421102755471.png)

注释：历史命令默认会保存1000条，可以在/etc/profie中修改

![image-20210423085049837](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423085049837.png)

##### 命令与文件补全

tab键可以补全命令

#### bash基本功能-别名与快捷键

##### 命令别名

![image-20210423090005074](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423090005074.png)

![image-20210423090757787](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423090757787.png)

注释：想要永久生效要到 /root/bashrc下修改配置文件；删除别名unalias

##### bash常用快捷键

![image-20210423091103796](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423091103796.png)

注释：小写就可以了

#### 输入输出重定向

##### 标准输入输出

![image-20210423091806593](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423091806593.png)

##### 输出重定向

![image-20210423092059975](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423092059975.png)

注释：输出重定向就是改变输出的位置，比如本来应该在屏幕上输出，把它改到输出在文件中

更重要的是：

![image-20210423093109372](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423093109372.png)

##### 输入重定向

![image-20210423094509173](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423094509173.png)

注释：输入重定向是指改变输入的位置，比如本来一个文件需要从键盘输入参数，但是输入重定向，让一个文件作为输入

#### 多命令顺序执行和管道符

##### 多命令顺序执行

![image-20210423095203923](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423095203923.png)

##### 管道符|

![image-20210423101522748](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423101522748.png)

##### grep

![image-20210423102446522](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423102446522.png)

#### 通配符和其他字符

##### 通配符

![image-20210423102914066](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423102914066.png)

##### 其他字符

![image-20210423110128325](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210423110128325.png)

### bash的变量

#### 用户自定义变量

变量：计算机内存的单元，其中存放的值可以改变

变量设置规则：由字母，数字，下划线组合而成，但是不能由数字组成；在bash中默认为字符串   

注释：
	—变量用等号连接值，等号左右两侧不能有空格
	—变量的值如果有空格，需要使用单引号或者双引号括起来
	—在变量的值中可以使用\转义字符
	—如果需要增加变量的值，那么可以进行变量值的叠加
	—如果是把命令的结果作为变量值赋予变量，则需要使用$()包含命令
	—环境变量名建议大写

变量分类：自定义变量；环境变量；位置参数变量；预定义变量

变量定义：name="fzz"

变量叠加：name="$name"" is a handsome boy"      此时name变成fzz is a handsome boy 

变量调用：echo $name

变量查看：set

变量删除：unset name

#### 环境变量

环境变量：用户自定义变量只在当前shell中生效，但是环境变量会在当前shell和这个shell的所有字shell生效，如果把环境变量写进相应的配置文件，那么这个环境变量会在所有shell生效

设置环境变量：export 变量名=变量值

查询变量：env

删除变量：unset

常见的环境变量

![image-20210427200115612](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210427200115612.png)

![image-20210427200615960](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210427200615960.png)

![image-20210427200950061](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210427200950061.png)

#### 位置参数变量

![image-20210427201355548](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210427201355548.png)

注释：$n就表示输入 \$1表示第一个输入 以此类推

![image-20210427203514742](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210427203514742.png)

![image-20210427203542871](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210427203542871.png)

#### 预定义变量

![image-20210428193306729](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210428193306729.png)

##### 接收键盘输入

![image-20210428194306352](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210428194306352.png)

### 数值运算和运算符

#### declare声明变量类型

![image-20210505095749768](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505095749768.png)

#### 数值运算

1.![image-20210505100313753](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505100313753.png)

2.![image-20210505100327104](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505100327104.png)

3.推荐![image-20210505100507952](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505100507952.png)

#### 运算符

![image-20210505100817879](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505100817879.png)

#### 变量测试与内容替换

![image-20210505101736870](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505101736870.png)

### 环境变量配置文件

#### 简介

##### source命令

![image-20210505105346826](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505105346826.png)

注释：更改配置文件后，一般要重启系统配置文件才能生效，source可以省略重启的过程

##### 配置文件简介

![image-20210505105602651](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505105602651.png)

![image-20210505110236023](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210505110236023.png)

注释：有五类配置文件 /etc下的配置文件是对所有用户生效

#### 配置文件的作用



#### 其他的配置文件和登陆信息

## Shell编程

### 正则表达式

#### 正则表达式与通配符

通配符用来匹配符合条件的文件名，通配符是完全匹配的。*代表匹配任意字符 ？代表匹配一个字符 []代表匹配括号里面的其中一个字符

正则表达式用来在文件中匹配符合条件的字符串，正则可以包含匹配

![image-20210507092030311](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210507092030311.png)

正则表达式的使用：grep 正则表达式 文件名

```
. #任意字符出现1次
* #前一个字符出现0次或多次
^ #后一个字符开头的  [^]表示取反
[] #匹配括号里面的任意字符1次
\ #转义字符
\{n\} #前一个字符出现n次
\{n,\} #前一个字符至少出现n次
\{n,m\} #前一个字符至少出现n次，至多出现m次
```

### 字符截取命令

#### cut字段提取命令

![image-20210507101720375](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210507101720375.png)

注释：默认是用tab作为分隔符

#### printf命令

![image-20210507103342337](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210507103342337.png)

![image-20210507103537567](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210507103537567.png)

注释：用printf打印文件的内容，printf "%s" $(cat student.txt)，不能直接打印

print和printf：print自动在每个输出之后加入一个换行符

#### awk命令

![image-20210512144345037](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210512144345037.png)

![image-20210512145628726](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210512145628726.png)

BEGIN命令：在处理所有数据之前，先处理这个

END命令：在处理所有数据之后，在处理END

手工定义分隔符

awk 'BEGIN{FS=":"}{print \$1 "\t" $3}' /etc/passwd

注释：手工定义分隔符一定要在前边加一个BEGIN，不加的话第一行无法处理

#### sed命令

sed是一种轻量级流编辑器，和vim最大的区别就是，sed不仅可以对文件进行编辑，还可以直接修改命令的结果

![image-20210512153159942](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210512153159942.png)



![image-20210512153318088](C:\Users\fzz\AppData\Roaming\Typora\typora-user-images\image-20210512153318088.png)



### 字符处理命令

### 条件判断

### 流程控制









