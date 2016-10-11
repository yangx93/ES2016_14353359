# ES2016_14353359

linux环境下DOL的配置

Description

DOL（Distributed operation layer）它是一个软件开发框架来编程并行应用程序。 DOL允许基于Kahn过程网络计算模型来指定应用，并且基于SystemC的仿真引擎。 此外，DOL提供了基于XML的规范格式来描述并行应用在多处理器系统上的实现，包括绑定和映射。
Install

Ubuntu并配置好必要的环境

$ sudo apt-get update

$ sudo apt-get install ant

$ sudo apt-get install openjdk-7-jdk

$ sudo apt-get install unzip

一、下载文件

$ sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz

$ sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip

二、解压文件

1.新建dol文件

$ mkdir dol 2.将dolethz.zip解压到 dol文件夹中

$ unzip dol_ethz.zip -d dol 3.解压systemc

$ tar -zxvf systemc-2.3.1.tgz

三、编译systemc

1.解压后进入systemc-2.3.1的目录下

$ cd systemc-2.3.1 

2.新建一个临时文件夹objdir

$ mkdir objdir

3.进入该文件夹objdir

$ cd objdir

4.运行configure（能根据系统的环境设置一下参数，用于编译）

$ ../configure CXX=g++ --disable-async-updates

5.编译

$ sudo make install

6.记录当前的工作路径（会输出当前所在路径，记下来，待会有用）

$ pwd

四、编译DOL

1.进入刚刚的dol文件夹，修改build.xml文件 找到下面这段话，就是说上面编译的systemc位置在哪里

property name=”systemc.inc” value=”YYY/include” property name=”systemc.lib” value=”YYY/lib-linux/libsystemc.a”/ 把YYY改成上页pwd的结果（注意，对于 64位 系统的机器，lib-linux要改成lib-linux64）

2.编译

$ ant -f build_zip.xml all 若成功会显示build sucessful

3.运行第一个例子进入build/bin/main路径下

$ cd build/bin/main

4.然后运行第一个例子

$ ant -f runexample.xml -Dnumber=1

五、实验体会

这次实验主要完成dol开发环境的配置，由于第一次做，还是遇到很多问题。首先在配置的过程中有好多未安装的程序，这个问题不大，照着上面的提示做就行了。其次是在修改build_zip.xml文件的时候，我把lib_linux改成了lib_linux64，造成最后的例子运行时老是不成功，最后在TA的指导下才发现自己把电脑和虚拟机的系统类型弄混了。





