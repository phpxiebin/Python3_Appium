# WIN10环境APP爬虫服务搭建文档

### 背景介绍
为了抓取APP接口加密header头才能获取到正确的响应内容，亦可解决APP内容抓取。
环境部署好后通过 **windows自带的任务计划程序+python3+mitmproxy+mqtt** 自动运行处理。
本文档主要记录了win10环境下部署 **Anaconda(python3)+appium+mumu模拟器** 部署配置的简要过程。

### 安装软件信息
1. Anaconda安装信息
>安装目录：C:\Users\xiebing\Anaconda3
环境变量已添加：C:\Users\xiebing\Anaconda3\Scripts

执行命令：
```
(base) C:\Users\xiebing>conda -V
conda 4.7.10
(base) C:\Users\xiebing>conda create -n reptile python=3
Preparing transaction: done
Verifying transaction: done
Executing transaction: done
#
# To activate this environment, use
#
#     $ conda activate reptile
#
# To deactivate an active environment, use
#
#     $ conda deactivate

(base) C:\Users\xiebing>conda env list
# conda environments:
#
base                  *  C:\Users\xiebing\Anaconda3
reptile                  C:\Users\xiebing\Anaconda3\envs\reptile


(base) C:\Users\xiebing>activate reptile

(reptile) C:\Users\xiebing>pip list
Package              Version
-------------------- ---------
Appium-Python-Client 0.46
certifi              2019.6.16
pip                  19.1.1
selenium             3.141.0
setuptools           41.0.1
urllib3              1.25.3
wheel                0.33.4
wincertstore         0.2
```

2. Appium安装信息
> 安装目录：C:\Program Files (x86)\Appium

3. JAVA JDK安装
> 安装目录：C:\Program Files\Java
环境变量已添加：C:\Program Files\Java\jdk-12.0.2\bin

```
C:\Users\xiebing>java -version
java version "12.0.2" 2019-07-16
Java(TM) SE Runtime Environment (build 12.0.2+10)
Java HotSpot(TM) 64-Bit Server VM (build 12.0.2+10, mixed mode, sharing)
```

4. Android SDK安装信息
> 安装目录：C:\android-sdk-windows
环境变量已添加：
ANDROID_HOME:
C:\android-sdk-windows
PATH:
%ANDROID_HOME%\platform-tools
%ANDROID_HOME%\tools
%ANDROID_HOME%\build-tools\29.0.1

ADB创建设备连接

```
C:\Users\xiebing>adb version
Android Debug Bridge version 1.0.41
Version 29.0.1-5644136
Installed as C:\Program Files\android-sdk-windows\platform-tools\adb.exe
```

查看安装包信息
```
aapt dump badging APK包路径
```

5. MUMU安卓模拟器
安装目录：C:\Program Files (x86)\MuMu
连接mumu虚拟机：
```
C:\Users\xiebing>adb connect 127.0.0.1:7555
connected to 127.0.0.1:7555
C:\Users\xiebing>adb devices
List of devices attached
127.0.0.1:7555  device
```

6. GIT安装
> 安装目录：C:\Program Files\Git

```
ssh方式
创建ssh key：ssh-keygen.exe -t rsa -C "GitLab" -b 4096
$ cat ~/.ssh/id_rsa.pub

http方式
git clone https://用户名:密码@github.com/xxxx
注: 用户名和密码urlencode 

```
