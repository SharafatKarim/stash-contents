---
Owner: Sharafat Karim
Last edited time: 2023-11-01T23:23
---
Perhaps let’s show the file structure,

![[/Untitled 9.png|Untitled 9.png]]

---

Then comes the Device,  
for now, Android 9 (Pie) seems pretty much solid!  

---

MainActivity.java

```Java
package com.example.mybuttontest;

import androidx.appcompat.app.AppCompatActivity;

import android.annotation.SuppressLint;
import android.content.Intent;
import android.os.Bundle;
import android.util.Log;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }

    @SuppressLint("SetTextI18n")
    public void disable(View view) {
        Button b =  findViewById(R.id.button);
        b.setText("ok ok");

        TextView texts = findViewById(R.id.textView);
        texts.setText("hello");
        Log.d("textLG", texts.toString());

				// New activity
        Intent intent = new Intent(this, SettingsActivity.class);
        startActivity(intent);
    }
}
```

---

in the menifest, a label and the parentAc..Name?

![[/Untitled 1 2.png|Untitled 1 2.png]]

Also setTitle,

![[/Untitled 2 3.png|Untitled 2 3.png]]

---

Time for code? Manifest one

```XML
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">

    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.MyButtonTest"
        tools:targetApi="31">
        <activity
            android:name=".SettingsActivity"
            android:exported="false"
            android:label="@string/title_activity_settings"
            android:parentActivityName=".MainActivity" />
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>

</manifest>
```

---

And to pass message

```Java
Intent intent = new Intent(this, SettingsActivity.class);
        intent.putExtra("key", "This is a value");
        intent.putExtra("key2", "This is an another value");
        startActivity(intent);
```

And on the receiving end,

```Java
Intent intent = getIntent();
        String message = intent.getStringExtra("key");
        ((TextView)findViewById(R.id.textView3)).setText(message);
```

You can attach on the `onCreate`