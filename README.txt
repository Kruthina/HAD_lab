1. Activity lifecycle
XML
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="HAD LAB"
        android:id="@+id/had"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="enter"
        android:id="@+id/button"/>


    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter your name"
        android:id="@+id/name"/>


</LinearLayout>

Java
package com.example.atry;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

EditText a;
TextView b;
Button c;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Toast.makeText(this, "ACTIVITY CREATED", Toast.LENGTH_SHORT).show();

        a = findViewById(R.id.name);
        b = findViewById(R.id.name);
        c = findViewById(R.id.button);

c.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View view) {

    }
});

    }

    @Override
    protected void onStart() {
        super.onStart();
        Toast.makeText(this, "ACTIVITY STARTED", Toast.LENGTH_SHORT).show();

    }

    @Override
    protected void onStop() {
        super.onStop();
        Toast.makeText(this, "ACTIVITY stopped", Toast.LENGTH_SHORT).show();
    }
}

2. Calculator

java
package com.example.program2;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity implements View.OnClickListener {

    Button one, two, three, four, five, six, seven, eight, nine, zero;
    Button clear, plus, minus, multiply, divide, equal;
    EditText res;
    String operatorPressed = " ";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        res = findViewById(R.id.res);
        one = findViewById(R.id.one);
        two = findViewById(R.id.two);
        three = findViewById(R.id.three);
        four = findViewById(R.id.four);
        five = findViewById(R.id.five);
        six = findViewById(R.id.six);
        seven = findViewById(R.id.seven);
        eight = findViewById(R.id.eight);
        nine = findViewById(R.id.nine);
        zero = findViewById(R.id.zero);
        clear = findViewById(R.id.clear);
        plus = findViewById(R.id.plus);
        minus = findViewById(R.id.minus);
        divide = findViewById(R.id.divide);
        multiply = findViewById(R.id.multiply);
        equal = findViewById(R.id.equal);

        one.setOnClickListener(this);
        two.setOnClickListener(this);
        three.setOnClickListener(this);
        four.setOnClickListener(this);
        five.setOnClickListener(this);
        six.setOnClickListener(this);
        seven.setOnClickListener(this);
        eight.setOnClickListener(this);
        nine.setOnClickListener(this);
        zero.setOnClickListener(this);
        clear.setOnClickListener(this);
        plus.setOnClickListener(this);
        minus.setOnClickListener(this);
        divide.setOnClickListener(this);
        multiply.setOnClickListener(this);
        equal.setOnClickListener(this);

    }

    @Override
    public void onClick(View view) {

        double finalresult = 0.0;

        switch(view.getId())
        {
            case R.id.one: res.append("1");
                            break;

            case R.id.two: res.append("2");
                            break;

            case R.id.three: res.append("3");
                            break;

            case R.id.four: res.append("4");
                            break;

            case R.id.five: res.append("5");
                            break;

            case R.id.six: res.append("6");
                break;
            case R.id.seven: res.append("7");
                break;
            case R.id.eight: res.append("8");
                break;
            case R.id.nine: res.append("9");
                break;

            case R.id.plus: res.append("+");
                            operatorPressed = "+";
                break;

            case R.id.minus: res.append("-");
                operatorPressed = "-";
                break;
            case R.id.divide: res.append("/");
                operatorPressed = "/";
                break;
            case R.id.multiply: res.append("*");
                operatorPressed = "*";
                break;
            case R.id.clear: res.setText(" ");
                break;

            case R.id.equal: finalresult = evaluateExpression(res.getText().toString(), operatorPressed);
                res.setText(String.valueOf(finalresult));
                break;

            default: return;

        }

    }
    private double evaluateExpression(String res, String operatorPressed) {

        String[] tokens = res.split("\\+|-|\\*|\\/");
        double firstOperand = Double.parseDouble(tokens[0]);
        double secondOperand = Double.parseDouble(tokens[1]);

        switch(operatorPressed) {
            case "+":
                return firstOperand + secondOperand;
            case "-":
                return firstOperand - secondOperand;
            case "*":
                return firstOperand * secondOperand;
            case "/":
                return firstOperand / secondOperand;
            default:
                return 0;

        }

    }
}

xml

  <?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity"
    android:orientation="vertical">


    <TextView
        android:id="@+id/label"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="60dp"
        android:gravity="center"
        android:text="CALCULATOR"
        android:textColor="@color/black"
        android:textSize="30dp" />

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/res"
        android:layout_margin="30dp"
        android:textSize="20dp"
        android:hint="Result"
        android:gravity="end"/>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="20dp"
        android:layout_marginRight="20dp"
        android:layout_marginBottom="20dp">

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="9"
            android:textSize="20dp"
            android:id="@+id/nine"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="8"
            android:textSize="20dp"
            android:id="@+id/eight"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="7"
            android:textSize="20dp"
            android:id="@+id/seven"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="C"
            android:textSize="20dp"
            android:id="@+id/clear"
            android:background="@color/white"
            android:layout_weight="0.25"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="20dp"
        android:layout_marginRight="20dp"
        android:layout_marginBottom="20dp">

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="6"
            android:textSize="20dp"
            android:id="@+id/six"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="5"
            android:textSize="20dp"
            android:id="@+id/five"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="4"
            android:textSize="20dp"
            android:id="@+id/four"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="+"
            android:textSize="20dp"
            android:id="@+id/plus"
            android:background="@color/white"
            android:layout_weight="0.25"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="20dp"
        android:layout_marginRight="20dp"
        android:layout_marginBottom="20dp">

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="3"
            android:textSize="20dp"
            android:id="@+id/three"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="2"
            android:textSize="20dp"
            android:id="@+id/two"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="1"
            android:textSize="20dp"
            android:id="@+id/one"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="-"
            android:textSize="20dp"
            android:id="@+id/minus"
            android:background="@color/white"
            android:layout_weight="0.25"/>

    </LinearLayout>

    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginLeft="20dp"
        android:layout_marginRight="20dp"
        android:layout_marginBottom="20dp">

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="/"
            android:textSize="20dp"
            android:id="@+id/divide"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="0"
            android:textSize="20dp"
            android:id="@+id/zero"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="="
            android:textSize="20dp"
            android:id="@+id/equal"
            android:background="@color/white"
            android:layout_weight="0.25"/>

        <Button
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="*"
            android:textSize="20dp"
            android:id="@+id/multiply"
            android:background="@color/white"
            android:layout_weight="0.25"/>

    </LinearLayout>


</LinearLayout>


3b implicit

xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/myphone"
        android:hint="Enter the phone number"
        android:layout_margin="20dp"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/call"
        android:text="CALL"
        android:layout_margin="20dp"/>

</LinearLayout>

Java
package com.example.program3b;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    EditText myphone;
    Button call;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        call = findViewById(R.id.call);
        myphone = findViewById(R.id.myphone);

        call.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Uri myuri = Uri.parse("tel: " + myphone.getText().toString());
                Intent it = new Intent(Intent.ACTION_DIAL, myuri);
                startActivity(it);
            }
        });
    }
}

Manifest
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools">
    <uses-permission android:name="android.permission.CALL_PHONE"></uses-permission>
    <application
        android:allowBackup="true"
        android:dataExtractionRules="@xml/data_extraction_rules"
        android:fullBackupContent="@xml/backup_rules"
        android:icon="@mipmap/ic_launcher"
        android:label="@string/app_name"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/Theme.Program3b"
        tools:targetApi="31">
        <activity
            android:name=".MainActivity"
            android:exported="true">
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>

            <meta-data
                android:name="android.app.lib_name"
                android:value="" />
        </activity>
    </application>

</manifest>

3a explicit

main.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">


    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/name"
        android:hint="Enter your name"
        />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/click"
        android:text="Click"
        />



</LinearLayout>

main.java
package com.example.program3;

import androidx.appcompat.app.AppCompatActivity;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class MainActivity extends AppCompatActivity {

    EditText name;
    Button click;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        name = findViewById(R.id.name);
        click = findViewById(R.id.click);

        click.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent it = new Intent(MainActivity.this, SecondActivity.class);
                Bundle b = new Bundle();
                b.putString("name",name.getText().toString());
                it.putExtras(b);
                startActivity(it);
            }
        });
    }
}

second.xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".SecondActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:id="@+id/mytext"
        android:text="NAME COMES HERE"
        android:textSize="40dp"
        android:layout_gravity="center"/>

</LinearLayout>

second.java
package com.example.program3;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.widget.TextView;

public class SecondActivity extends AppCompatActivity {

    TextView myname;
    String namefromfirstactivity = " ";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_second);

        myname = findViewById(R.id.mytext);
        namefromfirstactivity = getIntent().getStringExtra("name");
        myname.setText(namefromfirstactivity);

    }
}

4. Database

XML
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout   xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="Enter the details below:"
        android:id="@+id/enter"
        android:layout_marginTop="60dp"
        />

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Name"
        android:id="@+id/name"
        android:layout_margin="20dp"
        />

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Age"
        android:id="@+id/age"
        android:layout_margin="20dp"
        />

    <EditText
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Contact"
        android:id="@+id/contact"
        android:layout_margin="20dp"
        />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp"
        android:id="@+id/insert"
        android:text="INSERT"
        android:background="@color/white"/>
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp"
        android:id="@+id/update"
        android:text="UPDATE"
        android:background="@color/white"/>
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp"
        android:id="@+id/delete"
        android:text="DELETE"
        android:background="@color/white"/>
    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="20dp"
        android:id="@+id/view"
        android:text="VIEW"
        android:background="@color/white"/>


</LinearLayout>

java
package com.example.program4;

import androidx.annotation.Nullable;
import androidx.appcompat.app.AlertDialog;
import androidx.appcompat.app.AppCompatActivity;

import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;
import android.widget.Toast;

import org.w3c.dom.Text;

public class MainActivity extends AppCompatActivity {

    TextView enter;
    EditText name, age, contact;
    Button insert, update, delete, view;

    DBHelper db;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        name = findViewById(R.id.name);
        age = findViewById(R.id.age);
        contact = findViewById(R.id.contact);

        insert = findViewById(R.id.insert);
        update = findViewById(R.id.update);
        delete = findViewById(R.id.delete);
        view = findViewById(R.id.view);

        db = new DBHelper(this);

        insert.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String nameTXT = name.getText().toString();
                String ageTXT = age.getText().toString();
                String contactTXT = contact.getText().toString();

                boolean qryStatus = db.insertData(nameTXT, contactTXT,ageTXT);

                if(qryStatus == true)
                {
                    Toast.makeText(MainActivity.this,"New Record Created", Toast.LENGTH_SHORT ).show();
                }
                else
                {
                    Toast.makeText(MainActivity.this,"New Record Creation Failed", Toast.LENGTH_SHORT ).show();
                }
            }
        });

        update.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String nameTXT = name.getText().toString();
                String ageTXT = age.getText().toString();
                String contactTXT = contact.getText().toString();

                boolean qryStatus = db.updateData(nameTXT, contactTXT,ageTXT);

                if(qryStatus == true)
                {
                    Toast.makeText(MainActivity.this,"Record Updated", Toast.LENGTH_SHORT ).show();
                }
                else
                {
                    Toast.makeText(MainActivity.this,"Record Updation Failed", Toast.LENGTH_SHORT ).show();
                }
            }
        });

        delete.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                String nameTXT = name.getText().toString();

                boolean qryStatus = db.deleteData(nameTXT);

                if(qryStatus == true)
                {
                    Toast.makeText(MainActivity.this,"Record Deleted", Toast.LENGTH_SHORT ).show();
                }
                else
                {
                    Toast.makeText(MainActivity.this,"Record Deletion Failed", Toast.LENGTH_SHORT ).show();
                }
            }
        });

        view.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Cursor res = db.viewData();

                if(res.getCount() == 0)
                {
                    Toast.makeText(MainActivity.this,"No Record Exist", Toast.LENGTH_SHORT ).show();
                }
                else
                {
                    StringBuffer buffer = new StringBuffer();
                    while(res.moveToNext())
                    {
                        buffer.append("name :" + res.getString(0) + "\n");
                        buffer.append("age :" + res.getString(2) + "\n");
                        buffer.append("contact :" + res.getString(1) + "\n");
                    }
                    AlertDialog.Builder builder = new AlertDialog.Builder(MainActivity.this);
                    builder.setCancelable(true);
                    builder.setTitle("user data");
                    builder.setMessage(buffer.toString());
                    builder.show();
                }
            }
        });

    }
}

dbhelper.java
package com.example.program4;
import android.content.ContentValues;
import android.content.Context;
import android.database.Cursor;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteOpenHelper;

import androidx.annotation.Nullable;

public class DBHelper extends SQLiteOpenHelper {
    public DBHelper(@Nullable Context context) {
        super(context, "userData.db", null, 1);

    }

    @Override
    public void onCreate(SQLiteDatabase db) {
        db.execSQL("create Table userDetails(name TEXT primary key, contact TEXT, age TEXT)");
    }


    @Override
    public void onUpgrade(SQLiteDatabase db, int oldversion, int newversion) {
        db.execSQL("drop Table if exists userDetails");
    }

    public boolean insertData(String name, String contact, String age)
    {
        SQLiteDatabase db = this.getWritableDatabase();
        ContentValues contentValues = new ContentValues();
        contentValues.put("name",name);
        contentValues.put("contact",contact);
        contentValues.put("age",age);
        long result = db.insert("userDetails", null, contentValues);
        if(result == -1)
        {
            return false;
        }
        else
        {
            return true;
        }
    }

    public boolean updateData(String name, String contact, String age)
    {
        SQLiteDatabase db = this.getWritableDatabase();
        ContentValues contentValues = new ContentValues();
        contentValues.put("contact",contact);
        contentValues.put("age",age);
        Cursor cursor = db.rawQuery("Select * from userDetails where name = ?", new String[] {name});
        if(cursor.getCount() > 0)
        {
            long result = db.update("userDetails", contentValues, "name=?", new String[] {name});
            if (result == -1) {
                return false;
            } else {
                return true;
            }
        }
        else
        {
            return false;
        }

    }


    public boolean deleteData(String name)
    {
        SQLiteDatabase db = this.getWritableDatabase();
        ContentValues contentValues = new ContentValues();

        Cursor cursor = db.rawQuery("Select * from userDetails where name = ?", new String[] {name});
        if(cursor.getCount() > 0)
        {
            long result = db.delete("userDetails", "name=?", new String[] {name});
            if (result == -1) {
                return false;
            } else {
                return true;
            }
        }
        else
        {
            return false;
        }

    }

    public Cursor viewData()
    {
        SQLiteDatabase db = this.getWritableDatabase();

        Cursor cursor = db.rawQuery("Select * from userDetails", null);
        return cursor;

    }
}

5. Media player

xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity"
    android:background="#7716">

    <TextView
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:text="@string/songname"
        android:id="@+id/songname"
        android:textSize="30dp"
        android:gravity="center"
        android:layout_margin="30dp"
        />

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:text="Play"
        android:id="@+id/play"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:text="Pause"
        android:id="@+id/pause"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:text="Forward"
        android:id="@+id/forward"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:text="Reset"
        android:id="@+id/reset"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:text="Rewind"
        android:id="@+id/rewind"/>

    <Button
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_marginLeft="30dp"
        android:layout_marginRight="30dp"
        android:text="Stop"
        android:id="@+id/stop"/>


</LinearLayout>

java
package com.example.program5;

import androidx.appcompat.app.AppCompatActivity;

import android.media.MediaPlayer;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    Button play,reset,  pause, forward, rewind, stop;
    MediaPlayer mediaPlayer,mediaPlayer1 ;
    int starttime = 0;
    int stoptime = 0;
    int forwardtime = 5000;
    int backwardtime = 5000;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        play = findViewById(R.id.play);
        pause = findViewById(R.id.pause);
        forward = findViewById(R.id.forward);
        rewind = findViewById(R.id.rewind);
        reset = findViewById(R.id.reset);
        stop = findViewById(R.id.stop);



        play.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(MainActivity.this, "playing media now",Toast.LENGTH_SHORT).show();
                mediaPlayer =  MediaPlayer.create(MainActivity.this, R.raw.rain);
                //mediaPlayer1 =  MediaPlayer.create(MainActivity.this, R.raw.rain);
                mediaPlayer.start();
            }
        });

        pause.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(MainActivity.this, "pausing media now",Toast.LENGTH_SHORT).show();
                mediaPlayer.pause();
            }
        });

        reset.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(MainActivity.this, "reset media now",Toast.LENGTH_SHORT).show();

                mediaPlayer.seekTo(starttime);
                mediaPlayer.start();
            }
        });

        forward.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Toast.makeText(MainActivity.this, "fowarding media now",Toast.LENGTH_SHORT).show();

                int currentpos = mediaPlayer.getCurrentPosition() ;
                if((currentpos+forwardtime) <= (stoptime = mediaPlayer.getDuration())){
                    mediaPlayer.seekTo(currentpos+forwardtime);
                } }
        });

        rewind.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                Toast.makeText(MainActivity.this, "rewinding media now",Toast.LENGTH_SHORT).show();

                int currentpos = mediaPlayer.getCurrentPosition() ;
                if((currentpos-backwardtime) >= 0){
                    mediaPlayer.seekTo(currentpos-backwardtime);
                } }
        });

        stop.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Toast.makeText(MainActivity.this, "stopping media now",Toast.LENGTH_SHORT).show();
                mediaPlayer.stop();
                mediaPlayer =  mediaPlayer1;
            }
        });


    }
}