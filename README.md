# HotFix热修复

Tinker：https://github.com/Tencent/tinker

![image](https://github.com/gaoleicoding/HotFix/assets/16413477/89c0de8c-aabf-467a-9a97-058b80d3fc41)

## 1、Tinker搭配的这些，目前没发现啥问题：

minsdk <=21、
targetsdk 33、
android gradle plugin 7.4.2、
Gradle 7.5.1、
R8 4.0.71

## 2、tinkerId 和new tinkerId 需要不一样

configField("TINKER_ID", "\"tinker_id_${getTinkerIdValue()}\"") // tinkerId 可以设为项目的versionName作为基准，有一个小细节是必须以**tinker_id_**开头，不然会报错

configField("NEW_TINKER_ID", "\"${releaseTime()}\"") // new tinkerId 可以设为项目的打包时间，不断更新

![image](https://github.com/gaoleicoding/HotFix/assets/16413477/f9e90ce6-953c-4f61-8640-6da63739112d)

## 3、如何打patch包：

![2020031816064317](https://github.com/gaoleicoding/HotFix/assets/16413477/7fb2ea63-371f-4a96-a32d-b46b616bace5)

## 4、把patch包拖拽到AS查看信息：

<img width="209" alt="93225de04f802999210218567a3b63a" src="https://github.com/gaoleicoding/HotFix/assets/16413477/c716e90c-c0ec-4bf8-aa5f-a109d23b20bb">

## 5、测试时把补丁推送到应用私有目录，也可以放到assets中copy到私有目录

adb push “patch文件的路径” /storage/emulated/0/Android/data/包名/files/

## 6、查看打补丁包的过程，可以利用logcat  筛选tag是 Tinker. 的信息。如果出现如下图说明打补丁成功，打补丁过程较长，自测多次需要90s左右

![image](https://github.com/gaoleicoding/HotFix/assets/16413477/0b5d53d7-88bd-48a1-ac95-4b56f45b4dc9)

## 7、打包监听返回的状态

    //patch listener error code
    
    public static final int ERROR_PATCH_OK                = 0;
    
    public static final int ERROR_PATCH_DISABLE           = -1;
    
    public static final int ERROR_PATCH_NOTEXIST          = -2;
    
    public static final int ERROR_PATCH_RUNNING           = -3;
    
    public static final int ERROR_PATCH_INSERVICE         = -4;
    
    public static final int ERROR_PATCH_JIT               = -5;
    
    public static final int ERROR_PATCH_ALREADY_APPLY     = -6;

    


