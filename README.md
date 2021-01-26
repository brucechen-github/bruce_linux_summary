# linux_ecs_summary
summarize linux knowledge

=========================GIT===============================

Q1: Permissions 0644 for '/root/.ssh/id_rsa' are too open.

A: chmod 600 /root/.ssh/id_rsa

============================================================

Q2: Git SSH

A: ssh-keygen -t rsa -C "your_email@xxx.com"

============================================================

Q3: Git Config

A: git config --global user.name "your_name"
   git config --global user.email "your_email"

============================================================

Q4: 


============================================================

HuaWei ECS 11/5/2020  
```
https://mirrors.huaweicloud.com/
```
============================================================

=========================Docker=============================
```
1. 安装: 
   1)下载repo: wget -O /etc/yum.repos.d/docker-ce.repo https://repo.huaweicloud.com/docker-ce/linux/centos/docker-ce.repo
   2)软件仓库地址替换: sudo sed -i 's+download.docker.com+repo.huaweicloud.com/docker-ce+' /etc/yum.repos.d/docker-ce.repo
   3) yum install docker-ce
2. 运行:   
   systemctl start docker
```   

```
3. 运行Mysql8
   1) docker run --name bruce-mysql -e MYSQL_ROOT_PASSWORD=123456 -p 3306:3306 -d mysql:latest
   2) 替换加密caching_sha2_password -> mysql_native_password
      1.mysql -uroot -p
      2.use mysql;
      3.ALTER USER 'root'@'localhost' IDENTIFIED BY '123456' PASSWORD EXPIRE NEVER;
      4.ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
      5.ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY '123456';
      6.flush privileges;
```
============================================================

=========================user=============================
```
useradd bruce
passwd bruce
```
=========================jdk=============================

yum install java-1.8.0 
```
查找java路径
ls -lrt /usr/bin/java
ls -lrt /etc/alternatives/java
/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el7_8.x86_64/jre/bin/java
export JAVA_HOME=/usr/lib/jvm/java-1.8.0-openjdk-1.8.0.262.b10-0.el7_8.x86_64
export JRE_HOME=$JAVA_HOME/jre

启动tomcat，才能成功
```

=========================maven=============================
```
1. 安装
  1)wget https://mirrors.bfsu.edu.cn/apache/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
  2)tar -zxvf apache-maven-3.6.3-bin.tar.gz
  3)vim /etc/profile
  4)
  export M2_HOME=/home/bruce/apache-maven-3.6.3
  export PATH=$PATH:$M2_HOME/bin
  5)source /etc/profile
```

=========================nodejs=============================
```
1. 安装
   1)wget https://nodejs.org/dist/v14.15.0/node-v14.15.0-linux-x64.tar.xz
   2)tar -xvf node-v14.15.0-linux-x64.tar.xz
   3)ln -s /home/bruce/node-v14.15.0-linux-x64/bin/npm /usr/local/bin/
   4)ln -s /home/bruce/node-v14.15.0-linux-x64/bin/node /usr/local/bin/
2. 
npm install @vue/cli
3.
npm config

npm config set registry https://repo.huaweicloud.com/repository/npm/
npm config set sass_binary_site https://repo.huaweicloud.com/node-sass
npm config set phantomjs_cdnurl https://repo.huaweicloud.com/phantomjs
npm config set chromedriver_cdnurl https://repo.huaweicloud.com/chromedriver
npm config set operadriver_cdnurl https://repo.huaweicloud.com/operadriver
npm config set electron_mirror https://repo.huaweicloud.com/electron/
npm config set python_mirror https://repo.huaweicloud.com/python

```

```
# tar -zxvf Python-3.6.1.tgz
进入解压后的目录，编译安装。
# cd Python-3.6.1
# ./configure --prefix=/usr/local/python3
# make && make install

建立python3的软链
# ln -s /usr/local/python3/bin/python3 /usr/bin/python3

```
=========================pip3=============================  


mkdir ~/.pip/pip.conf

```
[global]
index-url = https://repo.huaweicloud.com/repository/pypi/simple
trusted-host = repo.huaweicloud.com
timeout = 120
```

=========================nginx=============================
```
1. 安装
   1)wget https://repo.huaweicloud.com/nginx/nginx-1.19.4.tar.gz
     yum -y install gcc pcre-devel zlib-devel openssl openssl-devel
   2)cd nginx-1.19.4
   3)./configure --prefix=/usr/local/nginx
   4)make
     make install
     cd /usr/local/nginx/
   5)ln -s /usr/local/nginx/sbin/nginx /usr/local/bin/
```
=========================挂载硬盘=============================
```
1.	fdisk -l  查看是否有硬盘
	df -h
2.	fdisk /dev/vdb  #进入到没有挂载的硬盘
 
	第一次输入p进入分区
	第二次输入n创建新的分区
	第三次选中p
	第四次输入编号1 并回车两次写入配置
	第五次输入w
3.	再次查看磁盘
	fdisk -l
	现在已经显示但是不能用
4.	对新硬盘进行格式化
	mkfs.ext4 /dev/vdb  对创建的硬盘捷星格式化
	partprobe  不重启的情况下发现硬盘
	mkdir /data 创建挂载目录
	mount /dev/vdb /data
	df -h 查看是否成功
	vi /etc/fstab   开机挂载硬盘
```

=========================Jenkins & Tomcat=========================
```
Mirror: https://mirrors.tuna.tsinghua.edu.cn/jenkins/updates/update-center.json
Tomcat bin/start.sh
修改端口号 conf/server.xml
```

