# Android-BottomNavigationView-example 

![Detail step by step explanation](https://posttrutherablog.com/2017/03/24/android-bottomnavigationview-example/)
It is an easiest step by step implementation for Android's BottomNavigationView in 5 minutes.

[BottomNavigationView](https://posttrutherablog.files.wordpress.com/2017/03/posttrutherablog_image_bottomnavigation.gif?w=736)

## Step 1 : Add the dependencies
~~~
compile ‘com.android.support:design:25.1.0’
~~~

## Step 2 : Add the widget to XML Layout

We simply need to add the Bottom Navigation View widget to the XML layout file. Remember that this should be aligned with the bottom of the screen with all content displaying above it. We can add this view like so:

~~~

<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout
    android:id="@+id/activity_main"
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context="com.truiton.bottomnavigation.MainActivity">
 
    <FrameLayout
        android:id="@+id/frame_layout"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        android:layout_above="@+id/navigation"
        android:animateLayoutChanges="true">
 
    </FrameLayout>
 
    <android.support.design.widget.BottomNavigationView
        android:id="@+id/navigation"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_alignParentBottom="true"
        android:background="@color/colorPrimary"
        app:itemIconTint="@color/nav_item_state_list"
        app:itemTextColor="@color/nav_item_state_list"
        app:menu="@menu/bottom_navigation_items"/>
</RelativeLayout>

~~~

## Step 3: Create a menu to display

~~~

<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <item
        android:id="@+id/action_item1"
        android:icon="@drawable/ic_account_box_black_24dp"
        android:title="@string/item_1"/>
    <item
        android:id="@+id/action_item2"
        android:icon="@drawable/ic_account_circle_black_24dp"
        android:title="@string/item_2"/>
    <item
        android:id="@+id/action_item3"
        android:icon="@drawable/ic_assignment_ind_black_24dp"
        android:title="@string/item_3"/>
~~~

## Step 4: Define bottom navigation view in Java file.

Define the BottomNavigationView inside the onCreate (AppCompactActivity) or onCreateView (Fragment).

~~~

BottomNavigationView bottomNavigationView = (BottomNavigationView)
        findViewById(R.id.navigation);
        
bottomNavigationView.setOnNavigationItemSelectedListener
        (new BottomNavigationView.OnNavigationItemSelectedListener() {
            @Override
            public boolean onNavigationItemSelected(@NonNull MenuItem item) {
                Fragment selectedFragment = null;
                switch (item.getItemId()) {
                    case R.id.action_item1:
                        selectedFragment = ItemOneFragment.newInstance();
                        break;
                    case R.id.action_item2:
                        selectedFragment = ItemTwoFragment.newInstance();
                        break;
                    case R.id.action_item3:
                        selectedFragment = ItemThreeFragment.newInstance();
                        break;
                }
                FragmentTransaction transaction = getSupportFragmentManager().beginTransaction();
                transaction.replace(R.id.frame_layout, selectedFragment);
                transaction.commit();
                return true;
            }
        });
        
~~~
        

## Step 5: Run it and Done it

![Test it](https://posttrutherablog.files.wordpress.com/2017/03/screenshot_20170324-021336.png)
  
  
        
