# HotFix
腾讯：tinker_demo

接入指南：https://github.com/Tencent/tinker/wiki/Tinker-%E6%8E%A5%E5%85%A5%E6%8C%87%E5%8D%97

tinker_demo使用方法：

1.调用assembleDebug编译，我们会将编译过的包保存在build/bakApk中。然后我们将它安装到手机，点击SHOW INFO按钮，可以看到补丁并没有加载.

2.修改代码，例如将MainActivity中 Toast.makeText(this, "I have fixed by tinker", Toast.LENGTH_SHORT).show(); 打开。然后我们需要修改build.gradle中的参数，将步骤一编译保存的安装包路径拷贝到ext中的oldApk参数中，四个oldApk路径都要替换。如下图：

![image](https://github.com/gaoleiandroid1201/HotFix/raw/master/material/screenshots/tinker_img1.png)

3.调用./gradlew tinkerPatchDebug, 补丁包与相关日志会保存在/build/outputs/tinkerPatch/。然后我们将patch_signed_7zip.apk推送到手机的sdcard中。

4.点击LOAD PATCH按钮, 如果看到patch success, please restart process的toast，即可点击KILL SELF按钮，重启app看效果

5.我们可以看到的确出现了Toast “I have fixed by tinker”，同时点击SHOW INFO按钮，显示补丁包的确已经加载成功了。


----------------------------------------------------------------------------------------------------------------------
阿里：sophix_demo


