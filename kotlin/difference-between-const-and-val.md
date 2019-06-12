# Difference between a `const` and `val` in kotlin

consts are compile time constants. Meaning that their value has to be assigned during compile time, unlike vals, where it can be done at runtime.

This means, that consts can never be assigned to a function or any class constructor, but only to a String or primitive.

For example:
```
const val foo = complexFunctionCall()   //Not okay
val fooVal = complexFunctionCall()  //Okay

const val bar = "Hello world"           //Also okay
```

[Reference](https://stackoverflow.com/a/37596023/4291698)
