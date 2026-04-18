Q1. Simple Calculator App.

➡️ activity_main.xml (Layout File) ⬇️

   <?xml version="1.0" encoding="utf-8"?>

<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:padding="62dp">

    <EditText
        android:id="@+id/etFirstNum"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter First Number"
        android:inputType="numberDecimal"/>

    <EditText
        android:id="@+id/etSecondNum"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter Second Number"
        android:layout_marginTop="10dp"
        android:inputType="numberDecimal"/>

    <TextView
        android:id="@+id/tvResult"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Result"
        android:textSize="24sp"
        android:gravity="end"
        android:layout_marginTop="20dp"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="20dp"
        android:orientation="horizontal">

        <Button
            android:id="@+id/btnPlus"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="+"/>

        <Button
            android:id="@+id/btnMinus"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="-"/>

        <Button
            android:id="@+id/btnMultiply"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="*"/>

        <Button
            android:id="@+id/btnDivide"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="/"/>
    </LinearLayout>

</LinearLayout>


➡️ MainActivity.java ⬇️
  
  package com.example.calculator;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText et1, et2;
    TextView tvResult;
    Button btnPlus, btnMinus, btnMultiply, btnDivide;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et1 = findViewById(R.id.etFirstNum);
        et2 = findViewById(R.id.etSecondNum);
        tvResult = findViewById(R.id.tvResult);

        btnPlus = findViewById(R.id.btnPlus);
        btnMinus = findViewById(R.id.btnMinus);
        btnMultiply = findViewById(R.id.btnMultiply);
        btnDivide = findViewById(R.id.btnDivide);

        View.OnClickListener action = v -> {

            double n1 = Double.parseDouble(et1.getText().toString());
            double n2 = Double.parseDouble(et2.getText().toString());

            Button btn = (Button) v;

            switch (btn.getText().toString()) {

                case "+":
                    tvResult.setText(String.valueOf(n1 + n2));
                    break;

                case "-":
                    tvResult.setText(String.valueOf(n1 - n2));
                    break;

                case "*":
                    tvResult.setText(String.valueOf(n1 * n2));
                    break;

                case "/":
                    if (n2 == 0)
                        tvResult.setText("Cannot divide by zero");
                    else
                        tvResult.setText(String.valueOf(n1 / n2));
                    break;
            }

            et1.setText("");
            et2.setText("");
        };

        btnPlus.setOnClickListener(action);
        btnMinus.setOnClickListener(action);
        btnMultiply.setOnClickListener(action);
        btnDivide.setOnClickListener(action);
    }
}
