##安装ROS
---
1. 建立源列表  
让电脑能够接受来自 packages.ros.org的软件  
`sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`  
2. 建立密钥  
`sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116`  
3. 安装ROS  
确保Debian的包的索引是最新的  
`sudo apt-get update`  
安装  
`sudo apt-get install ros-jade-desktop-full`  
4. 初始化rosdep  
rosdep能使你更方便的安装你想编译的源，并且它也是ROS一些内核运行时必要的东西。  
`sudo rosdep init`  
`rosdep update`  
5. 设置环境变量  
方便ROS运行时自动的添加你的bash会话。  
`echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc`  
`source ~/.bashrc`  
6. 安装rosinstall  
rosinstall是一个经常被用到的命令行工具。它能通过一句命令来下载很多你所要的ROS包的源树。  
`sudo apt-get install python-rosinstall`  


---
参考资料：http://wiki.ros.org/jade/Installation/Ubuntu




