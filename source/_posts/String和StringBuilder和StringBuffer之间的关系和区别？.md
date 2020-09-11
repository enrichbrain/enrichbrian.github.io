   首先，String与StringBuilder和StringBuffer是不可以变的，从String类源码可以看见，是用来final字符数组来保护字符串，**private final char value[]**。因此原则上是不可以改变的，但是可以用反射可以访问私有成员， 然后反射出 String 对象中的 value 属性， 进而改变通过获得的 value 引用改变数组的结构。
	然后StringBuilder和StringBuffer之间都是继承父类**AbstractStringBuilder** ，在AbstractStringBuilder 中没有用final来修饰char[] value，所以是可以变的。
	**1.三者之间的线程安全性**
	 但是StringBuilder没有对方法加入同步锁，所以是非线程安全的。然而StringBuffer是加入了方法同步锁，所以和String一样都是线程安全的。
	 **2.三者的性能**
	 每次对 String 类型进行改变的时候，都会生成一个新的 String 对象，然后将指针指向新的 String 对象。StringBuffer 每次都会对 StringBuffer 对象本身进行操作，而不是生成新的对象并改变对象引用。相同情况下使用 StringBuilder 相比使用 StringBuffer 仅能获得 10%~15% 左右的性能提升，但却要冒多线程不安全的风险。
	**对于三者使用的总结：**

 1. 操作少量的数据: 适用 String
 2. 单线程操作字符串缓冲区下操作大量数据: 适用 StringBuilder
 3. 多线程操作字符串缓冲区下操作大量数据: 适用 StringBuffer

在看完之后总结得出以上自己的理解
> 原文链接：https://blog.csdn.net/qq_34337272/article/details/103931508

