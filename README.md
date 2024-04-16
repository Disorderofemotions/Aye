<TimePicker
    android:id="@+id/time_picker"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
/>

<Button
    android:id="@+id/set_alarm_button"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:text="Set Alarm"
/>






<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".AlarmActivity">

    <EditText
        android:id="@+id/day_edit_text"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"/>

    <EditText
        android:id="@+id/time_edit_text"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/day_edit_text"/>

    <Button
        android:id="@+id/dismiss_button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Dismiss"
        android:layout_below="@id/time_edit_text"/>

</RelativeLayout>
