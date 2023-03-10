# 1.解码v0.2方案介绍

使用opencv barcode+zxing方法，纯C++方案，不使用ML方法。  
检测步骤：  
1）使用opencv barcode检查是否包含条码；  
2）检测到条码，一维码解码，结束；  
3）未检测到条码，使用zxing进行解码，结束。  

# 2.编译环境

编译系统：Ubuntu 18.04.3 LTS  

## 1）x86_64平台

编译工具：gcc (Ubuntu 7.5.0-3ubuntu1~18.04) 7.5.0


## 2）Open Harmony OS arm平台
编译工具：clang++(sdk版本为3.2.5.6，大版本为3.2即可)

通过 [HUAWEI DevEco Studio和SDK下载和升级](https://developer.harmonyos.com/cn/develop/deveco-studio/ "下载ohcommandlinetools-linux-tool工具")，下载 ohcommandlinetools-linux-tool工具。

参考[ohsdkmgr使用指导-命令行工具-DevEco Studio使用指南(OpenHarmony)-工具-HarmonyOS应用开发](https://developer.harmonyos.com/cn/docs/documentation/doc-guides-V3/ohos-sdk-command-line-tool-0000001263280431-V3)，下载3.2版本的SDK。



<table><tr><td bgcolor=blue>下载命令参考：  </td></tr></table> 

显示native版本：ohsdkmgr list native  
 Component | API Version | Version | Stage   | Status        | Available Update
 --------- | ----------- | ------- | ------- | ------------- | ----------------
 native    | 9           | 3.2.7.5 | Beta3   | Not Installed |                 
 native    | 8           | 3.1.7.7 | Release | Not Installed | 
  
下载3.2版本的native: ohsdkmgr install --sdk-directory="/home/xxx/ohos_test/ohos_sdk" native:9  

<table><tr><td bgcolor=red>注意：需要在<src_root>/compile_options.sh中配置OHOS_NDK的路径</td></tr></table>  

# 3.编译

## 1）x86_64平台

进入<src_root>/third_party/opencv目录，执行脚本B_x86_64_opencv.sh，编译opencv；  
进入<src_root>/third_party/zbar目录，执行脚本B_x86_64_zbar.sh，编译zbar；  
最后在<src_root>目录，执行脚本B_x86_64.sh，编译出动态库和执行程序。  

## 2）Open Harmony OS arm平台

进入<src_root>/third_party/opencv目录，执行脚本B_ohos_opencv.sh，编译opencv；  
进入<src_root>/third_party/zbar目录，执行脚本B_ohos_zbar.sh，编译zbar；  
进入<src_root>/third_party/authverify_oho目录，执行脚本B_all.sh，编译鸿蒙系统下的授权静态库，用于调用的授权；  
最后在<src_root>目录，执行脚本B_ohos.sh，编译出动态库和执行程序。









