# How to constrain one side of a view to more than one view in ConstraintLayout?
I recently had a requirement where a textview had to be constrained on the left to two other text views as in 

`textView3` `layout_constraintStart_toEndOf` to `textView1` if `textView1.width` > `textView2.width` 
                                          
                                          or

`textView3` `layout_constraintStart_toEndOf` to `textView2` if `textView2.width` > `textView1.width`

This scenario can easily occur if the text in these textviews is going to be dynamic or if your app supports multiple languages.
My first thought for handling this was to wrap `textView1` and `textView2` inside a `LinearLayout` with width equal to `wrap_content`, 
but then that would have increased the hierarchy of my views by one. Given ConstraintLayout was designed to flatten view hierarchy 
I looked if constraint layout provided a solution for this which it did. For handling such scenarios constraint layout provides a view called Barrier.
You add Barrier to your constraint layout, add `textView1` and `textView2` to barrier using `constraint_referenced_ids`, set `barrierDirection`
to `end` since `barrier` is to be applied to `end` of `textView1` and `textView2` and finally put `layout_constraintStart_toEndOf`
of `textView3` to `barrier`. This way `textView3` will be constrained to both `textView2` and `textView1`.

```
<?xml version="1.0" encoding="utf-8"?>
<android.support.constraint.ConstraintLayout 
  xmlns:android="http://schemas.android.com/apk/res/android"
  xmlns:app="http://schemas.android.com/apk/res-auto"
  android:layout_width="match_parent"
  android:layout_height="match_parent">

  <TextView
    android:id="@+id/textView1"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="16dp"
    android:layout_marginTop="16dp"
    android:text="@string/title"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent" />

  <TextView
    android:id="@+id/textView2"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    android:layout_marginStart="16dp"
    android:layout_marginTop="8dp"
    android:text="@string/description"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toBottomOf="@+id/textView1" />

  <android.support.constraint.Barrier
    android:id="@+id/barrier"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:barrierDirection="end"
    app:constraint_referenced_ids="textView2,textView1" />

  <TextView
    android:id="@+id/textView3"
    android:layout_width="0dp"
    android:layout_height="wrap_content"
    android:layout_marginStart="8dp"
    android:text="@string/lorem_ipsum"
    app:layout_constraintStart_toEndOf="@+id/barrier"
    app:layout_constraintTop_toTopOf="parent" />

</android.support.constraint.ConstraintLayout>
```
