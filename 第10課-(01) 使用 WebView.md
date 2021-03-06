# 第10課 使用 WebView



## (1) 使用 WebView



##### 執行結果:
![GitHub Logo](/images/results10-1.jpg)



##### 模擬器
```
Nexus 5, API 23
```



##### 建立專案設定
```
(1) Company Domain: abc.com 
(2) Minimum SDK: API 21: Android 5.0(Lollipop)
(3) 第1個Activity選用 Empty Activity; 第2個Activity選用 Basic Activity;
```



##### 檔案放置方式:
```
 app 
   |___<manifests>
   |     |___AndroidManifest.xml
   |            
   |___<java>
   |     |___<com.abc.myapplication>
   |            |___Main2Activity.java 
   |            |___MainActivity.java    
   | 
   |___<res>
         |		 
         |___<layout>
         |      |___activity_main.xml
         |      |___activity_main2.xml
         |      |___content_main2.xml   
         | 	 
         |___<values>
                |___colors.xml  
                |
                |___<dimens.xml(2)> 
                |        |___dimens.xml  
                |
                |___strings.xml
```



##### 檔案名稱: AndroidManifest.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    package="com.abc.myapplication">

    <!-- 允許使用Internet -->
    <uses-permission android:name="android.permission.INTERNET"/>
    <!-- ................ -->

    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
        <activity android:name=".MainActivity">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
        <activity
            android:name=".Main2Activity"
            android:label="@string/title_activity_main2"
            android:theme="@style/AppTheme.NoActionBar"></activity>
    </application>

</manifest>
```



##### 檔案名稱: colors.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="colorPrimary">#4f0010</color>
    <color name="colorPrimaryDark">#000</color>
    <color name="colorAccent">#4f0010</color>

    <!-- 4張圖片的顏色 -->
    <color name="imgColor_1">#0f5935</color>
    <color name="imgColor_2">#4a9470</color>
    <color name="imgColor_3">#29506d</color>
    <color name="imgColor_4">#123652</color>
</resources>
```



##### 檔案名稱: dimens.xml
```xml
<resources>
    <dimen name="activity_horizontal_margin">0dp</dimen>
    <dimen name="activity_vertical_margin">0dp</dimen>
    <dimen name="fab_margin">16dp</dimen>

    <!-- 圖片間的邊界 -->
    <dimen name="imageMargin">1dp</dimen>
    <dimen name="imageMarginTop">20dp</dimen>

    <!-- 文字大小 -->
    <dimen name="textSize">30dp</dimen>
</resources>
```



##### 檔案名稱: strings.xml
```xml
<resources>
    <string name="app_name">第1個Activity</string>
    <string name="title_activity_main2">第2個Activity</string>
</resources>
```



##### 檔案名稱: activity_main.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    tools:context="com.abc.myapplication.MainActivity">

    <!-- 第1個橫列 -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1">

        <ImageView
            android:id="@+id/img1"
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="@color/imgColor_1"
            android:layout_marginRight="@dimen/imageMargin"
            android:layout_marginBottom="@dimen/imageMargin"/>

        <ImageView
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="2"
            android:background="@color/imgColor_2"
            android:layout_marginBottom="@dimen/imageMargin"/>
    </LinearLayout>


    <!-- 第2個橫列 -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="0dp"
        android:layout_weight="1">

        <ImageView
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="2"
            android:background="@color/imgColor_3"
            android:layout_marginRight="@dimen/imageMargin"/>

        <ImageView
            android:layout_width="0dp"
            android:layout_height="match_parent"
            android:layout_weight="1"
            android:background="@color/imgColor_4"/>
    </LinearLayout>
</LinearLayout>
```



##### 檔案名稱: activity_main2.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<android.support.design.widget.CoordinatorLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:fitsSystemWindows="true"
    tools:context="com.abc.myapplication.Main2Activity">

    <android.support.design.widget.AppBarLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:theme="@style/AppTheme.AppBarOverlay">

        <android.support.v7.widget.Toolbar
            android:id="@+id/toolbar"
            android:layout_width="match_parent"
            android:layout_height="?attr/actionBarSize"
            android:background="?attr/colorPrimary"
            app:popupTheme="@style/AppTheme.PopupOverlay" />

    </android.support.design.widget.AppBarLayout>

    <include layout="@layout/content_main2" />

    <!-- 用FAB返回原呼叫Activity -->
    <android.support.design.widget.FloatingActionButton
        android:id="@+id/fab"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_gravity="bottom|end"
        android:layout_margin="@dimen/fab_margin"
        android:src="@android:drawable/ic_menu_revert" />

</android.support.design.widget.CoordinatorLayout>
```



##### 檔案名稱: content_main2.xml
```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:paddingBottom="@dimen/activity_vertical_margin"
    android:paddingLeft="@dimen/activity_horizontal_margin"
    android:paddingRight="@dimen/activity_horizontal_margin"
    android:paddingTop="@dimen/activity_vertical_margin"
    app:layout_behavior="@string/appbar_scrolling_view_behavior"
    tools:context="com.abc.myapplication.Main2Activity"
    tools:showIn="@layout/activity_main2">

    <!-- 顯示網頁內容 -->
    <WebView
        android:id="@+id/webView"
        android:layout_width="match_parent"
        android:layout_height="match_parent"/>

</LinearLayout>
```



##### 檔案名稱: MainActivity.java
```java
package com.abc.myapplication;

import android.content.Context;
import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {
    //-----------------------------------
    // 宣告一個存放執行狀態的Context物件
    //-----------------------------------
    Context context;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    
    //==========================================================================
    // 首次載入App時會執行onStart(), 下次App由背景回到前景時也會執行onStart()
    //==========================================================================
    @Override
    protected void onStart() {
        super.onStart();

        // 存放目前的執行狀態
        context=this;

        //-------------------------------------------
        // 如果第1個畫面被點擊, 切換到下一個Activity
        //-------------------------------------------
        ImageView img1 = (ImageView)findViewById(R.id.img1);
        img1.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                // 產生一個Bundle, 用來存放傳送的參數
                Bundle bundle=new Bundle();
                bundle.putString("url", "http://beta.html5test.com/");

                // 產生一個Intent, 用來轉換Activity
                Intent intent=new Intent();

                // 將Bundle物件加入Intent物件中
                intent.putExtras(bundle);

                // 設定轉換的Activity
                intent.setClass(context, Main2Activity.class);

                // 轉換至下一個Activity
                context.startActivity(intent);
            }
        });	
    }	
}
```



##### 檔案名稱: Main2Activity.java
```java
package com.abc.myapplication;

import android.os.Bundle;
import android.support.design.widget.FloatingActionButton;
import android.support.v7.app.AppCompatActivity;
import android.support.v7.widget.Toolbar;
import android.view.View;
import android.webkit.WebSettings;
import android.webkit.WebView;
import android.widget.ImageView;
import android.widget.TextView;

public class Main2Activity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        Toolbar toolbar = (Toolbar) findViewById(R.id.toolbar);
        setSupportActionBar(toolbar);

        FloatingActionButton fab = (FloatingActionButton) findViewById(R.id.fab);
        fab.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                //--------------------
                // 返回原呼叫Activity
                //--------------------
                finish();
            }
        });
    }
    
    
    //=============================================================================
    // 首次載入App時會執行onResume(), 下次Activity由背景回到前景時也會執行onResume()
    //=============================================================================
    @Override
    protected void onResume() {
        super.onResume();
		
        //-------------------------
        // 取得傳來Bundle中的參數
        //-------------------------
        Bundle bundle=getIntent().getExtras();
		
        //取得網頁地址
        String url=bundle.getString("url");  

        //-------------------------
        // 顯示網頁內容
        //-------------------------
        // 取得顯示網頁物件
        WebView webView = (WebView) findViewById(R.id.webView);
		
        // 允許使用java script
        WebSettings webSettings = webView.getSettings();
        webSettings.setJavaScriptEnabled(true);

        // 載入網頁
        webView.loadUrl(url);
    }    
}
```
