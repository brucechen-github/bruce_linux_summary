=============node===================

1. 源代码安装 wget https://npm.taobao.org/mirrors/node/v12.13.0/node-v12.13.0.tar.gz

   ./configure
   make & make install
   

2. tar -xvf node-v12.13.0.tar.xz -C /opt/software/

3. ln -s /usr/local/application/nodejs/bin/npm /usr/local/bin/

4. vim /etc/profile

   export NODE_HOME=`/root/zuo/env/node-v8.11.3-linux-x64`{ 这里填解压之后node的路径}

   export PATH=$PATH:$NODE_HOME/bin

5. npm config set registry https://registry.npm.taobao.org ||  npm install cnpm -g --registry=https://registry.npm.taobao.org

6. install @angular/cli   npm install -g @angular/cli


==============python3================

yum install python3.x86_64

