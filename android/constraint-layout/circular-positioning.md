# Circular Positioning

You can constrain a widget center relative to another widget center, at an angle and a distance. This allows you to position a widget on a circle. The following attributes can be used:

`layout_constraintCircle` : references another widget id

`layout_constraintCircleRadius` : the distance to the other widget center

`layout_constraintCircleAngle` : which angle the widget should be at (in degrees, from 0 to 360)

```
<Button android:id="@+id/buttonA" ... />
  <Button android:id="@+id/buttonB" ...
      app:layout_constraintCircle="@+id/buttonA"
      app:layout_constraintCircleRadius="100dp"
      app:layout_constraintCircleAngle="45" />
```
