# Null safety and safe calls

- `?. - safe call operator`  
```
val b: String? = null
println(b?.length)
```
This returns b.length if b is not null, and null otherwise. The type of this expression is Int?.

- `?: - elvis operator`
```
val l = b?.length ?: -1
```
If the expression to the left of ?: is not null, the elvis operator returns it, otherwise it returns the expression to the right. Note that the right-hand side expression is evaluated only if the left-hand side is null.

- `!! - not-null assertion operator`
```
val l = b!!.length
```
Converts any value to a non-null type and throws an exception if the value is null.
