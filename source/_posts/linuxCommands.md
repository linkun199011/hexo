---
title: Linux常用命令
date: 2017-08-20 02:21:49
tags: linux
---

#  罗列常用的linux命令

<!-- more -- >

## 查找命令


```

// find some files 
find . -name "*abc"

// when you excute : sudo apt-get install something 
// E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
// you should just 
sudo rm /var/lib/apt/lists/lock

// note: the src and dest should be full path, otherwise it won't work
ln -s [src path] [dest path]


// 全局替换

：%s/vivian/sky/g
:%s/Log\./Logger\./g   // 将全局的Log. 改成 Logger.

// 删除是排除某个文件
rm -rf !(filename)

grep ‘energywise’ *           #在当前目录搜索带'energywise'行的文件

grep -r ‘energywise’ *        #在当前目录及其子目录下搜索'energywise'行的文件
grep -l -r ‘energywise’ *     #在当前目录及其子目录下搜索'energywise'行的文件，但是不显示匹配的行，只显示匹配的文件

#安装deb

 dpkg -i 安装包名字


```

## 解压命令

```
# 解压 / 压缩 rar 文件
rar e aa.rar # 将aa.rar压缩文件解压到当前目录，aa文件中原包含的目录全没有。
rar x aa.rar # 将aa.rar压缩文件解压到aa目录下，并保持原来压缩之前aa文件的目录组织结构。
unrar x aa.rar + 路径名 # 解压到该路径下  x参数 是解压到一个文件夹里 
unrar e aa.rar          # e参数是把所有文件解压到当前目录下  注意这个命令比较特殊参数之前不能加-

# 解压 / 压缩 zip 文件

unzip xx.zip # 解压zip文件到当前目录
unzip -d folderName xx.zip # 解压zip文件到 folderName 文件夹下。
unzip -O CP936 xxx.zip (用GBK, GB18030也可以)

# 解压 / 压缩 tar.xz文件：

$xz -d ***.tar.xz  # -先 xz -d xxx.tar.xz 将 xxx.tar.xz解压成 xxx.tar 

$tar -xvf  ***.tar  # -然后，再用 tar xvf xxx.tar来解包。

解压：tar xvfz xxx.tar.gz. 压缩：tar czf xxx.tar.gz xxxx



# 解压tar.gz文件：
tar -xzvf .tar.gz

 tar [-cxtzjvfpPN] 文件与目录 .... 
      参数： 
      -c ：建立一个压缩文件的参数指令(create 的意思)； 
      -x ：解开一个压缩文件的参数指令！ 
      -t ：查看 tarfile 里面的文件！ 
      特别注意，在参数的下达中， c/x/t 仅能存在一个！不可同时存在！ 
      因为不可能同时压缩与解压缩。 
      -z ：是否同时具有 gzip 的属性？亦即是否需要用 gzip 压缩？ 
      -j ：是否同时具有 bzip2 的属性？亦即是否需要用 bzip2 压缩？ 
      -v ：压缩的过程中显示文件！这个常用，但不建议用在背景执行过程！ 
      -f ：使用档名，请留意，在 f 之后要立即接档名喔！不要再加参数！


tar -xvf xx.tar

# tar -cjf all.tar.bz2 *.jpg 
这条命令是将所有.jpg的文件打成一个tar包，并且将其用bzip2压缩，生成一个 
bzip2压缩过的包，包名为all.tar.bz2 
# tar -xjf all.tar.bz2 
这条命令是将上面产生的包解开


```

## Other

```
strace -o ps_output ps  //将ps的strace 结果输出到ps_output中
lsmod：查看系统正在加载的模块

edb的安装：
# apt-get install qt4-dev-tools
# apt-get install libboost-dev
（如果报 依赖包错误，解决方案见 http://blog.csdn.net/zhaowenchaofang/article/details/8916324）
安装g++ 
#apt-get install g++
下载 debugger  网址  http://www.codef00.com/projects#Debugger
注意下载的是    debugger-0.9.18
# tar -zvxf debugger-0.9.18.tgz
#mv debugger /usr/local/src/
#cd /usr/local/src/debugger
#qmake
#make
#make install
#exit
$edb


```
