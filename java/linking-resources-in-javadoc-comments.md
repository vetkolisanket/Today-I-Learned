# How to link resources in javadoc comments

To link resources like methods or classes in javadocs you can use `{@link package.class#member label}` inside your javadoc comments. The label is optional.

`{@link package.class#member label}` - can be used to refer to a class or a method in between your description.

`{@linkplain package.class#member label}` - same as @link the difference being @link's label is displayed in code font whereas 
@linkplain's label is displayed in standard font

`@see package.class#member label` - If you want to specify a class or a method in a separate section, you can use @see annotaion. I personally use this annotation when some class/method is very important to explain another class or method or is being refered to multiple times in the description
