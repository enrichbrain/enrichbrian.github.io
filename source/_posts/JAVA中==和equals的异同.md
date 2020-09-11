
  在JAVA中，用‘==’比较是看两个的地址是否相同，如果相同就会返回true，如果不同就会返回false。也就是说如果 Integer a = new Integer() 和 Integer b = new Integer()中的a和b用 “= =”比较就会返回false,因为创建了两个不同的对象，所以他们的地址不同。特别提醒，如果Integer c = 129 和int d = 129，如果c 和d用“= =”比较就会报出false，因为integer的数值范围为-128~127,如果超过了这个范围就会new一个Integer对象，因此两个就不同。
	equals在String中被重写过的，在String中就是比较两个是不是值相同，而不是比较是否地址相同，但是在Object比较中是比较地址是否相同，也就是说，上面的a和b用equals比较就会返回true。
	**当创建 String 类型的对象时，虚拟机会在常量池中查找有没有已经存在的值和要创建的值相同的对象，如果有就把它赋给当前引用。如果没有就在常量池中重新创建一个 String 对象。**
