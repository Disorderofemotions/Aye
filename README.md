<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".AlarmActivity">

    <TextView
        android:id="@+id/timeEditText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_centerInParent="true" />

    <Button
        android:id="@+id/snoozeButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/timeEditText"
        android:layout_centerHorizontal="true"
        android:text="Snooze Alarm" />

    <EditText
        android:id="@+id/dayEditText"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_above="@id/timeEditText"
        android:layout_centerHorizontal="true"
        android:hint="Enter Day" />

</RelativeLayout>
