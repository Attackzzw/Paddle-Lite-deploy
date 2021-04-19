# 手把手教你 通过使用 Android studio  实现Paddle lite部署 手机app
#### **此次主要熟悉怎么部署手机应用，**
#### 环境：[Android studio](http://www.android-studio.org/)，[Paddle-lite](https://github.com/PaddlePaddle/Paddle-Lite-Demo) , windows 10， 一部安卓手机

<table>
  <tr>
        <td ><center><img src="https://ai-studio-static-online.cdn.bcebos.com/5b3ca43ae2a04ba3b275c460aa457c0dabebfc497bed4a35828c84cf93eeeb26" >图1</center></td>
        <td ><center><img src="https://ai-studio-static-online.cdn.bcebos.com/18c0a864715849a68f4bc79b50eb3a0bed239ef1d319478fbd3887c0fa21f53b" >图2</center></td>
    </tr>
    <tr>
        <td ><center><img src="https://ai-studio-static-online.cdn.bcebos.com/17615e0d7c7048f3a032afde5fa933a463405c6023d7422cbc4addb27fa9e8c0" >图3</center></td>
        <td ><center><img src="https://ai-studio-static-online.cdn.bcebos.com/9474f7a7616e4eb9adef47379e4240e78d40452ab54749f087ffc4f83a990106" >图4</center></td>
    </tr>

</table>



# 一，环境安装



### 部署到手机前需要安装Android Studio和jdk 也就是java的环境。我的电脑是64位系统，所以jdk是64位的，已经公开在数据集，项目内已经包含([需要32位的点这里](https://www.oracle.com/cn/java/technologies/javase/javase-jdk8-downloads.html))

## 配置环境变量
*  安装jdk（安装包在此项目挂载的数据集里（win），或者[点这里](https://www.oracle.com/cn/java/technologies/javase/javase-jdk8-downloads.html)）
*  jdk安装不在陈述（傻瓜下一步），安装完jdk，接下来要配置下系统环境变量：
*  右键计算机->属性->高级系统设置->环境变量
*  这里的JAVA_HOME 就是刚才jdk安装的目录
*  在系统变量 path 里面添加：  %JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;  （注意不要落下‘;’）

![](https://ai-studio-static-online.cdn.bcebos.com/bb72c39d43824f29b258ac4ca32a0f45347e23db03124f91a67011a89217e049)

![](https://ai-studio-static-online.cdn.bcebos.com/4c01175b3973499087a1c8fa06b869f1e70c135d44fe42b18d9fa47c1ae4eab5)

## 安装[Android studio](http://www.android-studio.org/)
#### 下载地址：[Android studio](http://www.android-studio.org/)
*  **这里注意自己的系统，Windows，Mac，Linux， （实例这里是Windows滴Android Studio）**
*  **下载完安装包，傻瓜下一步就可以了，注意！如果在虚拟手机里测试，需要在“选择组件”那选上Android virtual device**

![](https://ai-studio-static-online.cdn.bcebos.com/b99bef824e92493c8731b6d9316a5bb7ee2eba9b678e430287bb7d87db763403)


*   **安装SDK(开发包)，依次选择File---->Settings---->Appearance & Behavior---->System Settings---->Android SDK**

	 **选择需要的安卓版本进行安装（也就是自己手机的安卓版本）**


![](https://ai-studio-static-online.cdn.bcebos.com/cc231e8274f445c7b0a21db73d0376fa3ef2e9b2e8034cc7b9469eb46d7b593f)
     


*   **安装好后，进入界面**
   
   **依次选择File---->Othor Settings---->Defaut Project Structure**

![](https://ai-studio-static-online.cdn.bcebos.com/026b89e964ad4b47aff94f1eef1980dcef6eefde075f4546a52bef1f8ebf0b89)

*   **接下来依次配置**

	**1.Android SDK的路径（刚才安装SDK的安装路径）**

	**2.Android NDK的路径（本次没有用到，不需要)**

	**3.JDK的路径**

![](https://ai-studio-static-online.cdn.bcebos.com/04a000e9a1874b8eba53dbc0559866fb188bca8c71ce4dc99dfc45fe4521de83)

### 配置SDK的系统变量
*   **新建变量名字:Android_HOME    值为 “SDK 安装的路径;SDK路径/platform-tools”**

*   **在系统变量 path中加入  %Android_HOME%**
    
![](https://ai-studio-static-online.cdn.bcebos.com/ec1c86924b00435ea99397157186a29d72e5ad6aaa8147ceaae893304cac698d)


## **安装完毕，准备就绪**

# 二，导入Paddle lite项目

## **使用paddle lite的mask_detection_demo**

*   **首先去[Paddle-lite](https://github.com/PaddlePaddle/Paddle-Lite-Demo)下载安卓Demo**
		 地址在GitHub，大约3Mb，虽然文件不大，但是由于是外网，很慢，等会就好了
      下载zip后解压到目录   

*   **解压完成，打开Android studio，点击open 在弹出的对话框中寻找自己刚解压的目录项目，OK**
		

![](https://ai-studio-static-online.cdn.bcebos.com/377f53d651c7492991de39cd9c8afa7e3d0984f643154908bae77e4fcdeb898b)


# 三，连接手机
#### 以上工作准备就绪，连接手机在手机端查看效果
#### 手机连接电脑后，打开开发者模式以及usb调试（否则权限不够，app安装不成功）


# 四，调试


#### 1.    接下来让我们单击编译运行 Run 我们会发现报错：提示Received close_notify during handshake

#### 这里是因为某些包下载不起作用，解决方法参考[此处](https://blog.csdn.net/longbatianxia1/article/details/104447834?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.channel_param)
#### 因为我这里之前已经部署过了，所以有些问题可能已经解决过了，没有展现出来（官方的demo 没有问题，多数为兼容，更新问题）
#### 或者可以试下Android studio提示的下载（我之前也经过了好几道工序 才安装成功，一堆英文）
#### 这里很冗余，不一一截图了，如果大家有哪不明白的地方或者出问题的地方，欢迎评论，大家一起探讨安卓端的 Paddle Lite部署

# 五，效果展示

#### **经过一系列的调试，下载，终于可以了部署到手机了**

![](https://ai-studio-static-online.cdn.bcebos.com/c284d4be328f462bbfe077ec4bea1a4066c70fc0a749492b8096789888776768)

<table>
	<tr>
		<td ><center><img src="https://ai-studio-static-online.cdn.bcebos.com/80a83c329fb04ee2a1b8fa00893208f9cef4a7a78a41467e8e0c6a0d045e786d" >图1</center></td>
		<td ><center><img src="https://ai-studio-static-online.cdn.bcebos.com/6999cce3e97f425dad9a836923d0655f79d67f4e414646a69c11ea5ae2a35c1c" >图2</center></td>
	</tr>
</table>


# 六，总结

#### **paddle Lite很好，主要问题是在部署时使用的其他软件不太熟练，像还有树莓派上面的部署，或许会比这安卓的要简单些（虽然我也没有树莓派~）**

#### **安卓上面的部署，现在虽然用到的人不多，但是慢慢的，等到AI普及了，或许手机上的AI应用会越来越多**

#### **在Android studio 安装app的时候可能会出现报错，多数是某些版本老旧，在右下角显示 upgrade ，等更新完，再次安装就可以了**

####  **本人小白，若有不足之处，欢迎批评~**
