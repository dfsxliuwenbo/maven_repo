# maven_repo

dfsx 的公用库集成:

仓库地址：

        maven { url 'https://github.com/dfsxliuwenbo/maven_repo/raw/master/' }

一、

dfsx push code repository
版本列表：

0.0.1

0.0.2

0.0.3

1.0.0 （修复没有arm64-v8包缺失）重要

调用者重写对应版本的String配置

0.0.1版本使用下面这些字段配置参数： 

    <string name="alibaba_appkey">24840376</string>
    <string name="alibaba_appsecret">8eff95afc3e9c9b778c3bc3306047721</string>

    <string name="xiaomi_appid">2882303761517838776</string>
    <string name="xiaomi_appkey">5331783867776</string>
    <string name="xiaomi_appsecret">1vn6FAaLaUTh0mRXpSJW8w==</string>
    
集成方式：
 maven { url 'https://github.com/dfsxliuwenbo/maven_repo/raw/master/' }
 
 compile 'com.dfsx.push:dfsxAliyunpsuh:{版本号}@aar'
 
 在主工程里面的 APP包名下面新建.aliapi.AliPopupPushActivity。继承自BasePopupPushActivity。
 并在Manifest注册。
 
 
      public class AliPopupPushActivity extends BasePopupPushActivity {
      }

     <activity
            android:name="{APP 的包名}.aliapi.AliPopupPushActivity"
            android:exported="true"
            android:label="@string/app_name"
            android:launchMode="singleTop"/>

使用:

   在Application中调注册以下代码：
   
   AliyunPushManager.getInstance().initAndRegister(applicationContext, new CommonCallback());
   AliyunPushManager.getInstance().regsiterThirdPush(applicationContext);
   //设置推送消息监听
   AliyunPushManager.getInstance().setListener(XXXXXXX);
   
   
二、

检查更新功能：

版本 0.0.1
版本 0.0.2

        compile 'com.dfsx.update:dfsxUpdate:0.0.2@aar'

支持自定义检查方法:

        checkForDialog(FragmentActivity fragmentActivity, String url, IApkUpdateChecker checker)
        
三、

 统计功能
 
 版本 0.0.1
 
 集成
 
        compile 'com.dfsx.statistics:dfsxStatistics:0.0.1@aar'
 
 配置参数
 
        <string name="statistics_app_authorities">com.dfsx.dazhoucms.app.TENCENT.MID.V3</string><!--你的包名.TENCENT.MID.V3 -->
        <string name="statistics_app_key">ACT58LTH5E7U</string>
        <string name="statistics_app_channel">dfsx</string>
 
 使用：
 
        StatisticUtils.initAndStart(this);
        StatisticUtils.onUserIPStatistic(this);

四、

 语音合成功能
 
   版本：
   
        1.0.0 (基于百度的语音技术集成)
		
		1.0.2 添加默认新闻阅读的播放状态回调
   集成：
   
        compile 'com.dfsx.readtext:dfsxTTSRead:1.0.0@aar'
		
   参数配置：
   
     1.使用res文件静态注册：

    <string name="baidu_tts_appId">15677704</string>
    <string name="baidu_tts_appKey">yWjnYw2OtdXVy2Hp2Mgp7t4s</string>
    <string name="baidu_tts_secretKey">sA4FvBqXzi4c6gBwLNHzGV0EFFL7iRL7</string>
    <!--0纯在线 1离在线融合-->
    <string name="baidu_tts_mode">1</string>
    <!--设置在线发声音人： 0 普通女声（默认） 1 普通男声 2 特别男声 3 情感男声<度逍遥> 4 情感儿童声<度丫丫>-->
    <string name="baidu_tts_params_speaker">0</string>
    <!--设置合成的音量，0-9 ，默认 5-->
    <string name="baidu_tts_params_volume">9</string>
    <!--设置合成的语速，0-9 ，默认 5-->
    <string name="baidu_tts_params_speed">5</string>
    <!--设置合成的语调，0-9 ，默认 5-->
    <string name="baidu_tts_params_pitch">5</string>
    <!--声学模型文件路径 (离线引擎使用) F: VOICE_FEMALE; M: VOICE_MALE; Y: VOICE_DUYY; X: VOICE_DUXY-->
    <string name="baidu_tts_offline_params_model_file">M</string>

    2.也可以使用代码创建 InitConfig 对象，public void init(InitConfig initConfig, Action1<Boolean> action)；

    3.使用，使用TTSReadManager 对象使用， 或扩展TTSReadManager 来使用。（可以参照扩展的新闻阅读功能NewsReadHelper的实现）