---
layout: post
title:  "常用linux命令"
date:   2015-5-20
keywords : 常用linux命令
description:  常用linux命令
categories:
- blog
permalink: linuxCommand
---



####系统信息

 1. arch 显示机器的处理器架构(1)
 2. uname -m 显示机器的处理器架构(2) 
 3. uname -r 显示正在使用的内核版本
 4. dmidecode -q 显示硬件系统部件 - (SMBIOS / DMI)
 5. hdparm -i /dev/hda 罗列一个磁盘的架构特性
 6. hdparm -tT /dev/sda 在磁盘上执行测试性读取操作
 7. cat /proc/cpuinfo 显示CPU info的信息
 8. cat /proc/interrupts 显示中断
 9. cat /proc/meminfo 校验内存使用
 10. cat /proc/swaps 显示哪些swap被使用
 11. cat /proc/version 显示内核的版本
 12. cat /proc/net/dev 显示网络适配器及统计
 13. cat /proc/mounts 显示已加载的文件系统
 14. lspci -tv 罗列 PCI 设备
 15. lsusb -tv 显示 USB 设备
 16. date 显示系统日期
 17. cal 2007 显示2007年的日历表
 18. date 041217002007.00 设置日期和时间 - 月日时分年.秒
 19. clock -w 将时间修改保存到 BIOS 

#### 关机 (系统的关机、重启以及登出 )

 1. shutdown -h now 关闭系统(1)
 2. init 0 关闭系统(2)
 3. telinit 0 关闭系统(3)
 4. shutdown -h hours:minutes & 按预定时间关闭系统
 5. shutdown -c 取消按预定时间关闭系统
 6. shutdown -r now 重启(1) 
 7. reboot 重启(2)
 8. logout 注销


#### 文件和目录

 1. cd /home  进入 '/ home' 目录'
 2. cd ..  返回上一级目录
 3. cd ../..  返回上两级目录
 4. cd 进入个人的主目录
 5. cd ~user1 进入个人的主目录
 6. cd - 返回上次所在的目录
 7. pwd 显示工作路径
 8. ls 查看目录中的文件
 9. ls -F 查看目录中的文件
 10. ls -l 显示文件和目录的详细资料
 11. ls -a 显示隐藏文件
 12. ls \*[0-9]\* 显示包含数字的文件名和目录名
 13. tree 显示文件和目录由根目录开始的树形结构(1)
 14. lstree 显示文件和目录由根目录开始的树形结构(2)
 15. mkdir dir1 创建一个叫做 'dir1' 的目录'
 16. mkdir dir1 dir2 同时创建两个目录
 17. mkdir -p /tmp/dir1/dir2 创建一个目录树
 18. rm -f file1 删除一个叫做 'file1' 的文件'
 19. rmdir dir1 删除一个叫做 'dir1' 的目录'
 20. rm -rf dir1 删除一个叫做 'dir1' 的目录并同时删除其内容
 21. rm -rf dir1 dir2 同时删除两个目录及它们的内容
 22. mv dir1 new_dir 重命名/移动 一个目录
 23. cp file1 file2 复制一个文件
 24. cp dir/* . 复制一个目录下的所有文件到当前工作目录
 25. cp -a /tmp/dir1 . 复制一个目录到当前工作目录
 26. cp -a dir1 dir2 复制一个目录
 27. ln -s file1 lnk1 创建一个指向文件或目录的软链接 
 28. ln file1 lnk1 创建一个指向文件或目录的物理链接
 29. touch -t 0712250000 file1 修改一个文件或目录的时间戳 - (YYMMDDhhmm) file file1 outputs the mime type of the file as text
 30. iconv -l 列出已知的编码


####文件搜索

 1. find / -name file1 从 '/' 开始进入根文件系统搜索文件和目录
 2.  find / -user user1 搜索属于用户 'user1' 的文件和目录
 3.  find /home/user1 -name \*.bin 在目录 '/ home/user1' 中搜索带有'.bin' 结尾的文件 
 4. find /usr/bin -type f -atime +100 搜索在过去100天内未被使用过的执行文件 
 5. find /usr/bin -type f -mtime -10 搜索在10天内被创建或者修改过的文件 
 6. find / -name \*.rpm -exec chmod 755 '{}' \; 搜索以 '.rpm' 结尾的文件并定义其权限 
 7. find / -xdev -name \*.rpm 搜索以 '.rpm' 结尾的文件，忽略光驱、捷盘等可移动设备 
 8. locate \*.ps 寻找以 '.ps' 结尾的文件 - 先运行 'updatedb' 命令 
 9. whereis halt 显示一个二进制文件、源码或man的位置 
 10. which halt 显示一个二进制文件或可执行文件的完整路径 


####挂载一个文件系统

 1. mount /dev/hda2 /mnt/hda2 挂载一个叫做hda2的盘 - 确定目录 '/ mnt/hda2' 已经存在 
 2. umount /dev/hda2 卸载一个叫做hda2的盘 - 先从挂载点 '/ mnt/hda2' 退出 
 3. fuser -km /mnt/hda2 当设备繁忙时强制卸载 
 4. umount -n /mnt/hda2 运行卸载操作而不写入 /etc/mtab 文件- 当文件为只读或当磁盘写满时非常有用 
 5. mount /dev/fd0 /mnt/floppy 挂载一个软盘 
 6. mount /dev/cdrom /mnt/cdrom 挂载一个cdrom或dvdrom 
 7. mount /dev/hdc /mnt/cdrecorder 挂载一个cdrw或dvdrom 
 8. mount /dev/hdb /mnt/cdrecorder 挂载一个cdrw或dvdrom 
 9. mount -o loop file.iso /mnt/cdrom 挂载一个文件或ISO镜像文件 
 10. mount -t vfat /dev/hda5 /mnt/hda5 挂载一个Windows FAT32文件系统 
 11. mount /dev/sda1 /mnt/usbdisk 挂载一个usb 捷盘或闪存设备 
 12. mount -t smbfs -o username=user,password=pass //WinClient/share /mnt/share 挂载一个windows网络共享


####磁盘空间

 1. df -h 显示已经挂载的分区列表
 2. ls -lSr \|more 以尺寸大小排列文件和目录 
 3. du -sh dir1 估算目录 'dir1' 已经使用的磁盘空间' 
 4. du -sk * \| sort -rn 以容量大小为依据依次显示文件和目录的大小 
 5. rpm -q -a --qf '%10{SIZE}t%{NAME}n' \| sort -k1,1n 以大小为依据依次显示已安装的rpm包所使用的空间 (fedora, redhat类系统) 
 6. dpkg-query -W -f='${Installed-Size;10}t${Package}n' \| sort -k1,1n 以大小为依据显示已安装的deb包所使用的空间 (ubuntu, debian类系统)


####用户和群组

 1. groupadd group_name 创建一个新用户组 
 2. groupdel group_name 删除一个用户组 
 3. groupmod -n new_group_name old_group_name 重命名一个用户组
 4. useradd -c "Name Surname " -g admin -d /home/user1 -s /bin/bash user1 创建一个属于 "admin" 用户组的用户 
 5. useradd user1 创建一个新用户 
 6. userdel -r user1 删除一个用户 ( '-r' 排除主目录) 
 7. usermod -c "User FTP" -g system -d /ftp/user1 -s /bin/nologin user1 修改用户属性 
 8. passwd 修改口令 
 9. passwd user1 修改一个用户的口令 (只允许root执行) 
 10. chage -E 2005-12-31 user1 设置用户口令的失效期限 
 11. pwck 检查 '/etc/passwd' 的文件格式和语法修正以及存在的用户 
 12. grpck 检查 '/etc/passwd' 的文件格式和语法修正以及存在的群组 
 13. newgrp group_name 登陆进一个新的群组以改变新创建文件的预设群组


####文件的权限 - 使用 "+" 设置权限，使用 "-" 用于取消

 1. ls -lh 显示权限 
 2. ls /tmp \| pr -T5 -W$COLUMNS 将终端划分成5栏显示 
 3. chmod ugo+rwx directory1 设置目录的所有人(u)、群组(g)以及其他人(o)以读（r ）、写(w)和执行(x)的权限 
 4. chmod go-rwx directory1 删除群组(g)与其他人(o)对目录的读写执行权限 
 5. chown user1 file1 改变一个文件的所有人属性 
 6. chown -R user1 directory1 改变一个目录的所有人属性并同时改变改目录下所有文件的属性 
 7. chgrp group1 file1 改变文件的群组 
 8. chown user1:group1 file1 改变一个文件的所有人和群组属性 
 9. find / -perm -u+s 罗列一个系统中所有使用了SUID控制的文件 
 10. chmod u+s /bin/file1 设置一个二进制文件的 SUID 位 - 运行该文件的用户也被赋予和所有者同样的权限 
 11. chmod u-s /bin/file1 禁用一个二进制文件的 SUID位 
 12. chmod g+s /home/public 设置一个目录的SGID 位 - 类似SUID ，不过这是针对目录的 
 13. chmod g-s /home/public 禁用一个目录的 SGID 位 
 14. chmod o+t /home/public 设置一个文件的 STIKY 位 - 只允许合法所有人删除文件 
 15. chmod o-t /home/public 禁用一个目录的 STIKY 位

####文件的特殊属性 - 使用 "+" 设置权限，使用 "-" 用于取消

 1. chattr +a file1 只允许以追加方式读写文件
 2. chattr +c file1 允许这个文件能被内核自动压缩/解压 
 3. chattr +d file1 在进行文件系统备份时，dump程序将忽略这个文件 
 4. chattr +i file1 设置成不可变的文件，不能被删除、修改、重命名或者链接 
 5. chattr +s file1 允许一个文件被安全地删除 
 6. chattr +S file1 一旦应用程序对这个文件执行了写操作，使系统立刻把修改的结果写到磁盘 
 7. chattr +u file1 若文件被删除，系统会允许你在以后恢复这个被删除的文件 
 8. lsattr 显示特殊的属性

####打包和压缩文件

 1. bunzip2 file1.bz2 解压一个叫做 'file1.bz2'的文件 
 2. bzip2 file1 压缩一个叫做 'file1' 的文件 
 3. gunzip file1.gz 解压一个叫做 'file1.gz'的文件 
 4. gzip file1 压缩一个叫做 'file1'的文件 
 5. gzip -9 file1 最大程度压缩 
 6. rar a file1.rar test_file 创建一个叫做 'file1.rar' 的包 
 7. rar a file1.rar file1 file2 dir1 同时压缩 'file1', 'file2' 以及目录 'dir1' 
 8. rar x file1.rar 解压rar包 
 9. unrar x file1.rar 解压rar包 
 10. tar -cvf archive.tar file1 创建一个非压缩的 tarball 
 11. tar -cvf archive.tar file1 file2 dir1 创建一个包含了 'file1', 'file2' 以及 'dir1'的档案文件 
 12. tar -tf archive.tar 显示一个包中的内容 
 13. tar -xvf archive.tar 释放一个包 
 14. tar -xvf archive.tar -C /tmp 将压缩包释放到 /tmp目录下 
 15. tar -cvfj archive.tar.bz2 dir1 创建一个bzip2格式的压缩包 
 16. tar -xvfj archive.tar.bz2 解压一个bzip2格式的压缩包 
 17. tar -cvfz archive.tar.gz dir1 创建一个gzip格式的压缩包 
 18. tar -xvfz archive.tar.gz 解压一个gzip格式的压缩包 
 19. zip file1.zip file1 创建一个zip格式的压缩包 
 20. zip -r file1.zip file1 file2 dir1 将几个文件和目录同时压缩成一个zip格式的压缩包 
 21. unzip file1.zip 解压一个zip格式压缩包 



####RPM 包 - （Fedora, Redhat及类似系统）

 1. rpm -ivh package.rpm 安装一个rpm包 
 2. rpm -ivh --nodeeps package.rpm 安装一个rpm包而忽略依赖关系警告 
 3. rpm -U package.rpm 更新一个rpm包但不改变其配置文件 
 4. rpm -F package.rpm 更新一个确定已经安装的rpm包 
 5. rpm -e package_name.rpm 删除一个rpm包 
 6. rpm -qa 显示系统中所有已经安装的rpm包 
 7. rpm -qa \| grep httpd 显示所有名称中包含 "httpd" 字样的rpm包 
 8. rpm -qi package_name 获取一个已安装包的特殊信息 
 9. rpm -qg "System Environment/Daemons" 显示一个组件的rpm包 
 10. rpm -ql package_name 显示一个已经安装的rpm包提供的文件列表 
 11. rpm -qc package_name 显示一个已经安装的rpm包提供的配置文件列表 
 12. rpm -q package_name --whatrequires 显示与一个rpm包存在依赖关系的列表 
 13. rpm -q package_name --whatprovides 显示一个rpm包所占的体积 
 14. rpm -q package_name --scripts 显示在安装/删除期间所执行的脚本l 
 15. rpm -q package_name --changelog 显示一个rpm包的修改历史 
 16. rpm -qf /etc/httpd/conf/httpd.conf 确认所给的文件由哪个rpm包所提供 
 17. rpm -qp package.rpm -l 显示由一个尚未安装的rpm包提供的文件列表 
 18. rpm --import /media/cdrom/RPM-GPG-KEY 导入公钥数字证书 
 19. rpm --checksig package.rpm 确认一个rpm包的完整性 
 20. rpm -qa gpg-pubkey 确认已安装的所有rpm包的完整性 
 21. rpm -V package_name 检查文件尺寸、 许可、类型、所有者、群组、MD5检查以及最后修改时间 
 22. rpm -Va 检查系统中所有已安装的rpm包- 小心使用 
 23. rpm -Vp package.rpm 确认一个rpm包还未安装 
 24. rpm2cpio package.rpm \| cpio --extract --make-directories \*bin\* 从一个rpm包运行可执行文件 
 25. rpm -ivh /usr/src/redhat/RPMS/\`arch`/package.rpm 从一个rpm源码安装一个构建好的包 
 26. rpmbuild --rebuild package_name.src.rpm 从一个rpm源码构建一个 rpm 包


####YUM 软件包升级器 - （Fedora, RedHat及类似系统）

 1. yum install package_name 下载并安装一个rpm包 
 2. yum localinstall package_name.rpm 将安装一个rpm包，使用你自己的软件仓库为你解决所有依赖关系 
 3. yum update package_name.rpm 更新当前系统中所有安装的rpm包 
 4. yum update package_name 更新一个rpm包 
 5. yum remove package_name 删除一个rpm包 
 6. yum list 列出当前系统中安装的所有包 
 7. yum search package_name 在rpm仓库中搜寻软件包 
 8. yum clean packages 清理rpm缓存删除下载的包 
 9. yum clean headers 删除所有头文件 
 10. yum clean all 删除所有缓存的包和头文件


####DEB 包 (Debian, Ubuntu 以及类似系统)

 1. dpkg -i package.deb 安装/更新一个 deb 包 
 2. dpkg -r package_name 从系统删除一个 deb 包 
 3. dpkg -l 显示系统中所有已经安装的 deb 包 
 4. dpkg -l \| grep httpd 显示所有名称中包含 "httpd" 字样的deb包 
 5. dpkg -s package_name 获得已经安装在系统中一个特殊包的信息 
 6. dpkg -L package_name 显示系统中已经安装的一个deb包所提供的文件列表 
 7. dpkg --contents package.deb 显示尚未安装的一个包所提供的文件列表 
 8. dpkg -S /bin/ping 确认所给的文件由哪个deb包提供

####APT 软件工具 (Debian, Ubuntu 以及类似系统)

 1. apt-get install package_name 安装/更新一个 deb 包
 2. apt-cdrom install package_name 从光盘安装/更新一个 deb 包 
 3. apt-get update 升级列表中的软件包 
 4. apt-get upgrade 升级所有已安装的软件 
 5. apt-get remove package_name 从系统删除一个deb包 
 6. apt-get check 确认依赖的软件仓库正确 
 7. apt-get clean 从下载的软件包中清理缓存 
 8. apt-cache search searched-package 返回包含所要搜索字符串的软件包名称

####查看文件内容

 1. cat file1 从第一个字节开始正向查看文件的内容 
 2. tac file1 从最后一行开始反向查看一个文件的内容 
 3. more file1 查看一个长文件的内容 
 4. less file1 类似于 'more' 命令，但是它允许在文件中和正向操作一样的反向操作 
 5. head -2 file1 查看一个文件的前两行 
 6. tail -2 file1 查看一个文件的最后两行 
 7. tail -f /var/log/messages 实时查看被添加到一个文件中的内容


####文本处理

 1. cat file1 file2 ... \| command <> file1_in.txt_or_file1_out.txt general syntax for text manipulation using PIPE, STDIN and STDOUT 
 2. cat file1 \| command( sed, grep, awk, grep, etc...) > result.txt 合并一个文件的详细说明文本，并将简介写入一个新文件中 
 3. cat file1 \| command( sed, grep, awk, grep, etc...) >> result.txt 合并一个文件的详细说明文本，并将简介写入一个已有的文件中 
 4. grep Aug /var/log/messages 在文件 '/var/log/messages'中查找关键词"Aug" 
 5. grep ^Aug /var/log/messages 在文件 '/var/log/messages'中查找以"Aug"开始的词汇 
 6. grep [0-9] /var/log/messages 选择 '/var/log/messages' 文件中所有包含数字的行 
 7. grep Aug -R /var/log/* 在目录 '/var/log' 及随后的目录中搜索字符串"Aug" 
 8. sed 's/stringa1/stringa2/g' example.txt 将example.txt文件中的 "string1" 替换成 "string2" 
 9. sed '/^$/d' example.txt 从example.txt文件中删除所有空白行 
 10. sed '/ *#/d; /^$/d' example.txt 从example.txt文件中删除所有注释和空白行 
 11. echo 'esempio' \| tr '[:lower:]' '[:upper:]' 合并上下单元格内容 
 12. sed -e '1d' result.txt 从文件example.txt 中排除第一行 
 13. sed -n '/stringa1/p' 查看只包含词汇 "string1"的行 
 14. sed -e 's/ *$//' example.txt 删除每一行最后的空白字符 
 15. sed -e 's/stringa1//g' example.txt 从文档中只删除词汇 "string1" 并保留剩余全部 
 16. sed -n '1,5p;5q' example.txt 查看从第一行到第5行内容 
 17. sed -n '5p;5q' example.txt 查看第5行 
 18. sed -e 's/00*/0/g' example.txt 用单个零替换多个零 
 19. cat -n file1 标示文件的行数 
 20. cat example.txt \| awk 'NR%2==1' 删除example.txt文件中的所有偶数行 
 21. echo a b c \| awk '{print $1}' 查看一行第一栏 
 22. echo a b c \| awk '{print $1,$3}' 查看一行的第一和第三栏 
 23. paste file1 file2 合并两个文件或两栏的内容 
 24. paste -d '+' file1 file2 合并两个文件或两栏的内容，中间用"+"区分 
 25. sort file1 file2 排序两个文件的内容 
 26. sort file1 file2 \| uniq 取出两个文件的并集(重复的行只保留一份) 
 27. sort file1 file2 \| uniq -u 删除交集，留下其他的行 
 28. sort file1 file2 \| uniq -d 取出两个文件的交集(只留下同时存在于两个文件中的文件) 
 29. comm -1 file1 file2 比较两个文件的内容只删除 'file1' 所包含的内容 
 30. comm -2 file1 file2 比较两个文件的内容只删除 'file2' 所包含的内容 
 31. comm -3 file1 file2 比较两个文件的内容只删除两个文件共有的部分
 

####字符设置和文件格式转换

 1. dos2unix filedos.txt fileunix.txt 将一个文本文件的格式从MSDOS转换成UNIX 
 2. unix2dos fileunix.txt filedos.txt 将一个文本文件的格式从UNIX转换成MSDOS 
 3. recode ..HTML < page.txt > page.html 将一个文本文件转换成html 
 4. recode -l \| more 显示所有允许的转换格式

####文件系统分析

 1. badblocks -v /dev/hda1 检查磁盘hda1上的坏磁块 
 2. fsck /dev/hda1 修复/检查hda1磁盘上linux文件系统的完整性 
 3. fsck.ext2 /dev/hda1 修复/检查hda1磁盘上ext2文件系统的完整性
 4. e2fsck /dev/hda1 修复/检查hda1磁盘上ext2文件系统的完整性 
 5. e2fsck -j /dev/hda1 修复/检查hda1磁盘上ext3文件系统的完整性 
 6. fsck.ext3 /dev/hda1 修复/检查hda1磁盘上ext3文件系统的完整性 
 7. fsck.vfat /dev/hda1 修复/检查hda1磁盘上fat文件系统的完整性 
 8. fsck.msdos /dev/hda1 修复/检查hda1磁盘上dos文件系统的完整性 
 9. dosfsck /dev/hda1 修复/检查hda1磁盘上dos文件系统的完整性 


####初始化一个文件系统

 1. mkfs /dev/hda1 在hda1分区创建一个文件系统 
 2. mke2fs /dev/hda1 在hda1分区创建一个linux ext2的文件系统 
 3. mke2fs -j /dev/hda1 在hda1分区创建一个linux ext3(日志型)的文件系统 
 4. mkfs -t vfat 32 -F /dev/hda1 创建一个 FAT32 文件系统 
 5. fdformat -n /dev/fd0 格式化一个软盘 
 6. mkswap /dev/hda3 创建一个swap文件系统


####SWAP文件系统

 1. mkswap /dev/hda3 创建一个swap文件系统
 2. swapon /dev/hda3 启用一个新的swap文件系统 
 3. swapon /dev/hda2 /dev/hdb3 启用两个swap分区 

####备份

 1. dump -0aj -f /tmp/home0.bak /home 制作一个 '/home' 目录的完整备份
 2. dump -1aj -f /tmp/home0.bak /home 制作一个 '/home' 目录的交互式备份 
 3. restore -if /tmp/home0.bak 还原一个交互式备份 
 4. rsync -rogpav --delete /home /tmp 同步两边的目录 
 5. rsync -rogpav -e ssh --delete /home ip_address:/tmp 通过SSH通道rsync 
 6. rsync -az -e ssh --delete ip_addr:/home/public /home/local 通过ssh和压缩将一个远程目录同步到本地目录 
 7. rsync -az -e ssh --delete /home/local ip_addr:/home/public 通过ssh和压缩将本地目录同步到远程目录 
 8. dd bs=1M if=/dev/hda \| gzip \| ssh user@ip_addr 'dd of=hda.gz' 通过ssh在远程主机上执行一次备份本地磁盘的操作 
 9. dd if=/dev/sda of=/tmp/file1 备份磁盘内容到一个文件 
 10. tar -Puf backup.tar /home/user 执行一次对 '/home/user' 目录的交互式备份操作 
 11. ( cd /tmp/local/ && tar c . ) \| ssh -C user@ip_addr 'cd /home/share/ && tar x -p' 通过ssh在远程目录中复制一个目录内容 
 12. ( tar c /home ) \| ssh -C user@ip_addr 'cd /home/backup-home && tar x -p' 通过ssh在远程目录中复制一个本地目录 
 13. tar cf - . \| (cd /tmp/backup ; tar xf - ) 本地将一个目录复制到另一个地方，保留原有权限及链接 
 14. find /home/user1 -name '*.txt' \| xargs cp -av --target-directory=/home/backup/ --parents 从一个目录查找并复制所有以 '.txt' 结尾的文件到另一个目录 
 15. find /var/log -name '*.log' \| tar cv --files-from=- \| bzip2 > log.tar.bz2 查找所有以 '.log' 结尾的文件并做成一个bzip包 
 16. dd if=/dev/hda of=/dev/fd0 bs=512 count=1 做一个将 MBR (Master Boot Record)内容复制到软盘的动作 
 17. dd if=/dev/fd0 of=/dev/hda bs=512 count=1 从已经保存到软盘的备份中恢复MBR内容



####光盘

 1. cdrecord -v gracetime=2 dev=/dev/cdrom -eject blank=fast -force 清空一个可复写的光盘内容 
 2. mkisofs /dev/cdrom > cd.iso 在磁盘上创建一个光盘的iso镜像文件 
 3. mkisofs /dev/cdrom \| gzip > cd_iso.gz 在磁盘上创建一个压缩了的光盘iso镜像文件 
 4. mkisofs -J -allow-leading-dots -R -V "Label CD" -iso-level 4 -o ./cd.iso data_cd 创建一个目录的iso镜像文件 
 5. cdrecord -v dev=/dev/cdrom cd.iso 刻录一个ISO镜像文件 
 6. gzip -dc cd_iso.gz \| cdrecord dev=/dev/cdrom - 刻录一个压缩了的ISO镜像文件 
 7. mount -o loop cd.iso /mnt/iso 挂载一个ISO镜像文件 
 8. cd-paranoia -B 从一个CD光盘转录音轨到 wav 文件中 
 9. cd-paranoia -- "-3" 从一个CD光盘转录音轨到 wav 文件中（参数-3）
 10. cdrecord --scanbus 扫描总线以识别scsi通道 
 11. dd if=/dev/hdc \| md5sum 校验一个设备的md5sum编码，例如一张 CD



####网络 - （以太网和WIFI无线）

 1. ifconfig eth0 显示一个以太网卡的配置
 2. ifup eth0 启用一个 'eth0' 网络设备 
 3. ifdown eth0 禁用一个 'eth0' 网络设备 
 4. ifconfig eth0 192.168.1.1 netmask 255.255.255.0 控制IP地址 
 5. ifconfig eth0 promisc 设置 'eth0' 成混杂模式以嗅探数据包 (sniffing) 
 6. dhclient eth0 以dhcp模式启用 'eth0' 