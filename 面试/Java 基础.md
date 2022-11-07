# 语法基础
## string、stringbuffer和stringbuilder的区别是什么？
可变和适用范围:<br />String对象是不可变的，而StringBuffer和StringBuilder是可变字符序列。每次对String的操作相当于生成一个新的String对象，而对StringBuffer和StringBuilder的操作是对对象本身的操作，而不会生成新的对象，所以对于频繁改变内容的字符串避免使用String，因为频繁的生成对象将会对系统性能产生影响。

线程安全:<br />String由于有final修饰，是immutable的，安全性是简单而纯粹的。StringBuilder和StringBuffer的区别在于StringBuilder不保证同步，也就是说如果需要线程安全需要使用StringBuffer，不需要同步的StringBuilder效率更高, StringBuffer类中的方法都添加了synchronized关键字,由此来实现同步。

Java9改进了字符串（包括String、StringBuffer、StringBuilder）的实现。在Java9以前字符串采用char[]数组来保存字符，因此字符串的每个字符占2字节；而Java9的字符串采用byte[]数组再加一个encoding-flag字段来保存字符，因此字符串的每个字符只占1字节。所以Java9的字符串更加节省空间，字符串的功能方法也没有受到影响。

## final、finalize 和 finally 的不同之处?

### final
final是一个修饰符（关键字）

1. **修饰类：**

如果一个类被声明为 final，意味着它不能再派生出新的子类，不能作为父类被继承。因此 一个类不能既被声明为 abstract 的，又被声明为 final 的。

2. **修饰方法：**

被final修饰的方法无法被重写，但是可以重载，类的private方法会隐式地被指定为final方法。<br />在早期java版本中，将方法设置为final,可以提升效率,会将final方法转为内嵌调用。但是如果方法过于庞大，可能看不到内嵌调用带来的任何性能提升。在最近的Java版本中，不需要使用final方法进行这些优化了。因此，如果只有在想明确禁止 该方法在子类中被覆盖的情况下才将方法设置为final的。

3. **修饰变量**：

当用final作用于类的成员变量时，成员变量（注意是类的成员变量，局部变量只需要保证在使用之前被初始化赋值即可）必须在定义时或者构造器中进行初始化赋值，而且final变量一旦被初始化赋值之后，就不能再被赋值了。
### finally
try 关键字最后可以定义 finally 代码块。 finally 块中定义的代码，总是在 try 和任何 catch 块之后、方法完成之前运行。正常情况下，不管是否抛出或捕获异常 finally 块都会执行。<br />finally块不会被执行的四种情况

1. 在finally语句块中发生了异常。
2. 在前面的代码中用了System.exit()退出程序。
3. 程序所在的线程死亡。
4. 关闭CPU。

如果在catch和finally块中都有return语句，会使用finally块中都有return的值，这是因为在 return的时候会把返回值压入栈，并把返回值赋值给栈中的局部变量， 最后把栈顶的变量值作为函数返回值。所以在 finally中的返回值就会覆盖 try/catch中的返回值，如果 finally中不执行 return语句，在 finally中修改返回变量的值，不会影响返回结果。

## String、StringBuffer与StringBuilder的区别


