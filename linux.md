===================Linux=====================

1. Command:

  - ln 将一个文件创建链接 
       -s 创建软链接
       软链接：不可以删除源文件
       硬链接：可以删除源文件
     Example：ln -s /opt/software/nginx/sbin/nginx /usr/bin/nginx


   - tar 
        -x 解压缩
        -z gzip压缩
        -v 压缩过程中显示
	-f 文件名	 
     tar -zxvf node-v12.13.0.tar.gz -C /opt/software/




查看Linux占用内存/CPU最多的进程

可以使用以下命令查使用内存最多的10个进程     
ps -aux | sort -k4nr | head -n 10
 

可以使用一下命令查使用CPU最多的10个进程     
ps -aux | sort -k3nr | head -n 10



=================================================

Q1: 解决Linux "g++: Command not found"报错问题


A: yum install "gcc-c++.x86_64" -y






