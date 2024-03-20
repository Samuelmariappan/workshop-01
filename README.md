# workshop-01

# Develop an android application pass the data between the activities using Intent.


## Instructions:

1.Create in design part user name, user age, user emailid and user contactnumber.

2.Read the input value from the user.

3.Display the output on the other activities 

1. Project Setup:

Create a new Android Studio project and name it appropriately (e.g., workshop - 01).
Ensure you have the Android SDK and tools installed.
2. Activity Layouts:

Create two activity layouts: activity_main.xml and activity_display.xml.

## PROGRAM:
```
/*

Developed by: Samuel M
Registeration Number :212222040142
*/
```

### MainActivity.java

```

package com.example.workshop_01;

import androidx.appcompat.app.AppCompatActivity;
import androidx.appcompat.widget.ButtonBarLayout;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {
    private EditText editTextName, editTextAge, editTextEmail, editTextContact;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editTextName = findViewById(R.id.editTextName);
        editTextAge = findViewById(R.id.editTextAge);
        editTextEmail = findViewById(R.id.editTextEmail);
        editTextContact = findViewById(R.id.editTextContact);

        Button buttonSubmit = findViewById(R.id.buttonSubmit);
        buttonSubmit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String name = editTextName.getText().toString();
                String age = editTextAge.getText().toString();
                String email = editTextEmail.getText().toString();
                String contact = editTextContact.getText().toString();

                Intent intent = new Intent(MainActivity.this, MainActivity2.class);
                intent.putExtra("name", name);
                intent.putExtra("age", age);
                intent.putExtra("email", email);
                intent.putExtra("contact", contact);
                startActivity(intent);

            }
        });
    }
}
```
### MainActivity2.java

```
package com.example.workshop_01;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;

public class MainActivity2 extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);

        TextView textViewName = findViewById(R.id.textViewName);
        TextView textViewAge = findViewById(R.id.textViewAge);
        TextView textViewEmail = findViewById(R.id.textViewEmail);
        TextView textViewContact = findViewById(R.id.textViewContact);

        Intent intent = getIntent();

        if (intent != null) {
            String name = intent.getStringExtra("name");
            String age = intent.getStringExtra("age");
            String email = intent.getStringExtra("email");
            String contact = intent.getStringExtra("contact");

            textViewName.setText("Name: " + name);
            textViewAge.setText("Age: " + age);
            textViewEmail.setText("Email: " + email);
            textViewContact.setText("Contact: " + contact);
        }
    }
}

```
### Activity_main.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

    <RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
        android:layout_width="match_parent"
        android:layout_height="match_parent">

        <EditText
            android:id="@+id/editTextName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:hint="Enter Name" />

        <EditText
            android:id="@+id/editTextAge"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@id/editTextName"
            android:hint="Enter Age" />

        <EditText
            android:id="@+id/editTextEmail"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@id/editTextAge"
            android:hint="Enter Email" />

        <EditText
            android:id="@+id/editTextContact"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_below="@id/editTextEmail"
            android:hint="Enter Contact Number" />

        <Button
            android:id="@+id/buttonSubmit"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@id/editTextContact"
            android:layout_centerHorizontal="true"
            android:text="Submit" />
    </RelativeLayout>

</androidx.constraintlayout.widget.ConstraintLayout>

```

### Activity_main2.xml

```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity2">

    <RelativeLayout
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_margin="16dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent">

        <TextView
            android:id="@+id/textViewName"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="16dp"
            android:text="Name" />

        <TextView
            android:id="@+id/textViewAge"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@id/textViewName"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="16dp"
            android:text="Age" />

        <TextView
            android:id="@+id/textViewEmail"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@id/textViewAge"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="16dp"
            android:text="Email" />

        <TextView
            android:id="@+id/textViewContact"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_below="@id/textViewEmail"
            android:layout_centerHorizontal="true"
            android:layout_marginTop="16dp"
            android:text="Contact" />

    </RelativeLayout>

</androidx.constraintlayout.widget.ConstraintLayout>

```
## Output:

![Screenshot 2024-03-20 143404](https://github.com/Samuelmariappan/workshop-01/assets/119393030/2e849e91-d0c3-4924-a6f3-c12a234826d7)
![Screenshot 2024-03-20 143330](https://github.com/Samuelmariappan/workshop-01/assets/119393030/bfde9875-e23a-4784-a94d-d1ee1fb8e857)

## Result:

The Worshop has Successfullly implemented. 
