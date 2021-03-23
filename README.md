# MainActivity
package com.college.addressbook;

import java.util.ArrayList;
import java.util.List;

import android.app.Activity;

import android.os.Bundle;
import android.widget.ListView;

public class MainActivity extends Activity {


    private ListView lvname;

    @Override
    public void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);


        List<PhoneBook> listPhoneBook = new ArrayList<PhoneBook>();
        listPhoneBook.add(new PhoneBook(
                ""));

        PhoneBookAdapter adapter = new PhoneBookAdapter(this, listPhoneBook);
        lvname.setAdapter(adapter);
    }
}
# PhoneBook
package com.college.addressbook;

public class PhoneBook {

    private String mName;
    public PhoneBook(String mName){
}
    public void setName(String name) {
        mName = name;
    }
    public String getName() {
        return mName;
    }}
 # PhoneBookAdapter
 package com.college.addressbook;

import java.util.List;

import java.util.List;

import android.content.Context;
import android.view.LayoutInflater;
import android.view.View;
import android.view.ViewGroup;
import android.widget.BaseAdapter;
import android.widget.TextView;

public class PhoneBookAdapter extends BaseAdapter {
    private Context mContext;
    private List<PhoneBook> mListPhoneBook;

    public PhoneBookAdapter(Context context, List<PhoneBook> list) {
        mContext = context;
        mListPhoneBook = list;

    }

    @Override
    public int getCount() {
        return mListPhoneBook.size();
    }

    @Override
    public Object getItem(int pos) {
        return mListPhoneBook.get(pos);
    }

    @Override
    public long getItemId(int pos) {
        return pos;
    }

    @Override
    public View getView(int pos, View convertView, ViewGroup parent) {
        PhoneBook entry = mListPhoneBook.get(pos);

        // inflating list view layout if null
        if(convertView == null) {
            LayoutInflater inflater = LayoutInflater.from(mContext);
            convertView = inflater.inflate(R.layout.phonebook_row, null);
        }

        TextView tvName = (TextView)convertView.findViewById(R.id.tvName);
        tvName.setText(entry.getName());
        return convertView;
    }
}

 
 # Activitymain.XML
 <?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="horizontal"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    >

    <LinearLayout
        android:layout_width="784dp"
        android:layout_height="wrap_content"
        android:orientation="vertical">

        <TextView
            android:id="@+id/tvName"
            android:layout_width="fill_parent"
            android:layout_height="95dp"
            android:textStyle="bold" />

        <ListView
            android:id="@+id/listPhone"
            android:layout_width="513dp"
            android:layout_height="893dp" />

    </LinearLayout>

</LinearLayout>
