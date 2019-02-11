# How to have auto adjust text size in a text view

If you want to auto adjust text size in a text view depending on the content of the text view you can use 
`app:autoSizeTextType="uniform"` attribute in your textview xml. Thats it. You can provide max and min text size can grow or 
shrink, you can also provide the step count at which it grows or shrink. For more information refer [here](https://developer.android.com/guide/topics/ui/look-and-feel/autosizing-textview).


    <?xml version="1.0" encoding="utf-8"?>
    <LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
      xmlns:tools="http://schemas.android.com/tools"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:orientation="vertical"
      android:padding="4dp">

        <TextView
            android:id="@+id/tv_count"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:gravity="center"
            android:lines="1"
            android:textColor="@color/black"
            app:autoSizeMinTextSize="20sp"
            app:autoSizeTextType="uniform"
            tools:text="100" />

        <TextView
          android:id="@+id/tv_title"
          android:layout_width="wrap_content"
          android:layout_height="wrap_content"
          android:lines="2"
          tools:text="@string/desc"
          android:textColor="@color/dark_gray" />

    </LinearLayout>
