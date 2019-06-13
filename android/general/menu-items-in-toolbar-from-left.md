# How to add menu items in toolbar from left

- To add a new android.support.v7.widget.ActionMenuView as child of the Toolbar, set its gravity to top|start, and then add the menu to that action menu view in your Activity, something like this

my_toolbar.xml
```
<android.support.v7.widget.Toolbar
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/tToolbar"
    android:layout_height="?attr/actionBarSize"
    android:layout_width="match_parent"
    android:background="?attr/colorPrimary"
    android:gravity="center_vertical|start"
    app:theme="@style/ThemeOverlay.AppCompat.Dark.ActionBar"
    app:popupTheme="@style/ThemeOverlay.AppCompat.Light">

    <android.support.v7.widget.ActionMenuView
        android:id="@+id/amvMenu"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"/>
</android.support.v7.widget.Toolbar>
```

my_activity.xml
```
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <!--Toolbar-->
    <include
        android:id="@+id/tToolbar"
        android:layout_height="wrap_content"
        android:layout_width="match_parent"
        layout="@layout/my_toolbar" />
</RelativeLayout>

```
MyActivity.java
```
import android.os.Bundle;
import android.support.v7.app.ActionBarActivity;
import android.support.v7.widget.ActionMenuView;
import android.support.v7.widget.Toolbar;
import android.view.Menu;
import android.view.MenuInflater;
import android.view.MenuItem;

public final class MyActivity extends ActionBarActivity {
  private ActionMenuView amvMenu;

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    // this layout includes the custom toolbar my_toolbar.xml
    setContentView(R.layout.my_activity);

    Toolbar t = (Toolbar) findViewById(R.id.tToolbar);
    amvMenu = (ActionMenuView) t.findViewById(R.id.amvMenu);
    amvMenu.setOnMenuItemClickListener(new ActionMenuView.OnMenuItemClickListener() {
      @Override
      public boolean onMenuItemClick(MenuItem menuItem) {
        return onOptionsItemSelected(menuItem);
      }
    });

    setSupportActionBar(t);
    getSupportActionBar().setTitle(null);
    getSupportActionBar().setDisplayHomeAsUpEnabled(true);
  }

  @Override
  public boolean onCreateOptionsMenu(Menu menu) {
    MenuInflater inflater = getMenuInflater();
    // use amvMenu here
    inflater.inflate(R.menu.my_activity_menu, amvMenu.getMenu());
    return true;
  }

  @Override
  public boolean onOptionsItemSelected(MenuItem item) {
    // Do your actions here
    return true;
  }
}
```

[Reference](https://stackoverflow.com/a/29809691/4291698)
