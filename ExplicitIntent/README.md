# Ex.No:4 To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:
Step 1: Open Android Studio and then click on File -> New -> New project.

Step 2: Then type the Application name as HelloWorld and click Next.

Step 3: Then select the Minimum SDK as shown below and click Next.

Step 4: Then select the Empty Activity and click Next. Finally click Finish.

Step 5: Design layout in activity_main.xml.

Step 6: Display message give in MainActivity file.

Step 7: Save and run the application.


## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Prakash Vasanth 
Registeration Number : 212221040127
*/
```
activity_main.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/maintxt"
        android:layout_width="317dp"
        android:layout_height="38dp"
        android:layout_marginTop="36dp"
        android:text="FACTORIAL FINDING"
        android:textAlignment="center"
        android:textSize="25sp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/text1"
        android:layout_width="156dp"
        android:layout_height="32dp"
        android:layout_marginStart="76dp"
        android:layout_marginTop="240dp"
        android:text="Enter a Number"
        android:textColor="@color/black"
        android:textSize="20sp"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <EditText
        android:id="@+id/n1"
        android:layout_width="50dp"
        android:layout_height="50dp"
        android:layout_alignRight="@+id/text1"
        android:layout_marginTop="224dp"
        android:hint="enter"
        android:layout_marginEnd="120dp"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <Button
        android:id="@+id/btn1"
        android:layout_width="120dp"
        android:width="200dp"
        android:minHeight="48dp"
        android:layout_height="45dp"
        android:layout_marginBottom="360dp"
        android:background="#2C34CF"
        android:text="Calculate"
        android:textColor="@color/white"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.498"
        app:layout_constraintStart_toStartOf="parent" />

    <TextView
        android:id="@+id/resum"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginLeft="150dp"
        tools:ignore="MissingConstraints" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity.java:
```
package com.example.factorial;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    public static String Send_Result;
    EditText num1;
    TextView txtrslt;
    Button btn;
    double n,i=1,fact=1;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        num1 = (EditText) findViewById(R.id.n1);
        txtrslt = (TextView) findViewById(R.id.resum);
        btn = (Button) findViewById(R.id.btn1);
        btn.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                n = Double.parseDouble(num1.getText().toString());
                while (i<=n)
                {
                    fact=fact*i;
                    i++;
                }
                String message = Double.toString(fact);
                Intent myIntent = new Intent(MainActivity.this, MainActivity2.class);
                myIntent.putExtra(Send_Result, message);
                startActivity(myIntent);
            }
        });
    }
}
```
activity_main2.xml:
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <TextView
        android:id="@+id/textView"
        android:layout_width="137dp"
        android:layout_height="47dp"
        android:text="RESULT : "
        android:textColor="@color/black"
        android:textSize="34sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.167"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.425" />

    <TextView
        android:id="@+id/result"
        android:layout_width="198dp"
        android:layout_height="59dp"
        android:text="00.00"
        android:textColor="#EA80FC"
        android:textSize="38sp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.924"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.433" />
</androidx.constraintlayout.widget.ConstraintLayout>
```
MainActivity2.java:
```
package com.example.factorial;

import androidx.appcompat.app.AppCompatActivity;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

import com.example.factorial.R;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        Intent intent = getIntent();
        String message = intent.getStringExtra(MainActivity.Send_Result);
        TextView textView = findViewById(R.id.result);
        textView.setText(message);
    }
}
```
## OUTPUT
Code with UI without inputs:
![Screenshot (157)](https://github.com/Vasanth1234567/Mobile-Application-Development/assets/86919099/3bbe1939-6076-4a6a-b8a7-b285166cacd7)

Code with UI with Inputs:
![Screenshot (158)](https://github.com/Vasanth1234567/Mobile-Application-Development/assets/86919099/20c40c7a-66e6-48f4-81dc-50c95d9d9b57)

Emulator with Output:
![Screenshot (159)](https://github.com/Vasanth1234567/Mobile-Application-Development/assets/86919099/27badc1b-e52d-4d22-bff6-22d8cf738ee8)




## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


