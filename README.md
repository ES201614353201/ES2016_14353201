
##DOL框架描述
DOL是一个能让自动化应用映射到多处理器上的结构平台。
它包含了三部分:
1. 应用层接口
2. 功能仿真
3. 映射优化

---

##DOL配置过程
---
1. 配置必要的环境
    * sudo apt-get update
    * sudo apt-get install  unzip
2. 安装Linux命令安装不了的环境
    1. 安装ant
        * 从官网下载ant安装包
        * tar -xf apache-ant-1.8.2-bin.tar.gz解压
        * 将文件移动到/opt/下：sudo mv apache-ant-1.8.2 /opt/
        * 配置环境变量：sudo gedit /etc/profile，在原来基础上添加以下蓝体字：
     `export ANT_HOME=/opt/apache-ant-1.8.2`
    2. 安装jdk-8u40-linux-x64.gz
        * 将安装包解压到 /usr/lib/java
         `cd /usr/lib`
         `sudo mkdir java`
        * 进入安装包下载所在路径
         `sudo tar zxvf ./jdk-8u40-linux-x64.gz -C /usr/lib/java`
        * 重命名为jdk8
         `cd /usr/lib/java`
         `sudo mv jdk1.8.0_40/ jdk8`
        * 配置环境变量
         `gedit ~/.bashrc`
        * 在打开的文件的末尾添加JDK所在路径
         `export JAVA_HOME=/usr/lib/java/jdk8`
         `export JRE_HOME=${JAVA_HOME}/jre`
         `export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib`
         `export PATH=${JAVA_HOME}/bin:$PATH`
        * 保存退出，然后输入下面的命令来使之生效
         `source ~/.bashrc`
        * 配置默认JDK /usr/lib/java/jdk8/为JDK所在路径
         `sudo update-alternatives --install /usr/bin/java java /usr/lib/java/jdk8/bin/java 300`
         `sudo update-alternatives --install /usr/bin/javac javac /usr/lib/java/jdk8/bin/javac 300`
        * 查看当前各种JDK版本和配置: 链接组 java (提供 /usr/bin/java)中只有一个候选项：/usr/lib/java/jdk8/bin/java无需配置。
         ` sudo update-alternatives --config java`
        * 通过一下命令验证配置是否成功
         `java -version`
         `java`
         `javac`
3. 解压文件
    * 新建dol的文件夹
     `sudo mkdir dol`
    * 将dolethz.zip解压到 dol文件夹中
     `sudo unzip dol_ethz.zip -d dol`
    * 解压systemc
     `sudo tar -zxvf systemc-2.3.1.tgz`
4. 编译systemc
    * 解压后进入systemc-2.3.1的目录下
     `cd systemc-2.3.1`
    * 新建一个临时文件夹objdir
     `sudo mkdir objdir`
    * 进入该文件夹objdir
     `cd objdir`
    * 运行configure(能根据系统的环境设置一下参数，用于编译)
     `sudo ../configure CXX=g++ --disable-async-updates`
    [结果图](http://yun.baidu.com/share/link?shareid=2114761651&uk=2533959007)
    * 编译
     `sudo make install`
    * 记录当前的工作路径
     `sudo pwd`
    [结果图](http://yun.baidu.com/share/link?shareid=2156269802&uk=2533959007)
 5. 编译dol
    * 进入刚刚dol的文件夹
     `cd ../dol`
    * 修改build_zip.xml文件
     `sudo gedit build_zip.xml`
    * 找到下面这段话，就是说上面编译的systemc位置在哪里
    `<property name="systemc.inc" value="YYY/include"/>`
    `<property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>`
    把YYY改成上页pwd的结果（注意，对于64位系统的机器，lib-linux要改 成lib-linux64）
    * 编译
     `sudo ant -f build_zip.xml all`
    * 进入build/bin/mian路径下
     `cd build/bin/main`
    * 运行第一个例子
     `sudo ant -f runexample.xml -Dnumber=1`
[结果图](http://yun.baidu.com/share/link?shareid=3798913449&uk=2533959007)



    