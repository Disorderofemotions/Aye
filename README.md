<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    tools:context=".MainActivity">

    <TextView
        android:id="@+id/text_view_p1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Player 1: 0"
        android:layout_marginBottom="8dp"/>

    <TextView
        android:id="@+id/text_view_p2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Player 2: 0"
        android:layout_below="@id/text_view_p1"
        android:layout_marginBottom="8dp"/>

    <GridLayout
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:rowCount="3"
        android:columnCount="3">

        <Button
            android:id="@+id/button_00"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text=""
            android:layout_column="0"
            android:layout_row="0"/>

        <!--Buttons for other cells in the grid, with similar attributes-->

    </GridLayout>

    <Button
        android:id="@+id/button_reset"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Reset Game"
        android:layout_below="@id/text_view_p2"/>

</RelativeLayout>
