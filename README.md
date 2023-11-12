# HotFix热修复
Tikner：https://github.com/Tencent/tinker

 v1.9.14.26 Latest
![image](https://github.com/gaoleicoding/HotFix/assets/16413477/6d06a85e-ce91-4d43-b3dd-7bd4d64a8dc3)

1、Tinker搭配的这些，目前没发现啥问题：
minsdk <=21
targetsdk 33
android gradle plugin 7.4.2
Gradle 7.5.1
R8 4.0.71

2、看看logcat  tag是 Tinker. 开头，可查看遇到的问题

3、tinkerId 和new tinkerId 需要不一样
tinkerId = getTinkerIdValue() // tinkerId 可以设为项目的版本号，作为基准
configField("NEW_TINKER_ID", "\"${releaseTime()}\"")// new tinkerId 可以设为项目的打包时间，不断更新


4、测试时可把补丁推送到SD卡，adb push “patch文件的路径” /storage/emulated/0/Android/data/包名/files/
