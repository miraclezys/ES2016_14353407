---
title: DOL开发环境配置
grammar_cjkRuby: true
---
#DOL开发环境配置


#### **DOL框架描述**
 The distributed operation layer (DOL) is a software development framework to program parallel applications. The DOL allows to specify applications based on the Kahn process network model of computation and features a simulation engine based on SystemC. Moreover, the DOL provides an XML-based specification format to describe the implementation of a parallel application on a multi-processor systems, including binding and mapping.

The DOL consists of basically three parts:
* DOL Application Programming Interface
* DOL Functional Simulation
* DOL Mapping Optimization

> www.tik.ee.ethz.ch/~shapes/dol.html


#### **安装Ubuntu**
因为本次实验需要在linux环境下进行，所以需要安装Ubuntu
> VMWARE教程：http://jingyan.baidu.com/article/0320e2c1ef9f6c1b87507bf6.html

> VIRTUALBOX教程：http://jingyan.baidu.com/article/cdddd41c5eea3153ca00e160.html

> Ubuntu下载：http://www.ubuntu.com/download/desktop

#### **安装必要的环境**
打开以安装好的Ubuntu，打开终端（Ctrl+Alt+T）
```
$	sudo apt-get update
$	sudo apt-get install ant
$ 	sudo apt-get install openjdk-7-jdk
$	sudo apt-get install unzip
```

#### **下载需要的软件**
```
$   sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
$   sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```

#### **解压文件**
1. 新建名为dol的文件夹

    ```
    $	mkdir dol
    ```
2. 将dolethz.zip解压到 dol文件夹中

    ```
    $	unzip dol_ethz.zip -d dol
    ```
3. 解压systemc

    ```
    $	tar -zxvf systemc-2.3.1.tgz
    ```

#### **编译systemc**
1. 解压后进入systemc-2.3.1的目录下

    ```
    $	cd systemc-2.3.1
    ```
2. 新建一个临时文件夹objdir

    ```
    $	mkdir objdir
    ```
3. 进入该文件夹objdir

    ```
    $	cd objdir
    ```
4. 运行configure(能根据系统的环境设置一下参数，用于编译)

    ```
    $	../configure CXX=g++ --disable-async-updates
    ```

	图为运行了configure之后的截图:

	![图为运行了configure之后的截图](/home/shushu/ES2016_14353407/img/1.jpg)

5. 编译

    ```
    $	sudo make install
    ```
6. 编译完后文件目录如下图

    ```
    $   cd ..
    $   ls
    ```
	编译完后文件目录如下:
    ![enter description here](/home/shushu/ES2016_14353407/img/2.jpg)
7. 记录当前的工作路径(记录下来，待会需要使用)

    ```
    $	pwd
    ```
	例如我的当前路径是：home/shushu/systemc-2.3.1
    ![enter description here](https://raw.githubusercontent.com/miraclezys/ES2016_14353407/master/img/3.jpg)


#### **编译dol**
1. 进入刚刚的dol文件夹

    ```
    $	cd ../dol
    ```
2. 修改build_zip.xml文件
    找到下面这段话，也是说上面编译的systemc位置在哪里

    ```
    <property name="systemc.inc" value="YYY/include"/>
    <property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
    ```

    把YYY改成上一步pwd的结果（注意，对于64位系统的机器，需要把lib-linux改成lib-linux64）
3. 然后是编译

    ```
    $	ant -f build_zip.xml all
    ```
4. 若成功会显示build successful

     ![若成功会显示build successful](https://raw.githubusercontent.com/miraclezys/ES2016_14353407/master/img/4.jpg)

#### **运行第一个例子**
1. 进入build/bin/mian路径下

    ```
    $	cd build/bin/main
    ```
2. 然后运行第一个例子

    ```
    $	ant -f runexample.xml -Dnumber=1
    ```
3. 成功结果如图

    ![成功结果](https://raw.githubusercontent.com/miraclezys/ES2016_14353407/master/img/5.jpg)

#### **实验心得**
首先，熟悉了markdown的语法，然后对dol开发环境的配置过程有了进一步的印象加深。写这份报告主要的困难如何插入图片，我的解决办法是先将图片上传到GitHub的仓库中，生成链接就能直接用于markdowm的图片插入了






 
