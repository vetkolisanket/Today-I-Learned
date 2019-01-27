# How to add transitions to an activity via xml?

1. To enable content transitions add the below code in your theme in v21/styles.xml. (Since they would work only from 21)
```
<!-- enable window content transitions -->
<item name="android:windowActivityTransitions">true</item>
```
2. Next define your transition in your transitions folder. Below I am using a simple explode animation. In your transition/explode.xml add the below code
```
<?xml version="1.0" encoding="utf-8"?>
<transitionSet xmlns:android="http://schemas.android.com/apk/res/android">
    <explode/>
</transitionSet>
```


3. Add the above mentioned transition as the enter and exit transition
```
<!-- specify enter and exit transitions -->
<item name="android:windowEnterTransition">@transition/explode</item>
<item name="android:windowExitTransition">@transition/explode</item>
```

4. While starting your activity, start it the below mentioned way
```
startActivity(ExplodeActivity.newIntent(this), ActivityOptionsCompat.makeSceneTransitionAnimation(this).toBundle())
```

Thats it and you'll have an explode animation while starting your activity. You can replace explode with any animation of your choice like fade in, fade out, slide etc

Reference [Stack overflow answer](https://stackoverflow.com/a/48473951/4291698)
