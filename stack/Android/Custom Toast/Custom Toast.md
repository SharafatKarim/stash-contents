---
Owner: Sharafat Karim
Last edited time: 2023-11-08T10:32
---
It won’t hurt you to add a linear layout with just a text and an icon, right?

![[/Untitled 8.png|Untitled 8.png]]

Later on, let’s just tweak the main activity’s java file

```Java
package com.example.mybuttontest;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.Gravity;
import android.view.LayoutInflater;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        setTitle("Home");

        Button login_button = (Button) findViewById(R.id.button);
        login_button.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                LayoutInflater layoutInflater = getLayoutInflater();
                View view_of_custom_toast = layoutInflater.inflate(R.layout.my_custom_toast, findViewById(R.id.lin_lay));

                Toast toast = new Toast(MainActivity.this);
                toast.setDuration(Toast.LENGTH_LONG);
                toast.setGravity(Gravity.CENTER, 0, 0);
                toast.setView(view_of_custom_toast);
                toast.show();
            }
        });
    }
}
```