일시 : 2013.6.5 (수) 1100-1200

Source에 있는 안드로이드 App 소스 리뷰


[링크]
http://code.google.com/p/zatouri/source/browse/trunk/WebAppLauncher/src/com/zatouri/webapplauncher/MainActivity.java
```
package com.zatouri.webapplauncher;

import android.os.Bundle;
import android.preference.PreferenceManager;
import android.app.Activity;
import android.content.Intent;
import android.content.SharedPreferences;
import android.util.Log;
import android.view.Menu;
import android.view.MenuItem;
import android.webkit.WebView;
import android.webkit.WebViewClient;

public class MainActivity extends Activity {

﻿  private static final int RESULT_SETTINGS = 1;
﻿  private WebView webview;
﻿  
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        webview = (WebView)this.findViewById(R.id.webView1);
        webview.setWebViewClient(new MyWebViewClient());
        webview.getSettings().setJavaScriptEnabled(true);
        
        loadURL();
    }


    
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.settings, menu);
        return true;
    }

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()) {
 
        case R.id.menu_settings:
            Intent i = new Intent(this, ZatouriPrefActivity.class);
            startActivityForResult(i, RESULT_SETTINGS);
            break;
 
        }
 
        return true;
    }
    
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
 
        switch (requestCode) {
        case RESULT_SETTINGS:
            loadURL();
            break;
 
        }
 
    }

﻿  private void loadURL() {
﻿  ﻿  SharedPreferences sharedPrefs = PreferenceManager.getDefaultSharedPreferences(this);
 
        String launchURL = sharedPrefs.getString("launchURL", "NULL");
        
        webview.loadUrl(launchURL);
﻿  }    
    
    private class MyWebViewClient extends WebViewClient {
        @Override
        public boolean shouldOverrideUrlLoading(WebView view, String url) {
            view.loadUrl(url);
            return true;
        }
    }
}
```



전 ASP.NET Mobile Framework를 공부해서 발표해보렵니다. - 민규

http://amf.codeplex.com/


---


CSS reset vs nomalization

http://the-pastry-box-project.net/oli-studholme/2013-june-3/

요런건 또 어떨까요? 모바일이 아니란 단점이;;