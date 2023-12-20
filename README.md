# HotFix热修复
Tinker：https://github.com/Tencent/tinker

![image](https://github.com/gaoleicoding/HotFix/assets/16413477/89c0de8c-aabf-467a-9a97-058b80d3fc41)

1、Tinker搭配的这些，目前没发现啥问题：

minsdk <=21、
targetsdk 33、
android gradle plugin 7.4.2、
Gradle 7.5.1、
R8 4.0.71

2、看看logcat  tag是 Tinker. 开头，可查看遇到的问题

    //patch listener error code
    public static final int ERROR_PATCH_OK                = 0;
    public static final int ERROR_PATCH_DISABLE           = -1;
    public static final int ERROR_PATCH_NOTEXIST          = -2;
    public static final int ERROR_PATCH_RUNNING           = -3;
    public static final int ERROR_PATCH_INSERVICE         = -4;
    public static final int ERROR_PATCH_JIT               = -5;
    public static final int ERROR_PATCH_ALREADY_APPLY     = -6;

3、tinkerId 和new tinkerId 需要不一样

configField("TINKER_ID", "\"${getTinkerIdValue()}\"") // tinkerId 可以设为项目的版本号（android.defaultConfig.versionName），作为基准

configField("NEW_TINKER_ID", "\"${releaseTime()}\"") // new tinkerId 可以设为项目的打包时间，不断更新

![image](https://github.com/gaoleicoding/HotFix/assets/16413477/f9e90ce6-953c-4f61-8640-6da63739112d)

查看patch包结果：

<img width="209" alt="93225de04f802999210218567a3b63a" src="https://github.com/gaoleicoding/HotFix/assets/16413477/c716e90c-c0ec-4bf8-aa5f-a109d23b20bb">
4、如何打patch包：

![2020031816064317](https://github.com/gaoleicoding/HotFix/assets/16413477/7fb2ea63-371f-4a96-a32d-b46b616bace5)


5、测试时可把补丁推送到应用私有目录

adb push “patch文件的路径” /storage/emulated/0/Android/data/包名/files/
