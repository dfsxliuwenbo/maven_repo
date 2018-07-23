# maven_repo
dfsx push code repository
版本列表：

0.0.1

0.0.2

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
