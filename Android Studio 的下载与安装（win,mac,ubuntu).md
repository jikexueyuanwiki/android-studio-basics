# 一、Android Studio 的下载与安装（win,mac,ubuntu)

标签（空格分隔）：androidstudio ubuntu win mac

---


* 官方下载地址（需翻墙）
http://developer.android.com/sdk/index.html
* 推荐国内镜像网站
http://www.androiddevtools.cn/#android-studio

##一、windows篇
建议大家下载集成了SDK的android studio版本，直接安装就可使用

![download.png](images\download.png)

#####事先准备：配置好jdk环境（这里不做过多介绍）
打开安装包，选择安装目录，一路到底。

若下载的不是集成了SDK的AS，则需下载配置一下SDK；


![sdkwin.png](images\sdkwin.png)

这里还是推荐下载第一个，因为exe在安装的过程中会配置好SDK的环境变量；

若下载的是压缩包版，则另需配置，如下：
>* 解压SDK压缩包
>* 在系统变量PATH里添加在变量值里加入androidSDK中platform-tools和tools的目录路径，这里我的是E:\android-sdk_r20.0.3-windows\android-sdk-windows\platform-tools和E:\adt-bundle-windows-x86_64-20130729\sdk\tools。
>* 完成后在CMD中输入abd,验证是否成功

之后打开android studio，在初始界面configura里配置好SDK目录。

![QQ截图20150507020558.png](images\QQ截图20150507020558.png)


##二、Mac篇
默认配置好JDK
android studio下载（并没有集成SDK）安装完成后需配置sdk目录
![downmac.png](images\downmac.png)
SDK下载
![sdkmac.png](images\sdkmac.png)
>* android-sdk环境变量配置
>1.启动Terminal终端工具
2.输入cd ~/ 进入当前用户的home目录

3. 创建：
touch .bash_profile
4.打开并编辑：
open .bash_profile
5、在文件中写入以下内容：export PATH=${PATH}:这里是platform-tools 的绝对路径，以我的为例：/Volumes/workplace/sdk/platform-tools/
6、执行如下命令：source .bash_profile 
7、验证：输入adb回车。如果未显示command not found，说明此命令有效，环境便亮设置完成。


##三、ubuntu篇
#### 配置顺序
java环境搭建->下载安装android studio->下载配置SDK->创建快捷方式



#### 1. java环境搭建
   ubuntu自带的是OpenJDK,这里还是推荐大家使用OrcalJDK,AS推荐使用的就是OrcalJDK.OpenJDK在编译的时候还是会出现一些问题的.
   
   
#####(一)添加软件源
* 先卸载openjdk
```shell
$ sudo apt-get purge openjdk* 
```
* 添加PPA(Personal Package Archives)
```shell
$ sudo apt-get install software-properties-common
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
```
* 安装jdk
```shell
$ sudo apt-get install oracle-java8-installer
```


#####(二)自行配置
######下载
oracle官网下载JDK压缩包(tar.gz格式)
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html


######创建java目录
 
```shell
 $sudo mkdir -p /usr/local/java
 $cd /usr/local/java 
 $sudo cp 下载目录下的jdk压缩包 当前目录下的jdk压缩包 
```
######解压
```shell
$sudo tar -zxvf jdk-8u25-linux-i586.tar.gz//解压
$sudo tar -zxvf jdk-8u25-linux-i586.tar.gz // 删除已解压的压缩包(注意名字对应) 
```

######配置环境变量
```shell
$sudo gedit /etc/profile 
```
在末尾加上如下部分：
JAVA_HOME=/usr/local/java/jdk1.8.0_25
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin export 
JAVA_HOME export PATH 
保存退出;

####配置ubuntu的JDK和JRE的位置 
    
```shell
$sudo update-alternatives --install "/usr/bin/java"  "java" "/usr/local/java/jdk1.8.0_25/bin/java" 1
$sudo update-alternatives --install "/usr/bin/javac"  "javac" "/usr/local/java/jdk1.8.0_25/bin/javac" 1  
$sudo update-alternatives --install "/usr/bin/javaws"  "javaws" "/usr/local/java/jdk1.8.0_25/bin/javaws" 1
```
######配置Oracle为系统默认JDK/JRE 
```shell
$sudo update-alternatives --set java /usr/local/java/jdk1.8.0_25/bin/java 
$sudo update-alternatives --set javac /usr/local/java/jdk1.8.0_25/bin/javac 
$sudo update-alternatives --set javaws /usr/local/java/jdk1.8.0_25/bin/javaws
```
配置完成后，执行如下命令使其立即生效。 
```
. /etc/profile 
```
###### 验证是否配置成功
环境变量配置完成后，在终端命令行中键盘敲入： java –version，出现jdk版本信息，而不是出错信息，即表示配置成功！ 



#### 2.android studio 的下载与安装

#### 下载

#### 解压安装
```shell
$sudo tar -zxvf 压缩包
```
解压完成后，进入bin/studio.sh，即为打开方式输入，直接在终端输入studio.sh即可打开；



#### 3.下载配置SDK
谷歌提供的linux版本的android studio并没有集成SDK,这需要我们自己下载，网址如上一致：

官方下载地址（需翻墙）
http://developer.android.com/sdk/index.html
推荐国内镜像网站
http://www.androiddevtools.cn/#android-studio

下载解压一般放在Android Studio的同一级目录；


####环境变量配置
```shell
cd ~/software/  说明：进入到保存sdk目录 
tar -zxvf android-sdk_r23.0.2-linux.tgz //解压sdk 
echo 'export ANDROID_HOME="'$HOME'/software/android-sdk-linux"' >> ~/.bashrc   //设置android环境变量 
echo 'export PATH="$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/platform-tools"' >> ~/.bashrc //设置android环境变量 
echo 'export JAVA_CMD="/usr/local/java/jdk1.8.0_25/bin/java"' >> ~/.bashrc //设置java环境变量
```
终端输入android，出现提示说明配置成功

打开android studio 根据提示配置SDK路径


打开SDK manager更改更新源，进行更新；

#### 4.新建项目

![project.png](images\project.png)



![p.png](images\p.png)
![QQ截图20150507015808.png](images\QQ截图20150507015808.png)
![QQ截图20150507015817.png](images\QQ截图20150507015817.png)


![QQ截图20150507020029.png](images\QQ截图20150507020029.png)

