# Tiny Dancer - A real time frames per second measuring library for Android

As android developers we all face this common issue where we have this screen which is glitchy/stutters/janky which we would like to improve
but we are not really sure if the changes we made improved or degraded the performance further. I recently came across this library
[Tiny Dancer](https://github.com/friendlyrobotnyc/TinyDancer) which displays frames per second rendered on the screen in real time.
For smooth transitions and animations an FPS of 60 is recommended, when this FPS drops below 60 users start experiencing stutter.
You can use this library to check which screens within your app need to be optimised in terms of rendering and if any changes you
have made within a screen have improved or deteriorated the rendering. It is quite easy to integrate as well.
