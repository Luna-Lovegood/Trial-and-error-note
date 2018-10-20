这次是老师布置了一个**用java写TCP可靠传输**的大作业，本来觉得PPT那么详细环境配置应该问题不大，直到操作一下午跑不通test的我眼泪掉下来...... 非常感谢助教大大远程耐心指导！

* 首先我们需要搞到这些东西，然后先安装jdk-6-6u45-windows-i586 .exe：

![iBZRv6.jpg](https://s1.ax1x.com/2018/10/20/iBZRv6.jpg)

* 然后根据这个教程修改环境变量：
[https://jingyan.baidu.com/article/925f8cb836b26ac0dde0569e.html](https://jingyan.baidu.com/article/925f8cb836b26ac0dde0569e.html)

	p.s. 如果之前配置过jdk那么需要修改注册表路径：
[https://www.cnblogs.com/lazycxy/p/8821588.html](https://www.cnblogs.com/lazycxy/p/8821588.html)

**至此，java运行环境就配置好了：**

![iBm4tH.jpg](https://s1.ax1x.com/2018/10/20/iBm4tH.jpg)

* 接着来安装eclipse，需要下载JRE（关闭双击.exe的错误窗口后会弹出下载网址），我下载的是JRE1.8，这之后cmd中`java -version`命令会显示java版本为1.8而不是之前的1.6。
p.s. 安装好后会自动修改环境变量的PATH，无需手动配置啦~

* 记得安装最新版本: Eclipse SDK(64bit)_1@258711.exe

	前先装最新的JAVASE11：jdk-11.0.1\_windows-x64_bin

* 安装好eclipse后需要修改jre版本：在Eclipse中的Window下的Preference里的

	Java->Installed JREs中添加之前安装的JRE6，并选为默认的JRE:

![iBunIg.jpg](https://s1.ax1x.com/2018/10/20/iBunIg.jpg)

* 到这里还有一个坑（吐血），eclipse修改jdk版本后会报错，按照下面的教程修改编译器版本：[https://blog.csdn.net/z59d8m6e40/article/details/72836040?tdsourcetag=s_pctim_aiomsg](https://blog.csdn.net/z59d8m6e40/article/details/72836040?tdsourcetag=s_pctim_aiomsg)

* 终于快通关了......别急，还差一步，加入TCP\_Win_TestSys.jar类库后会显示（unbound），按照这个教程就可以解决啦：
[https://blog.csdn.net/cnzyyh/article/details/51115377](https://blog.csdn.net/cnzyyh/article/details/51115377)

开始运行TestRun.java，成功了！（我，一脸人间不值得.jpg，小凯的表情就是我的表情）

![iBnbG9.jpg](https://s1.ax1x.com/2018/10/20/iBnbG9.jpg)

![iBnvqK.jpg](https://s1.ax1x.com/2018/10/20/iBnvqK.jpg)


