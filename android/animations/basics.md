# How to add smooth animations without adding any extra code (almost no code :P)

Whenever you are toggling the visibility of views within a container adding a simple line of code before the toggle could provide a smooth transition
from one scene to another. The line is `TransitionManager.beginDelayedTransition(container)`. And thats all, you will have a smooth
animation within the container.

Reference [Animate all the things. Transitions in Android](https://medium.com/@andkulikov/animate-all-the-things-transitions-in-android-914af5477d50)
