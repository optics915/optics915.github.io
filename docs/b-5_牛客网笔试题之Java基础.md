> 作者：optics915。
>
> **介绍:** 这是一个随手化的类似笔记的个人博客 作者: **[optics915](https://optics915.gitee.io/docsify-blog)** 。一般会在此记录一些从知乎、B站、GitHub上学来的有意思的操作，每一个过程都先自己操作成功之后再将其记录下来，以方便日后碰到相似类型时有理可依。

这个系列的文章是之前在牛客网上做基础题时遇到的一些自己认为有难度以及做错的题目，某种程度上这些题目可以给面试带来一些辅助作用，很多是基础问题，有利于面试前的突击。

#### 1. 关于以下application,说法正确是什么？
	1	public class Test {
	2	    static int x=10;
	3	    static {x+=5;}
	4	    public static void main(String[] args) //4
	5	        {
	6	        System.out.println("x="+x);
	7	    }
	8	    static{x/=3;};
	9	}//9s
		a. 选项	B
			i. 4行与9行不能通过编译，因为缺少方法名和返回类型
			ii. 编译通过，执行结果是：x=5
			iii. 编译通过，执行结果是：x=3
			iv. 9行不能通过编译，因为只能有一个静态初始化器
		b. 解析
			i. 执行顺序，静态代码块先于主方法执行，静态代码块之间遵从代码顺序执行。 
			ii. 所以：先初始化静态变量x=10；//x=10 
			iii. 执行第一个静态代码块，x=x+5; //x=15 
			iv. 执行第二静态代码块 x=x/3; //x=5 
			v. 执行主方法： 输出x=5 
			vi. 拓展一下，在类中定义的{}之间被称为构造块，构造块相对于构造方法先执行，构造块之间按照代码编译顺序执行 
			vii. 此外还有普通代码块，存在于方法之中。
		c. 拓展
			i. 类实例创建过程：按照父子继承关系进行初始化，首先执行父类的初始化块部分，然后是父类的构造方法；再执行本类继承的子类的初始化块，最后是子类的构造方法
			ii.  类实例销毁时候，首先销毁子类部分，再销毁父类部分
#### 2. 下面的程序 编译运行后，在屏幕上显示的结果是（）
		public class test {
		public static void main(String args[]) {
		int x,y;
		x=5>>2;
		y=x>>>2;
		System.out.println(y);
		}
		}
		a. 选项	
			i. 0
			ii. 2
			iii. 5
			iv. 80
		b. 解析
			i. 5的二进制是0101。 
			ii. x=5>>2 （>>带符号右移）
			iii. 将0101右移2位，为：0001。 
			iv. y=x>>>2 （>>>无符号右移，左边空缺补充为0）
			v. 将0001右移2位，补0。结果为：0000。
		c. 补充
			i. Java中的位运算符： 
				1) >>表示右移，如果该数为正，则高位补0，若为负数，则高位补1； 
				2) >>>表示无符号右移，也叫逻辑右移，即若该数为正，则高位补0，而若该数为负数，则右移后高位同样补0。
			ii. 左移n位：相当于乘以2^n
			iii. 右移n位：相当于除以2^n
#### 3. 根据以下代码段，下列说法中正确的是(    )。
	public class Parent {
	    private void m1(){}
	    void m2(){}
	    protected void m3(){}
	    public static void m4(){}
	}
		a. 选项	C
			i. 子类中一定能够继承和覆盖Parent类的m1方法
			ii. 子类中一定能够继承和覆盖Parent类的m2方法
			iii. 子类中一定能够继承和覆盖Parent类的m3方法
			iv. 子类中一定能够继承和覆盖Parent类的m4方法
		b. 解析
			i. D:父类的静态方法可以被子类继承，但是不能被重写（覆盖），静态方法在类加载时就加载到方法区了（1.8后是元空间），如果在子类写了个一样的方法，那是属于子类的另一个静态方法了，不是重写。
			ii. 重写针对的都是可见的实例方法，对于私有方法和静态方法都不能重写。
#### 4. 关于下面的程序Test.java说法正确的是(    )。
	复制代码
	1	public class Test {
	2	    static String x="1";
	3	    static int y=1;
	4	    public static void main(String args[]) {
	5	        static int z=2;
	6	        System.out.println(x+y+z);
	7	    }
	8	}
		a. 选项	D
			i. 3
			ii. 112
			iii. 13
			iv. 程序有编译错误
		b. 解析
			i. 被static修饰的变量称为静态变量，静态变量属于整个类，而局部变量属于方法，只在该方法内有效，所以static不能修饰局部变量
			ii. static 修饰的变量属于类,只能定义在类中方法外，故static int z=2;错了
		c. 补充
			i. 考虑下面三种情况：
			1	System.out.println(1 + 2 + "3");
			2	System.out.println("1" + 2 + 3);
			3	System.out.println(1 + "2" + 3);
			ii. 其输出结果分别为：33    123    123 
			iii. 系统会按照从左到右的顺序依次执行“+”运算。因此1+2+“3”会先执行1+2，其结果3再与“3”相加，即为33
#### 5. 下面属于JSP内置对象的是？ 
		a. 选项	ABCD
			i. out对象
			ii. response对象
			iii. application对象
			iv. page对象
		b. 解析
			i. 9个内置对象
				1、pageContext 表示页容器 EL表达式、 标签 、上传 
				2、request 服务器端取得客户端的信息：头信息 、Cookie 、请求参数 ，最大用处在MVC设计模式上 
				3、response 服务器端回应客户端信息：Cookie、重定向 
				4、session 表示每一个用户，用于登录验证上 
				5、application 表示整个服务器 
				6、config 取得初始化参数，初始化参数在web.xml文件中配置 
				7、exception 表示的是错误页的处理操作 
				8、page 如同this一样，代表整个jsp页面自身 
				9、out 输出 ，但是尽量使用表达式输出
#### 6. 以下哪项不属于java类加载过程？
		a. 选项	B
			i. 生成java.lang.Class对象
			ii. int类型对象成员变量赋予默认值
			iii. 执行static块代码
			iv. 类方法解析
		b. 解析
			i. 类的加载包括：加载，验证，准备，解析，初始化。 
				1) 选项A：生成java.lang.Class对象是在加载时进行的。生成Class对象作为方法区这个类的各种数据的访问入口。 
				2) 选项B：既然是对象成员，那么肯定在实例化对象后才有。在类加载的时候会赋予初值的是类变量，而非对象成员。
				3) 选项C：这个会调用。可以用反射试验。 
				4) 选项D：类方法解析发生在解析过程。
				![](https://s3.ax1x.com/2021/03/16/6y5Aeg.jpg)
				![](https://s3.ax1x.com/2021/03/16/6yoUsK.jpg)
#### 7. 关于抽象类叙述正确的是？ ( )
		a. 选项	B
			i. 抽象类不能实现接口
			ii. 抽象类必须有“abstract class”修饰
			iii. 抽象类必须包含抽象方法
			iv. 抽象类也有类的特性，可以被实例化
		b. 解析
			i. A.抽象类是可以实现接口的，而且抽象类也可以继承自抽象类 
			ii. C.抽象类指有abstract修饰的class，其可以包含抽象方法，也可以不包含 
			iii. D.抽象类和接口都是不能被实例化的，只有具体的类才可以被实例化
		c. 补充
			i. 抽象类和接口的区别：
				1) 不同点：
					a) 1.抽象类可以实现接口，接口不能继承类；
					b) 2.抽象类可以实现多个接口，接口不能实现接口；
					c) 3.抽象类是用abstract class，接口是用interface；
					d) 4.接口的子类必须实现所有接口函数，抽象函数的子类可以不覆写父类的抽象方法，但子类也要申明为抽象类；子类可以选择覆写父类的非抽象方法；
				2) 相同点：
					a) 1.抽象类和接口都不能直接实例化；
					b) 2.抽象类要被子类继承，接口要被类实现；
#### 8. java中下面哪个能创建并启动线程（）
	1	public class MyRunnable implements Runnable          { 
	2	     public void run()             { 
	3	         //some code here 
	4	     } 
	5	 }
		a. 选项	C
			i. new Runnable(MyRunnable).start()
			ii. new Thread(MyRunnable).run()
			iii. new Thread(new MyRunnable()).start()
			iv. new MyRunnable().start()
		b. 解析
			i. Java中线程实现有两种方式 
			1、实现Runnable接口，覆盖了run()方法，调用方法, new Thread(new A()).start()，调用线程。（如选项C） 
			2、继承Thread，并重写run()方法，调用方法，new A().start()   就调用了线程。（如选项D） ，但是该题是实现Runnable接口，故不对
			ii. 此题是通过实现Runnable接口，覆盖run()方法，调用方法来实现线程的创建和启动
			1、必须新建一个Thread类来启动线程，可排除A，D
			2、MyRunnable类必须实例化，也可排除A；
			3、start为线程启动函数，排除B；
			    所以正确答案为C 
			4、选项D是通过继承Thread才可以启动运行线程的，此题是通过实现Runnable接口方式，不合题意。
#### 9. 以下关于对象序列化描述正确的是
		a. 选项	CD
			i. 使用FileOutputStream可以将对象进行传输
			ii. 使用PrintWriter可以将对象进行传输
			iii. 使用transient修饰的变量不会被序列化
			iv. 对象序列化的所属类需要实现Serializable接口
		b. 解析
			i. 使用ObjectOutputStream和ObjectInputStream可以将对象进行传输.
			ii. 声明为static和transient类型的成员数据不能被串行化。因为static代表类的状态， transient代表对象的临时数据。
			![](https://s3.ax1x.com/2021/03/16/6y5Voj.jpg)
#### 10. A,B,C,D 中哪些是 setvar的重载？
	1	public class methodover
	2	{
	3	    public void setVar(int a, int b, float c) {}
	4	}
		a. 选项	ACD
			i. private void setVar(int a， float c， int b){}
			ii. protected void setVar(int a， int b， float c){}
			iii. public int setVar(int a， float c， int b){return a;}
			iv. public int setVar(int a， float c){return a;}
		b. 解析
			i. 重载是在同一个类中，有多个方法名相同，参数列表不同(参数个数不同，参数类型不同),与方法的返回值无关，与权限修饰符无关，B中的参数列表和题目的方法完全一样了。
#### 11. 下面有关 JAVA 异常类的描述,说法正确的有()
		a. 选项	ABC
			i. 异常的继承结构:基类为 Throwable,Error 和 Exception 。实现 Throwable, RuntimeException 和 IOException 等继承 Exception
			ii. 非 RuntimeException 一般是外部错误(不考虑Error的情况下),其可以在当前类被 try{}catch 语句块所捕获
			iii. Error 类体系描述了 Java 运行系统中的内部错误以及资源耗尽的情形,Error 不需要捕捉
			iv. RuntimeException 体系包括错误的类型转换、数组越界访问和试图访问空指针等等,必须 被 try{}catch 语句块所捕获
		b. 解析
			![](https://s3.ax1x.com/2021/03/16/6y5EwQ.jpg)
			ii. 都是Throwable的子类： 
			iii. 1.Exception（异常） :是程序本身可以处理的异常。 
			iv. 2.Error（错误）: 是程序无法处理的错误。这些错误表示故障发生于虚拟机自身、或者发生在虚拟机试图执行应用时，一般不需要程序处理。
			v. 3.检查异常（编译器要求必须处置的异常） ：  除了Error，RuntimeException及其子类以外，其他的Exception类及其子类都属于可查异常。这种异常的特点是Java编译器会检查它，也就是说，当程序中可能出现这类异常，要么用try-catch语句捕获它，要么用throws子句声明抛出它，否则编译不会通过。
			vi. 4.非检查异常(编译器不要求处置的异常): 包括运行时异常（RuntimeException与其子类）和错误（Error）。
#### 12. 关于依赖注入，下列选项中说法错误的是（）
		a. 选项	B

			i. 依赖注入能够独立开发各组件，然后根据组件间关系进行组装
			ii. 依赖注入使组件之间相互依赖，相互制约
			iii. 依赖注入提供使用接口编程
			iv. 依赖注入指对象在使用时动态注入
		b. 解析
			i. 依赖注入是为了降低代码之间的耦合度，而非相互依赖
#### 13. 基本的Java语言函数存储在以下哪个java包中？（） 
		a. 选项	A
			i. java.lang
			ii. java.io
			iii. java.net
			iv. java.util
		b. 解析
			i. java.lang包包含 
				1) 包装类 
				2) String 类 
				3) Math 类     ——    包含函数 
				4) Class 类 
				5) Object 类
#### 14. 以下代码段执行后的输出结果为
		a. 选项	D
	1	public class Test {
	2	public static void main(String args[]) {
	3	int x = -5;
	4	int y = -12;
	5	System.out.println(y % x);
	6	}
	7	}
			i. -1
			ii. 2
			iii. 1
			iv. -2
		a. 解析
			i. -5*2=-10	-12-（-10）=-2
		b. 扩展
			i. System.out.println((-3)%2);	-1
			System.out.println(4%3);	1
			System.out.println((-3)%(-2));	-1
			System.out.println(4%(-3));	1
#### 15. 下列循环语句序列执行完成后，i的值是（）
			i. int i;
			ii. for(i=2;i<=10;i++){
			iii. System.out.println(i);
			iv. }
		a. 选项	C
			i. 2
			ii. 10
			iii. 11
			iv. 不确定
		b. 解析
			i. for是这么执行的，第一次运行是给i赋初值为2，然后判断是否小于等于10，然后执行代码，再执行i++。第二次判断i++是否小于等于10，满足条件执行代码，再执行i++。如此反复，最后一次肯定是i=10,输出为10,然后执行i++,此时i=11,再判断11是否小于10，不满足，跳出循环。所以i的值为11.
#### 16. 以下程序段执行后将有（）个字节被写入到文件afile.txt中。
	1	try {
	2	    FileOutputStream fos = new FileOutputStream("afile.txt");
	3	    DataOutputStream dos = new DataOutputStream(fos);
	4	    dos.writeInt(3);
	5	    dos.writeChar(1);
	6	    dos.close();
	7	    fos.close();
	8	} catch (IOException e) {}
		a. 选项	C
			i. 3
			ii. 5
			iii. 6
			iv. 不确定，与软硬件环境相关
		b. 解析
			i. byte 1个字节 
			ii. short  2个字节 
			iii. int 4个字节 
			iv. long 8个字节 
			v. float 4个字节 
			vi. double 8个字节 
			vii. char 2个字节 
			viii. boolean 1个字节或4个字节，在java规范2中，如果boolean用于声明一个基本类型变量时占4个字节，如果声明一个数组类型的时候，那么数组中的每个元素占1个字节。
		c. 根据首字母来记byte(b)->boolean(b)->char(c)
#### 17. What will be printed when you execute the following code?
		class C {
		    C() {
		        System.out.print("C");
		    }
		}
		
		class A {
		    C c = new C();
		
		    A() {
		        this("A");
		        System.out.print("A");
		    }
		
		    A(String s) {
		        System.out.print(s);
		    }
		}
		
		class Test extends A {
		    Test() {
		        super("B");
		        System.out.print("B");
		    }
		
		    public static void main(String[] args) {
		        new Test();
		    }
		}
		a. 选项	B
			i. BB
			ii. CBB
			iii. BAB
			iv. None of the above
		b. 解析
			i. 1.类初始化阶段，先执行最顶层父类的静态初始化块，然后依次向下，直到执行当前类的静态初始化块
			ii. 2.对象初始化阶段，先执行最顶层父类的普通初始化块、最顶层父类的构造器 ，然后依次向下，直到执行当前类的初始化块。
			iii. 3.类初始化完成后，将会一直存在在虚拟机中，再次执行时无须再次进行类初始化。
			iv. 这道题： 
			v. 1.对象初始化阶段，执行父类普通成员变量和代码块，C c = new C()，这里输出C 
			vi. 2.然后因为子类调用的是带参数的构造方法，这里输出B 
			vii. 3.最后子类构造方法里输出B ，所以是CBB
#### 18. 在Java中，关于HashMap类的描述，以下正确的是 ()
		a. 选项	ACD
			i. HashMap使用键/值得形式保存数据
			ii. HashMap 能够保证其中元素的顺序
			iii. HashMap允许将null用作键
			iv. HashMap允许将null用作值
		b. 解析
			i. Map集合类	key	value
			HashMap	允许为null	允许为null
			TreeMap	不允许为null	允许为null
			ConcurrentMap	不允许为null	不允许为null
			HashTable	不允许为null	不允许为null
#### 19. jre 判断程序是否执行结束的标准是（） 
		a. 选项	A
			i. 所有的前台线程执行完毕
			ii. 所有的后台线程执行完毕
			iii. 所有的线程执行完毕
			iv. 和以上都无关
		b.   JX
			i.   main()函数即主函数，是一个前台线程，前台进程是程序中必须执行完成的，而后台线程则是java中所有前台结束后结束，不管有没有完成，后台线程主要用与内存分配等方面。                                                                                           
			ii. 前台线程和后台线程的区别和联系： 
			iii. 1、后台线程不会阻止进程的终止。属于某个进程的所有前台线程都终止后，该进程就会被终止。所有剩余的后台线程都会停止且不会完成。
			iv. 2、可以在任何时候将前台线程修改为后台线程，方式是设置Thread.IsBackground 属性。
			v. 3、不管是前台线程还是后台线程，如果线程内出现了异常，都会导致进程的终止。
			vi. 4、托管线程池中的线程都是后台线程，使用new Thread方式创建的线程默认都是前台线程。
#### 20. 下面哪些类可以被继承？ Java.lang.Thread、java.lang.Number、java.lang.Double、java.lang.Math、 java.lang.ClassLoader
		a. XX
			i. Thread
			ii. Number
			iii. Double
			iv. Math
			v. ClassLoader
		b. JX
			i. A，Thread可以被继承，用于创建新的线程 
			ii. B，Number类可以被继承，Integer，Float，Double等都继承自Number类 
			iii. C，Double类的声明为 
			iv. 复制代码
			v. 1	public final class Doubleextends Numberimplements Comparable<Double>
			vi.   final生明的类不能被继承
			vii. D，Math类的声明为 
			viii. 复制代码
			ix. 1	public final class Mathextends Object
			x.    不能被继承 
			xi. E，ClassLoader可以被继承，用户可以自定义类加载器
#### 21. Math.floor(-8.5)=( )
		a. 选项	D
			i. (float)-8.0
			ii. (long)-9
			iii. (long)-8
			iv. (double)-9.0
		b. 解析
			i. Math.floor()   表示向下取整，返回double类型   （floor---地板） 
			ii. Math.ceil()   表示向上取整，返回double类型    （ceil---天花板） 
			iii. Math.round()  四舍五入，返回int类型
#### 22. 有关hashMap跟hashTable的区别，说法正确的是？
		a. 选项	ABCD
			i. HashMap和Hashtable都实现了Map接口
			ii. HashMap是非synchronized，而Hashtable是synchronized
			iii. HashTable使用Enumeration，HashMap使用Iterator
			iv. HashMap允许将 null 作为一个 entry 的 key 或者 value，而 Hashtable 不允许。
		b. 解析
			HashTable和HashMap的区别
			1. 接口：HashTable和HashMap都是继承了Map接口
			2. 同步：HashTable是线程安全synchronized，HashMap非线程安全
			3. 哈希码：HashTable是直接使用元素的hashCode，HashMap需要重新计算
			4. 迭代器：HashTable使用的是Enumerator和Iterator，HashMap使用的是Iterator
			5. 空置：HashTable不接受空值或空键
			6. 扩容：HashTable初始值为11，每次扩容变成原来的两倍加一，HashMap初始值为16，每次扩容变成原来的两倍
#### 23. 以下关于final关键字说法错误的是（）
		a. 选项	AC
			i. final是java中的修饰符，可以修饰类、接口、抽象类、方法和属性
			ii. final修饰的类肯定不能被继承
			iii. final修饰的方法不能被重载
			iv. final修饰的变量不允许被再次赋值
		b. 解析
			1.final修饰变量，则等同于常量 
			2.final修饰方法中的参数，称为最终参数。 
			3.final修饰类，则类不能被继承 
			4.final修饰方法，则方法不能被重写。 
			5.final 不能修饰抽象类
			6.final修饰的方法可以被重载 但不能被重写
#### 24. 10. class Line {
	11. public class Point { public int x,y;}
	12. public Point getPoint() { return new Point(); }
	13. }
	14. class Triangle {
	15. public Triangle() {
	16. // insert code here
	17. }
	18. }
	在第16行插入哪段代码可以获得一个Point对象的坐标?(  )
		a. 选项	D
			i. Point p = Line.getPoint();
			ii. Line.Point p = Line.getPoint();
			iii. Point p = (new Line()).getPoint();
			iv. Line.Point p = (new Line()).getPoint();
			b. 解析
				![](https://s3.ax1x.com/2021/03/16/6y5KS0.jpg)
#### 25. 以下哪种JAVA的变量表达式使得变量a和变量b具有相同的内存引用地址(  )
		a. 选项	ABD
			i. String a = "hello"; String b = "hello";
			ii. Integer a; Integer b = a;
			iii. int a = 1; Integer b = new Integer(1);
			iv. int a = 1; Integer b = 1;
		b. 解析
			i. 首先结论：
				1) （1）int与Integer、new Integer()进行==比较时，结果永远为true
				2) （2）Integer与new Integer()进行==比较时，结果永远为false
				3) （3）Integer与Integer进行==比较时，看范围；在大于等于-128小于等于127的范围内为true，在此范围外为false。
			ii. D选项： int a =1;并不指向堆中，它只有值，没有引用地址，Integer b = 1， 即Integer b = new Integer(1);指向堆中地址为1的位置。
#### 26. 以下哪个方法用于定义线程的执行体？ （）
		a. 选项	C
			i. start()
			ii. join()
			iii. run()
			iv. synchronized()
		b. 解析
			i. start()方法是启动线程，启动线程后执行的run()方法
#### 27. 下面程序的输出是什么？
		package algorithms.com.guan.javajicu;
		public class TestDemo
		{
		    public static String output = ””;
		    public static void foo(inti)
		    {
		        try
		        {
		            if (i == 1)
		            {
		                throw new Exception();
		            }
		        }
		        catch (Exception e)
		        {
		            output += “2”;
		            return ;
		        } finally
		        {
		            output += “3”;
		        }
		        output += “4”;
		    }
		    public static void main(String[] args)
		    {
		        foo(0);
		        foo(1);
		        System.out.println(output);
		    }
		}
		a. 选项	B
			i. 342
			ii. 3423
			iii. 34234
			iv. 323
		b. 解析
			i. 首先是foo(0),在try代码块中未抛出异常，finally是无论是否抛出异常必定执行的语句， 
			ii. 所以 output += “3”;然后是 output += “4”; 
			iii. 执行foo(1)的时候，try代码块抛出异常，进入catch代码块，output += “2”; 
			iv. 前面说过finally是必执行的，即使return也会执行output += “3”
			v. 由于catch代码块中有return语句，最后一个output += “4”不会执行。
			vi. 所以结果是3423
#### 28. Choose the correct  ones from the following statements:
		a. 选项	AC
			i. A class can implement more than one interfaces
			ii. A class can extend more than one class
			iii. An interface has at least one method declared.
			iv. An abstract class which has no abstract methods declared is legal
		b. 解析
			i. 1、一个类可以有多个接口；
				2、一个类只能继承一个父类；
				3、接口中可以不声明任何方法，和成员变量
					interface testinterface{	
					}
				4、抽象类可以不包含抽象方法，但有抽象方法的类一定要声明为抽象类
					abstract class abstclass{
						abstract void meth();
					}
#### 29. 判断一块内存空间是否符合垃圾收集器收集的标准有哪些？
		a. 选项	ABD
			i. 给对象赋予了空值null,以下再没有调用过
			ii. 对象重新分配了内存空间
			iii. 给对象赋予了空值null
			iv. 给对象赋予了新值
		b. 解析
			i. 在java语言中，判断一块内存空间是否符合垃圾收集器收集标准的标准只有两个：
				1) 1.给对象赋值为null，以下没有调用过。
				2) 2.给对象赋了新的值，重新分配了内存空间。
#### 30. 以下代码执行的结果显示是多少（）？
![](https://s3.ax1x.com/2021/03/16/6y5eFs.jpg)
		a. 选项	B
			i. 505000
			ii. 0
			iii. 运行时错误
			iv. 5050
		b. 解析
			i. 考察count++与++count的区别！ 
				1) for循环外面count=0,循环里面的count=count++;(count的值都等于count值，而后面count自加不影响count结果，因此这个式子无意义);循环count都为0（因count++是先返回count的本身值再自加1的）！ 
				2) 若是改为count=++count;（先自加，再返回自加后的值），结果就是5050*101=510050了！
				3) 改为count++;结果就是5050*101=510050了！
			ii. count0=count1++的执行步骤： 
			tmp=count1； 
			count1++； 
			count0=tmp；
#### 31. 下面有关Java的说法正确的是（    ）
		a. 选项	 A C D F
			i. 一个类可以实现多个接口
			ii. 抽象类必须有抽象方法
			iii. protected成员在子类可见性可以修改
			iv. 通过super可以调用父类构造函数
			v. final的成员方法实现中只能读取类的成员变量
			vi. String是不可修改的，且java运行环境中对string对象有一个对象池保存
		b. 解析
			i. B:不必须有抽象方法，但是包含抽象方法的类一定是抽象类
			ii. C:父类中的protected方法子类在重写的时候访问权限可以修改，其实就是重写的要素之一，换了个说法而已
			iii. E:final 的成员方法除了能读取类的成员变量，还能读取类变量
#### 32. 对抽象类的描述正确的是()
		a. 选项	D
			i. 抽象类的方法都是抽象方法
			ii. 一个类可以继承多个抽象类
			iii. 抽象类不能有构造方法
			iv. 抽象类不能被实例化
		b. 解析
			i. A.抽象类可以有非抽象的方法，而接口中的方法都是抽象方法
			ii. B.java中类只能单继承，接口可以‘继承’多个接口
			iii. C.抽象类必须有构造方法，接口一定没有构造方法
			iv. D.实例化一般指new一个对象，所以抽象类不能实例化
#### 33. 关于抽象类和接口叙述正确的是？ ( )
		a. 选项	D
			i. 抽象类和接口都能实例化的
			ii. 抽象类不能实现接口
			iii. 抽象类方法的访问权限默认都是public
			iv. 接口方法的访问权限默认都是public
		b. 解析
			i. 抽象类
				1) 1.抽象类中可以构造方法 
				2) 2.抽象类中可以存在普通属性，方法，静态属性和方法。 
				3) 3.抽象类中可以存在抽象方法。 
				4) 4.如果一个类中有一个抽象方法，那么当前类一定是抽象类；抽象类中不一定有抽象方法。 
				5) 5.抽象类中的抽象方法，需要有子类实现，如果子类不实现，则子类也需要定义为抽象的。 
				6) 6,抽象类不能被实例化，抽象类和抽象方法必须被abstract修饰
			ii. 接口 
				1) 1.在接口中只有方法的声明，没有方法体。 
				2) 2.在接口中只有常量，因为定义的变量，在编译的时候都会默认加上public static final 
				3) 3.在接口中的方法，永远都被public来修饰。 
				4) 4.接口中没有构造方法，也不能实例化接口的对象。（所以接口不能继承类） 
				5) 5.接口可以实现多继承 
				6) 6.接口中定义的方法都需要有实现类来实现，如果实现类不能实现接口中的所有方法则实现类定义为抽象类。 
				7) 7，接口可以继承接口，用extends
#### 34. 指出下列程序运行的结果：
		public class Example{
		    String str=new String("tarena");
		    char[]ch={'a','b','c'};
		    public static void main(String args[]){
		        Example ex=new Example();
		        ex.change(ex.str,ex.ch);
		        System.out.print(ex.str+" and ");
		        System.out.print(ex.ch);
		    }
		    public void change(String str,char ch[]){
		   //引用类型变量，传递的是地址，属于引用传递。
		        str="test ok";
		        ch[0]='g';
		    }
		}
		a. 选项	
			i. tarena and abc
			ii. tarena and gbc
			iii. test ok and abc
			iv. test ok and gbc
		b. 解析
			i. string和char数组都是引用类型，引用类型是传地址的，会影响原变量的值
			ii. 但是string是特殊引用类型，string类型的值是不可变的，为了考虑一些内存，安全等综合原因，把它设置成不可变的; 不可变是怎么实现的？Java在内存中专门为string开辟了一个字符串常量池，用来锁定数据不被篡改，所以题目中函数中的str变量和原来的str已经不是一个东西了，它是一个局部引用，指向一个testok的字符串，随着函数结束，它也就什么都没了
			iii. 但是char数组是会改变原值的
#### 35. 在JAVA中，假设A有构造方法A(int a)，则在类A的其他构造方法中调用该构造方法和语句格式应该为（）
		a. 选项	B
			i. this.A(x)
			ii. this(x)
			iii. super(x)
			iv. A(x)
		b. 解析
			i. this的作用其中一个就是在一个构造方法中调用另一个构造方法，格式为this(参数)； 
			ii. super是调用父类的方法； 
			iii. A(a)这种形式是在new一个类时使用。
			iv. A.这是调用普通方法的写法
			v. C.这时显示调用父类构造方法
			vi. D.调用静态方法
#### 36. 下列哪项不属于jdk1.6垃圾收集器？
		a. 选项	D
			i. Serial收集器
			ii. parNew收集器
			iii. CMS收集器
			iv. G1收集器
		b. 解析
			![](https://s3.ax1x.com/2021/03/16/6y5mYn.jpg)
#### 37. 在开发中使用泛型取代非泛型的数据类型（比如用ArrayList<String>取代ArrayList），程序的运行时性能会变得更好。（） 
		a. 选项	B
			i. 正确
			ii. 错误
		b. 解析
			i. 使用泛型的好处
				1) 类型安全。 泛型的主要目标是提高 Java 程序的类型安全。通过知道使用泛型定义的变量的类型限制，编译器可以在一个高得多的程度上验证类型假设。没有泛型，这些假设就只存在于程序员的头脑中（或者如果幸运的话，还存在于代码注释中）
				2) 消除强制类型转换。 泛型的一个附带好处是，消除源代码中的许多强制类型转换。这使得代码更加可读，并且减少了出错机会
				3) 潜在的性能收益。 泛型为较大的优化带来可能。在泛型的初始实现中，编译器将强制类型转换（没有泛型的话，程序员会指定这些强制类型转换）插入生成的字节码中。但是更多类型信息可用于编译器这一事实，为未来版本的 JVM 的优化带来可能。由于泛型的实现方式，支持泛型（几乎）不需要 JVM 或类文件更改。所有工作都在编译器中完成，编译器生成类似于没有泛型（和强制类型转换）时所写的代码，只是更能确保类型安全而已。 
			ii. 所以泛型只是提高了数据传输安全性，并没有改变程序运行的性能
#### 38. 以下代码段执行后的输出结果为
		public class Test {
		public static void main(String args[]) {
		int i = -5;
		i =  ++(i++);
		System.out.println(i);
		}
		}
		a. 选项	C
			i. -7
			ii. -3
			iii. 编译错误
			iv. -5
		b. 解析
			i. ++（  ）  括号里面必须是一个变量，而 i ++  是一个字面量。，此时为-4，常量
#### 39. 下面哪个流类不属于面向字符的流（）
		a. 选项	BC
			i. BufferedWriter
			ii. FileInputStream
			iii. ObjectInputStream
			iv. InputStreamReader
		b. 解析
			![](https://s3.ax1x.com/2021/03/16/6y5tYR.jpg)
			ii. 既然是字符流，那么一般是reader和writer结尾，那么就选BC了
#### 40. public class IfTest{
	    public static void main(string[]args){
	        int x=3;
	        int y=1;
	        if(x=y)
	            System.out.println(“Not equal”);
	        else
	            System.out.println(“Equal”);
	     }
	}
	What is the result?
		a. 选项	C
			i. The output is “Equal”
			ii. The output in “Not Equal”
			iii. An error at line 5 causes compilation to fall.
			iv. The program executes but does not print a message.
		b. 解析
			i. if()语句括号中为比较表达式，返回值要么是true，要么是false，if(x=y)是将y赋值给x，但是数据类型是int类型的，编译不能通过，如果把代码改为这样： 
			ii. boolean x = false; 
			iii. boolean y = ture; 
			iv. if(x=y){...}这样就就不会报错了，编译正常通过。
#### 41. 以下程序的输出结果是
		public class Print{
			static boolean out(char c){
				System.out.println(c);
				return true;
			}
			public static void main(String[] argv){
				int i = 0;
				for(out('A');out('B') && (i<2);out('C')){
					i++;
					out('D');
				}
			}
		}
		a. 选项	A
			i. ABDCBDCB
			ii. BCDABCD
			iii. 编译错误
			iv. 运行错误
		b. 解析
			i. for循环的执行顺序用如下表达式： 
			for(expression1;expression2;expression3){ 
			expression4; 
			} 
			执行的顺序应该是： 
			1）第一次循环，即初始化循环。 
			首先执行表达式expression1（一般为初始化语句）；再执行expression2（一般为条件判断语句），判断expression1是否符合expression2的条件；如果符合，则执行expression4，否则，停止执行；最后执行expression3。 
			2）第N（N>=2）次循环 
			首先执行expression2，判断在expression3是否符合在expression2要求；如果符合，则继续执行在expression4，否则，停止执行。最后执行在expression3。如此往复，直至expression3不满足在expression2条件是为止。 
			ii. for循环执行开始 
			首先执行out('A') 输出A； 
			然后执行out('B')&&(i<2)此时输出B，i=0，判断条件为真，执行for循环的循环体； 
			执行i++，out('D')，输出D i=1； 
			执行out('C'),输出C  
			然后执行out('B')&&(i<2) 此时输出B，i=1 判断条件为真 ，执行for循环的循环体；
			执行i++，out('D')，输出D i=2； 
			执行out('C'),输出C  
			然后执行out('B')&&(i<2) 此时输出B，i=2，不满足i<2  判断条件为假 ，跳出循环；
			所以结果为ABDCBDCB
#### 42. 以下程序会输出什么
		        int a =100,b=50,c=a---b,d=a---b;
		        System.out.println(a);
		        System.out.println(b);
		        System.out.println(c);
		        System.out.println(d);
		a. 选项	C
			i. 100 48 48 49
			ii. 100 49 48 52
			iii. 98 50 50 49
			iv. 98 50 50 48
		b. 解析
			i. 先考虑a--，a执行后自减操作，即先用a后再自减1，与--a先反
			ii. （1）c=a---b，先执行a-b操作，得到c=50，再执行a减1操作，得到a=99
			iii. （2）d=a---b，先执行a-b操作，得到d=49，再执行a减1操作，得到a=98
#### 43. A,B,C,D 中哪些是 setvar的重载？
		public class methodover
		{
		    public void setVar(int a, int b, float c) {}
		}
		a. 选项	ACD
			i. private void setVar(int a， float c， int b){}
			ii. protected void setVar(int a， int b， float c){}
			iii. public int setVar(int a， float c， int b){return a;}
			iv. public int setVar(int a， float c){return a;}
		b. 解析
			i. 方法的重载是指： 
				1) 在同一个类中 
				2) 方法名相同 
				3) 方法的形参列表不同 
			ii. 具体的不同表现为：
				1) 类型、个数、顺序的不同才可以构成重载
			iii. 比较容易忽略的一点 
				1) 与方法的返回值类型与访问权限无关
		c. 疑问
			i. 参数类型不同构成重载；
				1) 返回相同，参数类型相同，参数顺序不同，例如：
					a) int fun( int x, int y )
					b) int fun( int y, int x )
			ii. 这样不是重载，因为编译器无法区别它们，从而报错。
				1) int fun( int x, char y )
				2) int fun( char y, int x ) 
				3) 是重载的
			iii. 参考：https://www.nowcoder.com/test/question/done?tid=39706160&qid=15389#summary
#### 44. 有关会话跟踪技术描述正确的是（）
		a. 选项	ABC
			i. Cookie是Web服务器发送给客户端的一小段信息，客户端请求时，可以读取该信息发送到服务器端
			ii. 关闭浏览器意味着临时会话ID丢失，但所有与原会话关联的会话数据仍保留在服务器上，直至会话过期
			iii. 在禁用Cookie时可以使用URL重写技术跟踪会话
			iv. 隐藏表单域将字段添加到HTML表单并在客户端浏览器中显示
		b. 解析
			i. 隐藏域在页面中对于用户（浏览器）是不可见的，在表单中插入隐藏域的目的在于收集或发送信息，以利于被处理表单的程序所使用。浏览者单击发送按钮发送表单的时候，隐藏域的信息也被一起发送到服务器
#### 45. 以下关于链表和数组说法正确的是（）
		a. 选项	ABC
			i. 数组从栈中分配空间，链表从堆中分配空间
			ii. 数组插入或删除元素的时间复杂度O(n)，链表的时间复杂度O(1)
			iii. 数组利用下标定位，时间复杂度为O(1)，链表定位元素时间复杂度O(n）
			iv. 对于add和remove，ArrayList要比LinkedList快
		b. 解析
			i. 数组元素在栈区，链表元素在堆区；
#### 46. 下面程序的输出是:()
	String x="fmn";
	x.toUpperCase();
	String y=x.replace('f','F');
	y=y+"wxy";
	System.out.println(y);
		a. 选项	D
			i. FmNwxy
			ii. fmnwxy
			iii. wxyfmn
			iv. Fmnwxy
		b. 解析
			i. 本题主要考察String对象的不可变性。
				1) toUpperCase()会对当前对象进行检查 如果不需要转换直接返回当前对象，否则new一个新对象返回；
				2) replace()如果两个参数相同，则直接返回，否则new一个新对象，所以这里y指向"Fmn";
				3) y=y+"wxy" 这里修改y所指向的字符串对象，让它由指向"Fmn"变成指向"Fmnxyz".
			ii. 详解
				1) String x="fmn";  “fmn”是在常量池里的不可变对象。
				2) x.toUpperCase();   在堆中new一个"FMN"对象，但无任何引用指向它。
				3) String y=x.replace('f','F'); 在堆中 new一个"Fmn"对象，y指向它。
				4) y=y+"wxy"; 在堆中 重新new一个"Fmnwxy"对象， 修改y指向，现在y指向它。
#### 47. 类方法中可以直接调用对象变量
		a. 选项	B
			i. 正确
			ii. 错误
		b. 解析
			i. 类方法（也就是静态方法）
			ii. 静态方法中不能调用对象的变量，因为静态方法在类加载时就初始化，对象变量需要在新建对象后才能使用
#### 48. String s = new String("xyz");创建了几个StringObject？
		a. 选项	A
			i. 两个或一个都有可能
			ii. 两个
			iii. 一个
			iv. 三个
		b. 解析
			i. String对象的两种创建方式:
				1) 第一种方式: String str1 = "aaa"; 是在常量池中获取对象("aaa" 属于字符串字面量，因此编译时期会在常量池中创建一个字符串对象)，
				2) 第二种方式: String str2 = new String("aaa") ; 一共会创建两个字符串对象一个在堆中，一个在常量池中（前提是常量池中还没有 "aaa" 字符串对象）
			ii. 如果在常量池中已经存在“xyz”，那么不会继续创建，只创建一个new String("xyz")的对象。如果常量池中没有，则会创建两个对象，一个是对象的值“xyz”，一个是new String("xyz")的对象。
#### 49. 下面叙述那个是正确的？（）
		a. 选项	B
			i. java中的集合类（如Vector）可以用来存储任何类型的对象，且大小可以自动调整。但需要事先知道所存储对象的类型，才能正常使用。
			ii. 在java中，我们可以用违例（Exception）来抛出一些并非错误的消息，但这样比直接从函数返回一个结果要更大的系统开销。
			iii. java接口包含函数声明和变量声明。
			iv. java中，子类不可以访问父类的私有成员和受保护的成员。
		b. 解析
			i. A.vector是线程安全的ArrayList，在内存中占用连续的空间。初始时有一个初始大小，当数据条数大于这个初始大小后会重写分配一个更大的连续空间。如果Vector定义为保存Object则可以存放任意类型。
			ii. B.try{}catch{}会增加额外的开销
			iii. C.接口中声明的'变量'必须为public final static,所以为常量
			iv. D.子类可以访问父类受保护的成员
#### 50. 下列代码执行结果为（）
	public static void main(String args[])throws InterruptedException{
		    	Thread t=new Thread(new Runnable() {
					public void run() {
						try {
							Thread.sleep(2000);
						} catch (InterruptedException e) {
							throw new RuntimeException(e);
						}
						System.out.print("2");
					}
				});
		    	t.start();
		    	
		    	t.join();
		    	System.out.print("1");
		    }
		a. 选项	A
			i. 21
			ii. 12
			iii. 可能为12，也可能为21
			iv. 以上答案都不对
		b. 解析
			i. join()的作用是：“等待该线程终止”，这里需要理解的就是该线程是指的主线程等待子线程的终止。也就是在子线程调用了join()方法后面的代码，只有等到子线程结束了才能执行。
			ii. 因为子线程的休眠时间太长，因此主线程很有可能在子线程之前结束也就是输出结果是12，但是子线程用了join函数，因此主线程必须等待子线程执行完毕才结束因此输出结果只能是21
#### 51. 关于Java和C/C++的比较，下列哪个描述是错误的？
		a. 选项	CD
			i. Java不支持指针，C/C++支持
			ii. Java程序不需要显式地关心内存释放，而C/C++需要
			iii. Java和C++一样，是纯编译型语言，因此它们的class都是在编译时静态联编(static binding)的
			iv. Java数组、字符串不可能溢出，C/C++数组、字符串则有可能溢出边界
		b. 解析
			i. Java和C++的区别：
				1) 1. Java是解释型语言，所谓的解释型语言，就是源码会先经过一次编译，成为中间码，中间码再被解释器解释成机器码。对于Java而言，中间码就是字节码(.class)，而解释器在JVM中内置了。
				2) 2. C++是编译型语言，所谓编译型语言，就是源码一次编译，直接在编译的过程中链接了，形成了机器码。
				3) 3. C++比Java执行速度快，但是Java可以利用JVM跨平台。
				4) 4. Java是纯面向对象的语言，所有代码（包括函数、变量）都必须在类中定义。而C++中还有面向过程的东西，比如是全局变量和全局函数。
				5) 5. C++中有指针，Java中没有，但是有引用。
				6) 6. C++支持多继承，Java中类都是单继承的。但是继承都有传递性，同时Java中的接口是多继承，类对接口的实现也是多实现。
				7) 7. C++中，开发需要自己去管理内存，但是Java中JVM有自己的GC机制，虽然有自己的GC机制，但是也会出现OOM和内存泄漏的问题。C++中有析构函数，Java中Object的finalize方法
				8) 8. C++运算符可以重载，但是Java中不可以。同时C++中支持强制自动转型，Java中不行，会出现ClassCastException（类型不匹配）。
