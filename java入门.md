# java入门

## java基础

### 1.编译和运行

编写：编写的代码保存在.java文件中

编译：使用javac.exe命令编译我们的java源文件，格式：javac 源文件名.java

运行：使用java.exe命令解释运行我们的字节码文件，格式：java 类名 

### 2.

在一个java源文件中可以声明多个class，但是只能最多有一个类声明为public的，而且声明为public的类的类名必须和源文件名相同。

### 3.程序入口是main()方法，格式是固定的

```java
class HelloJava{
	public static void main(String[] args){
		System.out.println("hello world");	
	}
}
class Person{

}
```

### 4.输出数据：

```java
System.out.println("hello world");//换行System.out.print("hello world");//不换行
```

### 5.编译的过程

编译以后会生成一个或多个字节码文件，字节码文件名与源文件中的类名相同。

### 6.jdk

JDK=JRE+JAVA的开发工具（javac.exe,java.exe,javadoc.exe）

JRE=JVM+Java核心类库

### 7.配置环境变量？

记住程序的路径，方便在命令行窗口的任意目录驱动程序，是为了在任何目录下都可以运行java程序

如何配置：

```java
JAVA_HOME=bin的上一层目录

path=%JAVA_HOME%\bin
```

### 8 idea项目结构

project->module->package->class

```java
//格式化代码快捷键ctrl+alt+L
//复制当前行数据到下一行ctrl+D
//快速键入相关代码main/psvm,sout
```

### 9字面量

字符：'a'   必须单引号，有且只有一个字符

字符串："三生三世十里桃花"  必须双引号

### 10 数据类型

#### 引用数据类型：String

#### 基本数据类型：4类八种

整数：byte 1字节 ；short 2字节；int 4字节(10位数)【默认】； long 8字节(19位数)

浮点数：float 4字节；double 8字节【默认】（特殊计数法比long表示的还多1.70*10的308次方）

字符：char 2字节

布尔：boolean 1字节

**注意：**

**long lg2=12222212121212121，会报错，因为默认的整数字面量是int，这里长度超过了int类型，但没超过long类型，需要在后面加L/l：long lg2=12222212121212121L**

**float score=98.5，会报错，因为默认的浮点数字面量是double，需要在后面加F/f：float score=98.5F**,表示字面量98.5是float类型

类名大驼峰让，首字母大写

标识符小驼峰，首字母小写

### 11自动类型转换

##### 1强制类型转换：强制将范围大的变量，数据赋值给类型范围小的变量。

short a=(short)b

强制类型转换可能出现数据丢失

小数强制转换成整数是直接截断小数保留整数。

##### 2表达式类型转换

```
//        注意在表达式中小范围的类型会自动转换为大范围的类型运算
//        最终类型由表达式中的最高类型决定。
//        表达式中byte，short，char是直接转换成int类型参与运算的
```

##### 3自动类型转换

类型范围小的变量可以直接赋值给类型范围大的变量

### 12赋值运算符

扩展运算符包含了强制类型转换

```java
byte i=10;
byte j=20;
i+=j;
//等价于
i=(byte)(i+j);
//i=i+j;//会报错，运算时默认int，表达式中byte，short，char是直接转换成int类型参与运算的
```

### 13逻辑运算符

逻辑与&，逻辑或|：无论是左边false还是true，右边都会执行

短路与&&，短路或||：判断结果与&，|一样，过程是&&左边为false，右边则不执行，||左边为true，右边则不执行

实际开发常用的还是&&，||，!(非)

&&优先级高于||

&优先级高于|

### 14分支

###### switch：

switch分支表达式类型只支持byte，short，int，char，JDK5开始支持枚举，JDK7开始支持String，不支持double、float、long

case给出的值不允许重复，且只能是字面量。不能是变量。

不要忘记break，否则会出现穿透现象。

穿透也不是坏事，可以简洁冗余代码

### 15循环

break：只能用于结束所在循环，或者结束所在switch分支的执行

continue：跳出当前循环的当次执行，进入下一次循环。（）只能在循环中使用

### 16数组

用来存储一批同种类型数据的内存区域（可以理解为容器）

#### 动态初始化数组：

定义数组的时候只确定元素的**类型**和数组的**长度**，之后再存入具体数据。

```java
		//动态初始化定义数组,先定义后赋值，double默认值{0.0,0.0,0.0}
        double[] myage=new double[3];//默认值{0.0,0.0,0.0}
        System.out.println(myage[0]);//0.0
        myage[0]=10.0;
        System.out.println(myage[0]);//10.0

        //动态初始化定义数组,先定义后赋值，string默认值{null,null,null}
        String[] myname=new String[3];//默认值{null,null,null}
        System.out.println(myname[0]);//null
        myname[0]="方前林";
        System.out.println(myname[0]);//方前林
```

##### 动态初始化数组的元素默认值：

byte short int long char默认值为0（注意char是编码为0的字符，但是没有编码0的）；

float double默认值0.0；

boolean默认是false；

类 接口 数组 string默认值null；

```Java
        char[] mychar=new char[3];
        System.out.println(mychar[0]);// 编码0，
        System.out.println((int)mychar[0]);// 0		
```



#### 静态初始化数组：

定义时直接给数组赋值

```java
		//数组 引用类型
        //静态初始化方式定义数组:
        String[] names=new String[]{"方前林","方菊"};
        double[] score=new double[]{111,222};
        //简化写法
        String[] names2={"方前林","方菊"};
        double[] score2={111,222};
        System.out.println(names[0]);
        System.out.println(score[0]);
        //数组变量名中存储的是数组在内存中的地址，数组是引用类型
        System.out.println(names);
        System.out.println(score);//[D@7ef20235 代表数组，double,内存中的地址
```

##### **数组的访问**：数组名[索引]，

##### **数组长度**：数组名.length

```java
		System.out.println(names[0]);
        System.out.println(score[0]);
        System.out.println(names.length);
        System.out.println(score.length);
```

##### **数组的注意事项**

​	**定义数组：**int[] age={1,2,3};等同于int age[]={1,2,3};

```java
		double[] score2={111,222};//主要还是用这种
        double score3[]={111,222};
```

​	**什么类型的数组就要放什么类型的数据，否则报错**

```Java
		String[] names2={"方前林","方菊",111};//报错
```

​	**数组一旦定义，程序执行中，长度和类型就固定了**

```
		double score3[]={111,222};
        System.out.println(score3[3]);//Index 3 out of bounds for length 2
```

##### 动态静态定义不能混用：都是单独的形式

```
int[] myname=new int[3]{1,2,3};//报错
```

### 17冒泡排序

```java
package com.xfzy.array;

public class MaoPao {
    public static void main(String[] args) {
        int[] myarray=new int[]{12,43,23,54,1};
        //冒泡排序第一轮是控制循环比较的轮数（数组长度-1）
        for(int i=0;i<myarray.length-1;i++){
            //第二轮才是比较元素大小，排序（数组长度-i-1）
            for(int j=0;j<myarray.length-i-1;j++){
                if(myarray[j]>myarray[j+1]){
                    int temp=myarray[j];
                    myarray[j]=myarray[j+1];
                    myarray[j+1]=temp;
                }
            }
        }
        for(int i=0;i<myarray.length;i++){
            System.out.println(myarray[i]);
        }
    }
}
```

### 18Java内存分配

方法区：放Class文件的

栈内存：运行方法，main方法，定义的变量

堆内存：new出来的对象，都在堆内存中

将class文件加载到方法区

栈内存中执行main方法

new出来的在堆内存中开辟新地址，数组变量存的是地址。

### 19方法

方法定义完整格式：

修饰符 返回值类型 方法名(形参列表){

​	方法体

​	return 返回值

}

```java
package com.xfzy.method;

public class MethodDemo
{
    public static void main(String[] args) {
        int rs=add(10,20);
        System.out.println(rs);
    }
    public static  int add(int a,int b){
        int c=a+b;
        return c;
    }
}
```

方法申明了具体的返回值，内部必须用return返回对应类型的数据。如果不需要返回结果，申明类型为void

形参列表可以有多个，甚至可以没有；如果有多个形参，必须用“，”隔开，且不能给初始化值

#### 方法注意事项

方法编写顺序无所谓

方法与方法是平级关系，**不能嵌套**定义。

方法声明有返回值必须return，没有不能return

return后面不能写代码，永远不可达。

方法要调用才能执行，调用时必须严格匹配参数情况。

有返回值的方法调用时可以选择定义变量接受结果，或者直接输出，甚至直接调用。没有返回值的方法只能直接调用。

### 20方法的参数传递机制

基本类型的参数传递：按值传递，改动形参不影响原值

引用类型的参数传递：也是按值传递，但是传递的是一个地址，改动引用类型形参也改到了原值

### 21方法重载

同一个类中，出现多个方法名称相同，但是形参列表不同，那么这些方法就是方法重载。

**好处：**对于相似功能的业务场景：可读性好，方法名相同提示是同一类型的功能，通过参数实现差异化

，是一种专业的代码设计。

**方法重载的识别技巧：**只要是同一个类，方法名称相同，形参列表不同，那他们就是重载的方法！（修饰符返回值类型都无所谓！）

**形参列表不同是指：形参的个数、类型、顺序不同，不关心形参的名称**

### 22面向对象

拿东西过来编程解决问题。万物皆对象。

**类：**相同事物共同特征的描述。

**对象：**对象是类的具体的实例——对象==实例

java中必须先定义类，才能得到对象。

**定义类的格式：**

```java
public class 类名(){

	//1.成员变量

	//2.成员方法

	//3.构造器

	//4.代码块

	//5.内部类
}
```

**定义类建议：**类名首字母建议大写、英文、有意义，满足驼峰模式，不能用关键字，满足标识符规定。

一个代码文件中可以有多个类。但是**只能一个类是public修饰的，public修饰的类名必须是Java代码的文件名称**。

**成员变量的格式：**

修饰符 数据类型 变量名称 = 初始化值

一般无需为成员变量赋初始值。存在默认值**0，0.0，false，null**

**内存机制：**

栈内存存储类的地址，只想堆内存，堆内存存储属性，还存储类的方法，但是为了节省空间，只存储了方法的地址，指向方法区。

**垃圾回收：**

当内存中的对象，没有被任何变量引用（指向时），就会被判定为内存中的垃圾，自动垃圾回收机制。

### 23构造器

**构造器作用**：定义在类中的，可以用于初始化一个类的对象，并返回对象的地址。

```java
Car c=new Car();
```

构造器格式

```
修饰符 类名 （形参列表）{
	...
}
```

```java
public class Car{
	//无参数构造器:默认存在的：初始化对象时，成员变量的数据均采用默认值。
	public Car(){
	
	}
	//有参数的构造器：在初始化对象时，同时可以接收参数为对象进行赋值
	public Car(String n,double p){

	}
}
```

调用构造器得到对象的格式：

```java
Car c=new Car();
Car c1=new Car("奔驰",39.8);
```

**注意**：

1任何类定义出来，默认就自带了无参数构造器，写不写都有

2.**一旦定义了有参数构造器，无参数构造器就没有了，如果还想用无参数构造器，只有自己重新手写一个无参数构造器了**。

### 24this关键字

**可以出现在构造器、方法中，代表当前对象的地址，（当前new出来的对象）**

**可以在构造器中，成员方法中用于指定当前对象的成员。**

```Java
package com.xfzy.thethis;

public class Car {
    String name;
    double price;
//    无参数构造器
    public Car(){
        System.out.println("无参数构造器里的this"+this);
    }
    public Car(String name,double price){
        System.out.println("有参数构造器里的this"+this);//@27d6c5e0s
    }
    public void run(){
        System.out.println("方法里的this"+this);//@27d6c5e0
    }
}


package com.xfzy.thethis;

public class Test {
    public static void main(String[] args) {
//        Car car1=new Car();
        Car car2=new Car("奔驰",20.9);
        car2.run();
        System.out.println("new出来的对象地址"+car2);//@27d6c5e0
    }
}

//有参数构造器里的thiscom.xfzy.thethis.Car@27d6c5e0
//方法里的thiscom.xfzy.thethis.Car@27d6c5e0
//new出来的对象地址com.xfzy.thethis.Car@27d6c5e0
```

**this出现在构造器中可以区分访问的是当前对象的变量**

```Java
package com.xfzy.thethis;

public class Car {
    String name;
    double price;
//    无参数构造器
    public Car(){
    }
    public Car(String name,double price){
        this.name=name;
        this.price=price;//防止形参name，price循环赋值，赋值不到当前对象上去
    }
    public void run(){
       
    }
}

```

**this出现在成员方法中以区分访问的是当前对象的变量还是传进来的局部变量**

```java
package com.xfzy.thethis;

public class Car {
    String name;
    double price;

    public Car(String name,double price){
        this.name=name;
        this.price=price;
    }
    public void goWith(String name){
        System.out.println(name+"正在和"+this.name+"一起跑");//区分当前对象的name和传进来的name
    }
}

```

### 25封装

面向对象三大特征：封装、继承、多态

封装告诉我们如何正确设计对象的属性和方法。

**封装的原则：对象代表什么，就得封装对应的数据，并提供数据对应的行为。**

**比如：**人画圆:画圆是圆的方法，是人调用的；张三杀死了李四，死是李四的方法，是张三调用的李四的死亡方法。

好处：有什么事，找对象，调方法。编程更简单。



**如何封装更好：**

一般建议**对成员变量使用private（私有隐藏）关键字**修饰（private修饰的成员代表只能在当前类中访问）

为每个成员变量提供配套的getter，setter方法暴露其取值和赋值。这样更安全和优雅。

```Java
package com.xfzy.encapsulation;

public class Student {
    private int age;
    public void setAge(int age){
        if(age>=0&&age<150){
            this.age=age;
        }else{
            System.out.println("您的年龄数据有问题");
        }
    }
    public int getAge(){
        if(this.age>=0){
            return this.age;
        }else{
            System.out.println("您的年龄数据有问题");
            return -1;
        }
    }
}
```

### 26JavaBean

**JavaBean也可称为实体类，其对象可以用于在程序中封装数据。**

标准JavaBean必须满足**以下要求**：

**成员变量使用private修饰。**

**提供成员变量对应的setXxx()，getXxx()方法。**

**必须提供一个无参构造器；有参数构造器是可写可不写的。**



ieda邮件可直接生成构造器以及getter，setter

```Java
package com.xfzy.javabean;

public class User {
    //1成员变量必须私有
    private String name;
    private double salary;
    //2必须含有无参构造器，有参构造器可有可无

    public User() {
    }

    public User(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }

    //3必须提供成套的getter，setter
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
}

```

### 27 成员变量、局部变量

区               别      成员变量                                                             局部变量

类中位置不同     类中、方法外                                                      常见于方法中

初始化值不同     有默认值（0，0.0，none），无需初始化      没有默认值，使用之前先赋值

内存位置不同     堆内存（类中）                                                  栈内存

生命周期不同     随着对象的创建和消失                                       随着方法的调用和方法运行结束

作 用 域 不 同     难界定                                                                  在所属的大括号中

### 28 String类

String是字符串类型，可以定义字符串变量指向字符串对象。（以""方式给出的字符串对象，**在字符串常量池中存储（堆内存里）**，而且字符串常量池相同内容只会存储一份，判断相等true。而运算出来的字符串存在堆里，他们的地址不一样，不是同一个，判断相等false）

**不可变字符串**：String变量每次的修改其实都**是产生并指向了新的字符串对象**！**原来的字符串对象都是没有改变的**，所以称不可变字符串。

String类创建字符串对象的两种方式：

1.直接用""定义

```java
String name="我爱你中国";
```

2.构造器定义（多种）

```java
String s1=new String();//""

String s2=new String("我爱你");//我爱你

char[] a={'a','b','中','国'}
String s3=new String(a);//ab中国

byte[] b={97,98,99}
String s4=new String(b);//abc
```

注意：通过构造器创建出来的字符串地址不相同（堆内存），通过""创建的地址相同（字符串常量池）

**注意：**

```java
//name1==name2
String name1="abc";
String name2="a"+"b"+"c";//a,b,c都已知，编译的时候直接编译成abc，他俩是同一个
```

```java
//name1！=name3
String name1="abc";
String name2="ab";
String name3=name2+"c";//name2是变量，运行的时候才知道这个具体值
```

#### String常用API

**字符串比较**：（==会比较地址不一样，基本数据类型比较适合用==）

equals()只比较字符串内容。

equalsIgnoreCase()只比较字符串内容且忽略大小写。

length()长度

charAt()获取某个索引位置处的字符

toCharArray()将当前字符串转换成字符数组返回

substring()根据开始和结束位置进行截取。

replace()使用新值，将字符串中的旧值替换，得到新的字符串（替换所有敏感词为***）

contains()判断字符串中是否包含某字符串

startsWith()判断字符串是否以某字符串开始

split()根据传入的字符切割字符串，得到字符串数组返回

### 29集合

集合与数组类似，也是一种容器，用于装数据的。

**数组：**定义完成后，类型确定、长度固定。

在个数不确定，且要进行增删数据操作的时候，数组是不太合适的

**集合**： **集合的大小不固定**，启动后可以动态变化，**类型也可以选择不固定**；

​			集合非常适合做元素个数不确定，且要进行增删操作的业务场景。

​			集合提供了许多丰富、好用的功能，而数组功能单一。

### 30ArrayList集合

#### arraylist

是集合的一种，它支持索引。

ArrayList集合的对象获取：public ArrayList() 构造器，创建一个空的集合对象

```java
ArrayList list=new ArrayList();
list.add("java");
list.add("hei");
list.add(1,"fql");//插入
```

**注意：集合中存储的元素并不是对象本身，而是对象的地址（虽然直接打印出来不是地址而是值！）**

#### 泛型

java强类型，不希望集合中各种类型都有，所以添加一个约束，用泛型

**Arraylist<E>:其实就是一个泛型类，可以在编译阶段约束集合对象只能操作某种数据类型**

Arraylist<String>:此集合只能支持操作字符串类型的元素

Arraylist<Integer>:此集合只能操作整型的元素

注意：集合中只能存储引用类型，不支持基本数据类型。int不行，integer可以

**集合和泛型都不支持基本数据类型，只能支持引用数据类型。**

```java
package com.xfzy.arraylist;

import java.util.ArrayList;

public class ArrayListDemo1 {
    public static void main(String[] args) {
        ArrayList<String> list=new ArrayList<>();//后面的可以不写String
        list.add("fangqan");
//        list.add(1);//报错！
        System.out.println(list);//[fangqan]

        ArrayList<Integer> integer=new ArrayList<>();
        integer.add(1);
        System.out.println(integer);//[1]
    }
}
```

**如果想使用全部类型，也最好使用泛型来写**

```java
public class ArrayListDemo1 {
    public static void main(String[] args) {		
		ArrayList<Object> list3=new ArrayList<>();
        list3.add(1);
        list3.add("dddd");
        System.out.println(list3);//[1, dddd]
    }
}
```

#### ArrayList集合常用方法

get()返回指定索引的元素

size()返回集合中的元素的个数

remove(int index)删除指定索引处的元素，返回被删除的元素

remove(Object o)删除指定的元素，返回删除是否成功，只会删除**第一次**出现的元素！

set()修改指定索引的元素，返回被修改的元素（修改前的值）

**注意：从集合中遍历删除元素要倒叙遍历，可以避免漏掉元素**

## Java加强

### 01static

static**是静态**的意思，可以**修饰成员变量和成员方法**。

#### 静态成员变量

static修饰成员变量表示该成员变量**只在内存中只存储一份**，可以被共享修改和访问。**存在堆内存的类的静态变量区**

**静态成员变量**（有static修饰，属于类，内存中加载一次）：常表示如在线人数信息等需要被共享的信息，可以被共享访问。

访问：**类名.静态成员变量（推荐），不推荐使用对象来访问**，同一个类中可以省略类名

**实例成员变量：**无static修饰，属于对象，只能通过对象名来访问。

```Java
package com.xfzy.d1_static;

public class StaticFieldDemo1 {
    public static void main(String[] args) {
        System.out.println(User.onlineNumber);//通过类名访问
        User u=new User();
        u.onlineNumber++;
        System.out.println(u.onlineNumber);//也可以通过对象访问到，但不推荐！
    }
}
```

```Java
package com.xfzy.d1_static;

public class User{
    public static int onlineNumber=190;
}
```

#### 静态成员方法

静态成员方法（有static修饰，属于类），建议用类名访问，虽然也可以用对象访问到。

实例成员方法（无static修饰，属于实例），只能用对象触发访问。

使用场景：表示**对象自己的行为**的，且方法中**需要访问实例成员**的，则该方法必须**声明为实例方法**。

如果该方法是以**执行一个共用功能为目的**，则可以**申明成静态方法**。

**内存原理：**方法区中首先加载出静态方法main,以及其他静态方法。栈内存中运行main方法。栈内可以直接访问到已加载出来的静态方法。可直接使用类名或者方法名（同一个类中）调用。栈中new新对象之后，在堆内开辟内存，存储变量和方法的引用，指向方法区中同时加载出来的实例方法

```java
package com.xfzy.d1_static;

public class Student {
    //实例成员变量
    private String name;

    public Student(String name) {
        this.name = name;
    }

    //静态成员方法
    public static int getMax(int age1,int age2){
        return age1>age2?age1:age2;
    }
    //实例成员方法
    public void study(){
        System.out.println(name+"好帅");
    }

    public static void main(String[] args) {
        //1.类名.静态方法名
        System.out.println(Student.getMax(10, 3));
        //直接方法名
        System.out.println(getMax(10, 3));
        //实例方法只能用实例访问
        //study();//Non-static method 'study()' cannot be referenced from a static context
        Student s=new Student("猪八戒");
        s.study();
    }
}

```

#### **static访问注意事项：**

静态方法只能访问静态成员变量，不可以**直接**访问实例成员变量

实例成员方法可以访问静态成员变量以及实例成员变量

静态成员方法中是不可以用this的，因为this是指向实例的。

```java
package com.xfzy.d1_static;

public class Student {
    //实例成员变量
    private String name;
    //静态成员变量
    private static String hobby="吃饭";

    public Student(String name) {
        this.name = name;
    }
 
    //静态成员方法  只能访问静态成员变量，不可以访问实例成员变量   不可以用this的，因为this是指向实例的。
    public static int getMax(int age1,int age2){
        System.out.println(hobby);//能访问静态成员变量
        //System.out.println(name+"好帅");//Non-static field 'name' cannot be referenced from a static context
        //System.out.println(this);//'com.xfzy.d1_static.Student.this' cannot be referenced from a static context
        return age1>age2?age1:age2;
    }
    //实例成员方法   实例成员方法可以访问静态成员变量以及实例成员变量
    public void study(){
        System.out.println(name+"好帅");
        System.out.println(hobby);
    }

    public static void main(String[] args) {
        //1.类名.静态方法名
        System.out.println(Student.getMax(10, 3));
        //2.直接方法名（同一个类中才可以）
        System.out.println(getMax(10, 3));
        //3.实例.静态方法名
        Student s=new Student("猪八戒");
        System.out.println(s.getMax(10, 3));
        
        //实例方法只能用实例访问
        //study();//Non-static method 'study()' cannot be referenced from a static context
        s.study();
    }
}
```

### 02工具类

工具类：**类中都是一些静态方法**，每个方法都是以完成一个共用的功能为目的，这个类用来给系统**开发人员共同使用**的。

由于工具类都是静态方法，直接用类名就可以访问，因此，工具类无需创建对象，建议将工具类构造器私有化。

```java
package com.xfzy.d12_static_util;

public class Util {
    //构造器私有！工具类无需创建对象，所以把构造器私有化
    private Util(){

    }
    public static String createVeritifyCode(int n){
        String code="";
//        生成一个随机验证码
        return code;
    }
}
```

### 03代码块

代码块是类的五大成分之一（成员变量，构造器，方法，代码块，内部类），定义在内中方法外。

在Java类下，使用{}括起来的代码被称为代码块。

#### 静态代码块

格式：static{}

特点：需要通过**static关键字修饰，随着类的加载而加载，并且自动触发、只执行一次**

使用场景：在类加载的时候做一些**静态数据初始化**的操作，以便后续使用。

#### 构造代码块/实例代码块（了解，见得少）

格式：{}

特点：每次创建对象，**调用构造器执行时，都会执行**该代码块中的代码，**并且在构造器执行前执行**

使用场景：初始化实例资源

### 04设计模式--单例模式

#### 设计模式：

开发中一个问题有n中解决方案，最优的一种被总结出来称为设计模式。

设计模式共有20多种。

设计模式：用来解决什么问题？遇到这种问题该模式怎么写，它如何解决的？

#### **单例模式：**

**可以保证系统中，应用该模式的这个类永远只有一个实例，即一个类永远只能创建一个对象。**

例如任务管理器对象只有一个，可以节约内存空间。

单例实现的方式有很多：饿汉单例模式、懒汉单例模式...

##### 饿汉单例模式：

在用类获取对象的时候。对象已经提前为你创建好了。

**设计步骤：**定义一个类，把**构造器私有**。定义一个**静态变量存储一个对象。**

```java
package com.xfzy.d4_static_singleinstance;

/**
 * 使用饿汉单例实现单例类
 */
public class SingleInstance {
    /**
     * 2.饿汉单例是在获取对象之前就提前准备好了一个，这个对象只能是一个，所以定义静态成员变量。
     */
    public static SingleInstance instance=new SingleInstance();
    /**
     * 1.构造器私有
     */
    private SingleInstance(){
    }
}
```

```java
package com.xfzy.d4_static_singleinstance;

public class Test1 {
    public static void main(String[] args) {
        SingleInstance s1=SingleInstance.instance;
        SingleInstance s2=SingleInstance.instance;
        System.out.println(s1 == s2);//true证明拿的是同一个对象
    }
}
```

##### 懒汉单例模式：

真正需要该对象的时候，才去创建一个对象（延迟加载对象）

**设计步骤：**1.**构造器私有**。2定义一个静态变量存储一个对象(一定要私有化！不要让别人通过这个变量拿到了null)。3**提供一个方法返回单例对象**

```java
package com.xfzy.d4_static_singleinstance;

public class SingleInstance2 {
    /**
     * 1.定义一个静态变量存储一个对象即可；属于类，与类一起加载
     * 一定要私有化！不要让别人通过这个变量拿到了null
     */
    private static SingleInstance2 instance;//null
    /**
     * 2.构造器私有
     */
    private SingleInstance2() {

    }
    /**
     * 3.必须提供一个方法返回一个单例对象
     */
    public static SingleInstance2 getInstance() {
        //判断是否已经创建了实例，确保单例！
        if(instance==null){
            instance=new SingleInstance2();
        }
        return instance;
    }
}
```

```java
package com.xfzy.d4_static_singleinstance;

public class Test2 {
    public static void main(String[] args) {
        SingleInstance2 s1=SingleInstance2.getInstance();
        SingleInstance2 s2=SingleInstance2.getInstance();
        System.out.println(s1 == s2);//true 单例！
    }
}
```

**饿汉快，懒汉节省内存。**



### 05继承

Java中提供了一个关键字extends。可以实现让一个类和另一个类建立起父子关系。

```java
public class Student extends People{}
```

当子类继承父类后，就可以直接使用父类公共的属性和方法了。

提高复用性，减少代码冗余，增强类的功能扩展性。

内存原理：当new一个子类的时候，堆内存中开辟了一个对象，这个对象包括父类空间super，子类空间this两部分，但是通过实例名.属性/方法都是可以自动访问对应的。

#### 特点：

1，子类不会继承父类的构造器，父类构造器用于初始化父类对象呀。

2，java是**单继承**模式：一个子类只能继承一个直接父类。但是可以**多层继承**，爷父子。（就近原则，先用爸爸的）

​		**不支持多继承**是因为有可能出现冲突，比如两个父类有同名方法。

3，java中所有的类都是Object类的子类。

有争议的观点：

1，**子类可以继承父类的私有成员，但是不能直接访问。**

2，**子类不可以继承父类的静态成员，因为静态成员只能有一份，只能算是共享的。**



#### 访问特点：

在子方法中访问成员（成员变量、成员方法）满足：

**就近原则**，先找子类，子类没有找父类，父类没有就报错。

如果出现重名，一定要在子类使用父类的，用**super.父类成员变量/方法**，子类自己的**this.子类成员变量/方法**



#### 方法重写：

继承体系中，子类出现了和父类中一模一样的方法申明，我们就称子类这个方法是重写的方法。

**@Override**写在重写方法之上，用于校验，可以提高程序可读性

```
@Override //重写校验注解，加上后，这个方法必须是正确重写的，更安全
```

##### **重写的要求：**

**1重写方法的名称、形参列表必须与被重写方法的名称和参数列表一致。**

**2私有方法不能被重写！**

**3静态方法不能被重写**，父类的静态方法是父类的，用父类名调

**4**子类重写父类方法时，访问**权限必须大于或者等于父类****（private<缺省<protected<public）**

**重写是否成功就看@Override报不报错！《申明不变，重新实现！》**

#### 

#### 子类继承父类后构造器特点：

子类中**所有的构造器默认都会先访问父类中无参构造器**，在执行自己。

##### 为什么？现有爸爸才有儿子

1.因为子类在初始化的时候，有可能会使用到父类中的数据，如果父类没有完全初始化完成，子类将无法使用父类的数据。

2.子类初始化之前，一定要**调用父类构造器先完成父类数据空间的初始化**

##### 如何调用的父类构造器？

**默认的子类构造器第一行都是super();**

写不写都有，默认找父类的无参数构造器执行。



#### super()调用父类的有参构造器

作用：**初始化继承自父类的数据。**

如果父类中没有无参构造器，只有有参构造器，会报错，因为子类默认调用父类的无参构造器。

解决：子类构造器中可以书写super(...),手动调用父类的有参构造器。或者父类无参构造器写出来。



#### this、super

this代表本类（子类）对象的引用，super代表父类存储空间的标识。

**super()：调用父类构造器**，作用：**初始化继承自父类的数据。**

**this()：本类构造器中访问兄弟构造器**

```java
public Student(String name){
	this(name,"重庆邮电大学");//如果不填写学校，默认用重庆邮电大学，调用其他构造器！
}
public Student(String name,String school){
	this(name,"重庆邮电大学");
}
```

**注意：**

**子类通过this()调用本类的其他构造器，本类其他构造器会通过super()去手动调用父类的构造器，最终还是会调用父类构造器的。**

**所以this()也要放在构造器第一行，super()也是，所以二者不能共存于同一个构造器中！**（有this()了也不会默认有super()）



### 06 包

包是用来分门别类管理不同类的，类似于文件夹、建包利于程序的管理和维护。

**建包的语法格式** ：package 公司域名倒写.技术名称。建议小写且具备意义。（idea中都自动写好了这一行）

不同包下的类需要导入使用：

**导入包格式**：import 包名.类名；

1 同一个包下的类可以直接访问

2 不同包下的类需要导入包

3 如果这个类中使用不同的包下的相同的类名，此时默认的只能导入一个包，另一个**类要使用全名访问(带包名访问)。**

```java
package com.xfzy.d1_package;

import com.xfzy.d1_package.it.Student;

public class Test {
    //1 同一个包下的类可以直接访问
    //2 不同包下的类需要导入包
    Student s = new Student();
    //3 如果这个类中使用不同的包下的相同的类名
    //  此时默认的只能导入一个包，另一个类要使用全名访问(带包名访问)。
    com.xfzy.d1_package.it2.Student s2=new com.xfzy.d1_package.it2.Student();
}
```



### 07权限修饰符

用来控制一个成员能够被访问的范围。

可以修饰成员变量。方法，构造器，内部类，不同权限修饰符的成员能够被访问的范围将受限制。

**权限修饰符作用范围：**

private		同类中

缺省 			同类中、同包不同类

protected   同类中、同包不同类、不同包下的子类（用子类访问）

public		   同类中、同包不同类、不同包下的子类（用子类访问）、不同包不同类

```java
package com.xfzy.d2_modifier;

public class Dad {
    /**
     * 私有方法
     */
    private void privateMethod() {
        System.out.println("--private--");
    }

    /**
     * 缺省修饰成员
     */
    void method(){
        System.out.println("--缺省--");
    }

    /**
     * 受保护的方法
     */
    protected void protectedMothod(){
        System.out.println("--受保护的--");
    }
    /**
     * public修饰的方法
     */
    public void publicMothod(){
        System.out.println("--public--");
    }

    public static void main(String[] args) {
        //同一个类中都可以访问到
        Dad f=new Dad();
        f.privateMethod();
        f.method();
        f.protectedMothod();
        f.publicMothod();
    }
}
```

注意：protected 不同包下的子类（用子类访问）：

```java
package com.xfzy.d2_modifier.itcast;

import com.xfzy.d2_modifier.Dad;

public class Son extends Dad {
    public static void main(String[] args) {
        //同一个类中都可以访问到
        Dad f=new Dad();

        //私有方法只能在同类中访问到
        //f.privateMethod();//报错

        //缺省方法只能在同包下访问
        //f.method();//报错

        //protected只能在同包类或者其他类的子类才可以访问到（子类中用子类访问而不是父类）
        Son s=new Son();
        s.protectedMothod();//子类中用子类访问

        f.publicMothod();
    }
}
```

注意：自己定义成员（方法、构造器、成员变量等）一般需满足如下要求：

成员变量一般私有；

方法一般公开；

如果该成员只希望本类访问，使用private修饰。

如果该成员只希望本类、同一个包下的其它类和子类访问，使用protected修饰符



### 08final的语法

final的作用：

可以修饰（类、方法、变量）

1修饰类：表示该类是**最终类，不能被继承**；例如工具类可以加final

2修饰方法：表示该类是**最终方法，不能被重写**；可以定义常量

3修饰变量：表示该**变量第一次赋值后，不能再次被赋值**（有且仅能被赋值1次）（修饰局部变量，静态成员变量->常量，实例成员变量）

注意：final修饰变量后，如果是**基本类型变量，则不可改变值，**如果是**引用类型变量，则对象地址不能改变，对象内容可以改变**。



### 09常量

使用**public static final修饰的成员变量**，**必须有初始值**，而且执行的过程中其值不能被改变。

作用：**可以用于系统的配置信息，**方便程序维护，提高可读性。

常量命名规范：英文单词**全部大写**。多个单词下划线连接起来。

执行原理：

在编译阶段会**宏替换**，把使用常量的地方全都替换成真实的字面量。让使用常量的程序执行性能与直接使用字面量是一样的。



### 10枚举

枚举是Java中的一种特殊类型

枚举的作用：”**是为了做信息的标志和信息的分类**“。相比于定义几个常量，安全性准确性高很多，且天然结合了switch分支。

（做分类：用枚举；固定具体值：用常量）

**定义格式：**

```java
//修饰符 enum 枚举名称{
//	第一行都是罗列枚举类实例的名称
//}
enum Season{
    //第一行都是罗列枚举类实例的名称
    SPRING,SUMMER,AUTUMN,WINTER;
}
```

**反编译：**

当我们在命令窗口使用**javac Season.java**然后使用**javap Season.class**即可反编译，得到如下代码：

```Java
public final class Season extends java.lang.Enum<Season> {
  public static final Season SPRING;
  public static final Season SUMMER;
  public static final Season AUTUMN;
  public static final Season WINTER;
  public static Season[] values();
  public static Season valueOf(java.lang.String);
  static {};
}
```

**枚举特征：**

枚举类都是继承了枚举类型：java.lang.Enum

枚举都是最终类，不可以被继承

**枚举类的构造器都是私有的**，**枚举对外不能创建对象。**

枚举类的第一行默认都是罗列枚举对象的名称的。

枚举相当于是**多例模式**：只能创建固定个数对象。



### 11抽象类

abstract：抽象，可以修饰类、成员方法。

abstract修饰类，这个类就是抽象类；修饰方法，这个方法就是抽象方法。

```java
//修饰符 abstract class 类名{
//	修饰符 abstract 返回值类型 方法名称(形参列表);
//}
package com.xfzy.d6_abstract;

public abstract class Animal {
    /**
     * 每个动物可能跑的不一样，所以先不实现，交给子类自己去实现。约定子类一定要实现，不然会报错！
     * 所以用抽象类、方法
     * 抽象方法不能写方法体代码。
     */
    public abstract void run();
}

```

**使用场景：**抽象类一般作为父类，让子类继承；可以理解成不完整的设计图。

当父类知道子类一定要完成某些行为，但是每个子类又实现的不一样，于是该父类就把该行为定义成抽象方法形式，具体实现交给子类去完成，此时这个类就可以声明为抽象类。**约定子类一定要实现，不然会报错！**



#### 注意：

1类有的东西，抽象类都有

2抽象类中可以没有抽象方法，但是有抽象方法的必须是抽象类

3一个类继承了抽象类必须重写抽象类的全部抽象方法，否则这个类也必须定义成抽象类。

4不能有abstract修饰变量、代码块、构造器。

**most important:得到了抽象方法，失去了创建对象的能力！**

**为什么？**假如可以创建，抽象方法连代码块都没有，运行会报错。**即使抽象类中没有抽象方法，也不能**创建对象，如果我这时候让你创建了，你偷偷加上抽象方法怎么办？**所以抽象类不能创建对象！**



#### final和abstract是互斥关系！

**abstract定义的抽象类**作为模板让子类继承，**final定义的类**不能被继承。

**抽象方法**定义通用功能让子类重写，**final定义的方法**子类不能重写。



### 12设计模式--模板方法模式

模板方法模式：当系统中出现同一个功能多处开发，而该功能大部分代码一样，部分代码可能不同的时候。

**实现步骤：**

1把功能定义为一个所谓的模板方法，放在抽象类中，模板方法中只定义通用且能确定的代码。

2模板方法中不能决定的功能定义成抽象方法让子类去实现。

模板方法最好加上final，不能被重写

```java
//写作文案例
package com.xfzy.d9_template;

public abstract class Student {
    //模板方法最好加上final
    public final void write(){
        System.out.println("这是作文开头，一样的部分");
        zhengwen();
        System.out.println("这是作文结尾，一样的部分");
    };
    public abstract void zhengwen();

}

```



### 13接口

定义格式：

public interface 接口名 {}

jdk8之前接口中只能有抽象方法和常量

注意：由于接口体现规范思想，规范默认都是公开的，所以代码层面，**public static final 和public abstract可以省略不写。**

```java
package com.xfzy.d10_interface;

public interface InerfaceDemo {
    /**
     * 目标：接口中成分特点
     * jdk8之前接口中只能有抽象方法和常量
     */

    //1常量
    //注意：由于接口体现规范思想，规范默认都是公开的，所以代码层面，public static final 可以省略不写。
    String MY_NAME = "fangqianlin";
    //public static final String MY_NAME="fangqianlin";

    //2抽象方法
    //注意：由于接口体现规范思想，规范默认都是公开的，所以代码层面，public abstract可以省略不写。
    void run();
    //public abstract void run();
    void eat();
    //public abstract void eat();
}
```

#### 接口的用法

接口是用来被类实现（implements）的，实现接口的类称为是实现类。实现类可以理解为所谓的子类。

```java
修饰符 class 实现类 implements 接口1,接口2,接口3，...{

}
```

```java
package com.xfzy.d11_interface_implements;

public interface SportsMan {
    void run();
    void competition();
}
```

```java
package com.xfzy.d11_interface_implements;

public class PingpangMan implements SportsMan{
    private String name;
    public PingpangMan(String name) {
        this.name = name;
    }
    //实现接口的方法
    @Override
    public void run() {

    }

    @Override
    public void competition() {

    }
}
```

#### **注意：**

**接口可以单实现，也可以多实现。**

**一个类实现接口，必须实现全部接口的全部抽象方法，否则这个类需要定义成抽象类。**



**类和类的关系：单继承**

**类和接口的关系：多实现**

**接口和接口的关系：多继承**，一个接口可以同时继承多个接口。



#### 接口多继承

作用：规范合并，整合多个接口为同一个接口，便于子类实现。



#### jdk8新增方法（开发很少用，Java源码涉及）

去过按照原来的实现类需要实现接口的所有抽象方法，当项目需要升级时，我们给接口添加方法了，牵一发而动全身的需要给实现类添加实现。很麻烦，所以现在**允许接口中直接定义带有方法体的方法。**

##### 1.默认方法（jdk8开始）

必须用**default修饰**，默认用public修饰

默认方法，接口不能创建对象，这个方法只能过继给实现类，由**实现类的对象调用**。

##### 2.静态方法

必须使用**static修饰**，默认用public修饰

接口的静态方法，必须由**接口名自己调用**。

##### 3私有方法（实例方法）（jdk9支持）

必须使用**private修饰**，在接口内部才能访问（**其他私有方法，默认方法中去调用**）



#### 接口注意事项

1 **接口不能创建对象**！（抽象类都不能创建，接口更抽象！）

2 一个类实现多个接口，**多个接口中有同样的静态方法不冲突**！（实现类不让调接口的静态方法！不像实例可以调用类的静态方法）

3 一个类继承了父类，同时又实现了接口，**父类中和接口中有同名方法。默认用父类的**！（先有亲爸才有干爹！）

4 一个类实现多个接口，多个接口中存在同名的默认方法，不冲突，但是需要实现类重写该方法，不然也会报错。（把他俩全干掉）

5 一个接口继承多个接口，是没有问题的，但是如果多个接口存在规范冲突则不能多继承。（比如两个抽象方法名返回值不同。）



### 14多态

**同类型的对象，执行同一个行为，会表现出不同的行为特征。**

##### 多态的常见形式：

```java
父类类型 对象名称=new 子类构造器;
接口 对象名称=new 实现类构造器;
```

```java
package com.xfzy.d1_polymorphic;

public class Test {
    public static void main(String[] args) {
//        Dog a=new Dog();
//        a.run();
//        Rabit r=new Rabit();
//        r.run();
        //1.多态的形式
        Animal a=new Dog();
        a.run();//狗狗跑得快,[编译看Animal中有没有run(),运行的时候走的Dog中的方法]
        System.out.println(a.name);//父类动物,[编译看Animal中有没有name,运行的时候也走的Animal中的name]

        Animal r=new Rabit();
        r.run();//兔子跑得哈哈哈哈,[编译看Animal中有没有run(),运行的时候走的Rabit中的方法]
        System.out.println(r.name);//父类动物,[编译看Animal中有没有name,运行的时候也走的Animal中的name]

    }
}
```

##### **多态中成员访问特点：结合以上代码看**

方法调用：编译看左边，运行看右边。

变量调用：编译看左边，运行也看左边。（**多态侧重行为多态**）

##### **多态使用的前提：**

有继承/实现关系；有父类引用指向子类对象；有方法重写。



#### 多态的优势

1.在多态的形式下，**右边的对象可以实现解耦合**，便于扩展和维护。

```java
Animal a=new Dog();//比如这里想要用其他的类，直接将Dog()整个替换成Cat();
a.run();//后续业务行为随对象而变，后续代码无需修改
```

2.定义**方法的时候，使用父类型作为参数，该方法就可以接收这父类的一切子类对象，**体现出多态的扩展与便利性。

```java
//要求所有动物都可以进来比赛
public void go(Animal a) {
   System.out.println("开始");     
   a.run();
   System.out.println("结束");   
}
```



#### 多态产生一个问题

多态下不能访问子类的独有功能。（编译阶段就看父类的）

```java
Animal a=new Dog();//比如这里想要用其他的类，直接将Dog()整个替换成Cat();
a.run();//父类有的方法
//a.kanmen();//狗才有的方法，会报错->多态下不能访问子类的独有功能。
```



#### 多态下引用数据类型的类型转换

**自动类型转换（从子到父）**：子类对象赋值给父类类型的变量指向。

```java
Animal a=new Dog();//比如这里想要用其他的类，直接将Dog()整个替换成Cat();
a.run();//父类有的方法
```

**强制类型转换（从父到子）**：子类 对象变量=（子类）父类类型的变量

**作用：可以解决多态下的劣势。可实现调用子类独有的功能**

```java
Animal a=new Dog();//比如这里想要用其他的类，直接将Dog()整个替换成Cat();
a.run();//父类有的方法
//a.kanmen();//狗才有的方法，会报错->多态下不能访问子类的独有功能。
Dog d=(Dog)a;//强制转换——从父类类型到子类类型必须强制转换
d.kanmen();//狗才有的方法，可以访问了
```

注意：如果**转型后的类型和对象真实类型不是同一种类型**，**编译不报错，转换的时候会报错！**

```java
Animal a=new Dog();//比如这里想要用其他的类，直接将Dog()整个替换成Cat();
Rabit d=(Rabit)a;//强制转换——类型不一样，编译不报错，转换的时候会报错！
```

Java建议强制转换前使用**instanceof判断当前对象的真实类型**，在进行强制转换。

```java
if(变量名 instanceof 真实类型)//判断左边变量指向的对象真是类型是否是右边类型或者是其子类类型。是则返回true
```

```java
Animal a=new Dog();
if(a instanceof Dog){
	Dog d=(Dog)a;
}else if{
    Rabit r=(Rabit)a;
}
```

### 15内部类

内部类就是定义在一个类里面的类，里面的类可以理解成（寄生），外部类可以理解成宿主。

```java
public class People{
    //内部类
	public class Heart{
		
	}
}
```

**内部类场景：**当一个事物的内部，还有一个部分需要一个完整的结构来进行描述，而这个**内部的完整的结构又只有为外部事物提供服务**，那么整个内部的完整结构可以使用内部类来设计。

**内部类作用：** 内部类通常可以方便访问外部类的成员，包括私有成员。

​						内部类提供了更好的封装性，内部类本身就可以用private protected等修饰，封装性可以做更多控制。

#### 内部类分类：

##### 静态内部类：（用的少）

有static修饰，属于外部类本身

它的特点和使用 与 普通类是完全一样的，类有的成分他都有，只是位置在别人里面而已。

```java
public class Outer{
    //静态内部类
	public static class Inner{
		
	}
}
```

```java
//静态内部类创建对象的格式
public class Test{
	public static void main(String[] args){
		Outer.Inner in=new Outer.Inner();
	}
}
```

静态内部类    **可以**直接**访问外部类的静态成员**（外部类静态成员只有一份可以被共享访问）

静态内部类**不可以**直接**访问外部类的实例成员**（外部类的实例成员必须用外部类对象访问）



##### 成员内部类（用的多一点）

无static修饰，属于外部类的对象。

jdk16之前，成员内部类中不能定义静态成员，jdk开始也可以定义静态成员了（虽然属于外部类实例，但是还是只有一份，共享）

```java
public class Outer{
    //成员内部类
	public class Inner{
		
	}
}
```

```java
//成员内部类创建对象的格式
public class Test{
	public static void main(String[] args){
		Outer.Inner in=new Outer().new Inner();//因为内部类属于外部类的实例。
        in.show();//访问内部类实例方法
        Outer.Inner.test();//访问内部类静态方法
	}
}
```

1.成员内部类**可以直接访问外部类的静态成员**（外部类的静态成员只有一份被共享访问）

2.成员内部类的**实例方法中可以直接访问外部类的实例成员**。（因为必须先有外部类对象，才能有成员的内部类对象，所以可以直接访问外部类对象的实例成员）

注意：在**内部类中访问所在外部类对象实例**需要使用：**外部类名.this**

成员内部类可能用的更多，因为要现有外部类对象才能有内部类对象，而静态内部类可以独立出来。



##### 局部内部类（没啥用）

只服务于局部执行体，现在还可以定义局部接口。

局部内部类放在方法、代码块、构造器等执行体中。

局部内部类的类文件名为：**外部类$N内部类.class**



##### 匿名内部类（重点）

本质上是一个**没有名字的局部内部类**，定义在方法中、代码块中、等。也会产生class文件。

**作用：方便创建子类对象，最终目的是为了简化代码编写。**

格式：

```
new 类|抽象类名|或者接口名(){
	重写方法;
}
```

```java
//例如：Employee是一个员工抽象类
Employee a=new Employee(){
	public void work(){
		
	}
}
a.work();
```

```java
package com.xfzy.d8_innerclass_anonymous;

public class Test {
    public static void main(String[] args) {
        //Animal a=new Tiger();
        //匿名内部类认为不需要定义子类,编译还是看左，运行看右。
        //不需要定义子类，方便快速定义一个对象
        Animal a = new Animal() {//实际上是多态，等同于上面那行
            @Override
            public void run() {
                System.out.println("老虎跑得快");
            }
        };
        a.run();
    }
}

//匿名内部类认为不需要定义子类
//class Tiger extends Animal{
//    @Override
//    public void run() {
//        System.out.println("老虎跑得快");
//    }
//}
abstract class Animal {
    public abstract void run();
}
```

**特点：** 匿名内部类是一个**没有名字的内部类**

​			匿名内部类**写出来就会产生一个匿名内部类的对象。**

​		    匿名内部类的对象类型相当于是当前new的那个类型的子类型（多态）。



**在开发中的使用形式：可以直接作为方法的实际参数进行传输 **

```java
package com.xfzy.d8_innerclass_anonymous;

/**
 * 掌握匿名内部类的使用形式
 */
public class Test2 {
    public static void main(String[] args) {

        Swimming s=new Swimming() {
            @Override
            public void swim() {
                System.out.println("学生的开了自由泳");
            }
        };
        go(s);//类似对象回调
        //直接当作参数
        go(new Swimming() {
            @Override
            public void swim() {
                System.out.println("更简化了游泳");
            }
        });
    }
    public static void go(Swimming s){
        s.swim();
    }
}
//class Student implements Swimming{
//    @Override
//    public void swim() {
//        System.out.println("学生的开了自由泳");
//    }
//}
interface Swimming{
    void swim();
}
```



匿名内部类使用场景：

开发中不是我们主动去定义内部类的，而是别人需要我们写或者我们可以写的时候才会使用。匿名内部类的代码可以实现代码进一步的简化。



### 16常用API

#### Object类

Object类的方法是一切子类都可以直接使用的（一个类默认继承了Object类/间接继承了Object类）

Object类常用方法：

1.toString()默认返回当前**对象在堆内存中的地址信息**：类的权限名@内存地址

```java
String toString()
```

开发中希望是对象内容数据被输出，所以tostring方法存在的**意义就是为了被子类重写，以便返回对象的内容信息**，而不是地址信息。

可以使用tos加回车快速生成此重写方法。



2.equals(Object obj)默认是比较当前对象与另一个**对象的地址**是否相同，相同返回true，不同返回false

```java
boolean equals(Object obj)
```

开发中希望是对象内容数据被比较输出，所以equals方法存在的**意义就是为了被子类重写，以便返回对象的内容对比信息**，而不是地址信息对比。

可以使用equ加回车快速生成此重写方法。



#### Objects类

Objects类也是Object类的子类，是从jdk7之后才有的

引入：官方重写equals方法时，在进行字符串比较时，没用对象（字符串）自己的equals方法，而是选择了Objects的equals方法来比较两个对象。

**1.equals方法：比较两个对象，底层会先进行非空判断，从而可以避免空指针异常。再调用第一个参数的equals比较。**

```java
static boolean equals(Object a, Object b)
```

Objects的equals方法比较的结果是一样的，但是更安全。（比如有null）

**2.isNull方法，判断变量是否为null，为null返回true**，跟==比较完全一样

```java
static boolean isNull(Object obj)
```



#### StringBuilder类

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/StringBuilder.html

是一个可变的字符串类，我们可以把它看成一个对象容器。

作用：提高字符串的操作效率，如拼接，修改等。

StringBuilder构造器

```java
StringBuilder()
```

构造一个字符串生成器，其中没有字符，初始容量为16个字符。

```java
StringBuilder(int capacity)
```

构造一个字符串生成器，其中不包含字符，并由capacity参数指定初始容量。

```java
StringBuilder(CharSequence seq)
```

构造包含与指定的“CharSequence”相同字符的字符串生成器。

```java
StringBuilder(String str)
```

构造初始化为指定字符串内容的字符串生成器。

方法：

1.append()

2.reverse()



**性能好**

String是不可变的，拼接字符串的时候要利用StringBuilder，再转成String，加一次就创建这2个对象了

StringBuilder：内容可变的，拼接字符串性能好，只用这一个对象就好了。

注意：stringbuilder只是**拼接字符串的手段，**效率好，最终**还是需要恢复成String类型，平时也要使用String**



#### Math类

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/lang/Math.html

包含执行基本数字运算的方法，Math类没有提供公开的构造器。

类中的方法都是静态的，直接用Math.静态方法名就可以用。

常用的跟js中差不多。

```java
static double random()
//返回一个带正号的双精度值，大于或等于0.0且小于1.0。[0.0,1.0)
```

生成0-9的随机数

```java
  (int)Math.random()*10;
//(int)  [0.0,1.0)  *10  ->  0-9
```



#### System类

System类的功能都是通用的，直接类名调用即可，所以System不能被实例化。

```java
static void exit(int status)
```

终止当前运行的Java虚拟机，jvm终止。非零表示异常终止

```java
static long currentTimeMillis()
```

以毫秒为单位返回当前时间。从1970-1-1 00:00:00走到此刻的毫秒值(算是c语言的生日)

```java
static void arraycopy(Object src, int srcPos, Object dest, int destPos, int length)
    //                被拷贝的数组， 开始索引   ，  目标数组   ， 粘贴位置    ，拷贝个数
```

将数组从指定的源数组（从指定位置开始）复制到目标数组的指定位置。



#### BigDecimal类（大 小数类型）

用于解决浮点型运算精度失真的问题

比如

```java
double c=0.1+0.2;//0.300000000004
```

使用方法：

**创建对象BigDecimal封装浮点型数据（最好的方式是调用方法）**

禁止使用以下构造器：

```java
BigDecimal(double val)//将双精度转换为BigDecimal，这是双精度二进制浮点值的精确十进制表示。
```

以上还是会造成精度失真。

可以使用字符串参数的构造器

```java
BigDecimal(double val)//将BigDecimal的字符串表示形式转换为BigDecimal。
```

**（最好的方式是调用方法）**此方法**内部其实执行了Double.toString()**,使用[“double.toString（double）”]提供的“double”规范字符串表示法，将“double”转换为“BigDecimal”

```java
public static BigDecimal valueOf(double val):包装浮点数成为BigDecimal对象
```

```java
BigDecimal bd1= BigDecimal.valueOf(0.1);
BigDecimal bd2= BigDecimal.valueOf(0.2);
bd1.add(bd2);//0.3
bd1.subtract(bd2);
bd1.multipty(bd2);
bd1.divide(bd2);
```

加减乘除。

**运算完之后记得转成Double类型：API**

```java
bd1.doubleValue();
```

注意事项：BigDecimal是一定要精度运算的，如果除不尽，会报错。必须指定精度。

```java
BigDecimal divide(BigDecimal divisor, int scale, RoundingMode roundingMode)
```

返回“BigDecimal”，其值为“（this/divisor）”，其小数位数为指定值。

```
BigDecimal bd1= BigDecimal.valueOf(3);
BigDecimal bd2= BigDecimal.valueOf(10);
//bd2.divide(bd1);//0.33333~会报错。必须加范围
bd2.divide(bd1,2,RoundingMode.HALF_UP);//0.33
```



### 17Date类

Date类的对象在Java中代表的是当前所在系统的此刻日期时间。

**构造器：**

```java
Date()//日期时间
```

分配“日期”对象并对其进行初始化，使其表示分配的时间，以最接近的毫秒为单位。

```java
Date(long date)//传入毫秒值得到日期时间
```

传入毫秒值，转换成`Date`对象

**获取时间毫秒值：**

```java
//1.Date的getTime()方法
Date d=new Date();//日期对象
long time = d.getTime();
System.out.println(time);

//2.System的方法
long time1=System.currentTimeMillis();
System.out.println(time1);
```

**将毫秒值转换成日期对象：**

```java
//1.构造器
Date d1=new Date(毫秒值);
System.out.println(d1);

//2.Date对象的setTime方法
Date d3=new Date();
d3.setTime(毫秒值);
System.out.println(d3);
```



### 18 SimpleDateFormat类

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/text/SimpleDateFormat.html

可以对Date对象或**时间毫秒值格式化**成为我们想要的时间形式。

```java
Date对象  -> 2017年12月28日 22:54:
时间毫秒值 -> 2017年12月28日 22:54:
```

也可以把字符串的**时间形式解析成日期对象**。

```java
2017年12月28日 22:54: -> Date对象
```

**构造器：**

```
SimpleDateFormat()
```

使用默认模式和默认日期格式符号构造“SimpleDateFormat”

```
SimpleDateFormat(String pattern)
```

使用指定模式和默认日期格式符号构造“SimpleDateFormat”

```
SimpleDateFormat(String pattern, DateFormatSymbols formatSymbols)
```

使用指定模式和指定日期格式符号构造“SimpleDateFormat”。

```
SimpleDateFormat(String pattern, Locale locale)
```

使用给定区域设置的给定模式和默认日期格式符号构造“SimpleDateFormat”。

**格式化方法：**

```java
public final String format(Date date)
```

将日期   ->   日期/时间字符串

```java
public final String format(Object time)
```

将时间毫秒值  ->  成日期/时间字符串

**解析方法：**

```java
Date parse(String source)
```

从给定字符串的开头分析文本以生成日期。

**其他方法：**

```java
time1.after(time2);//判断time1是否在time2后面
time1.before(time2);//判断time1是否在time2前面
```

**例子：**

1格式化时间对象

```java
Date d =new Date();
SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss EEE a");
String rs1=sdf.format(d);
```

2格式化时间毫秒值

```java
long time = System.currentTimeMillis();
String rs2= sdf.format(time);
```

3解析时间

2017年12月28日 22:54:06

```java
public static void main throws ParseException{
    String dateStr = "2017年12月28日 22:54:06";
	SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");//格式要和目标格式完全一样
	Date d =sdf.parse(dateStr);//会报错，让你检查格式对不对，需要自己抛出错误,
	long time = d.getTime()+2L*24*60*60;//建议加L转换成浮点运算，以免越界
	sdf.format(time);
}

```

### 19Calendar类

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/Calendar.html

Calendar代表了系统此刻日期对应的日历对象。**是可变日期对象，一旦修改，其对象表示的时间将产生变化。**

Calendar是一个抽象类，不能直接创建对象。public abstract class **Calendar**

Calendar的**getInstance方法返回一个Calendar对象**，该对象的日历字段已使用当前日期和时间初始化：

```java
Calendar rightNow = Calendar.getInstance();
```

**用的时候直接打印出来以获取字段field名称。**

**方法：**

```java
int get(int field)
```

返回给定日历字段的值。

```java
void set(int field, int value)
```

将给定日历字段设置为给定值。

```java
abstract void add(int field, int amount)
```

根据日历规则，向给定日历字段添加或减去指定的时间量。

```java
final Date getTime()
```

返回表示此日历的时间值（与1970-01-01的毫秒偏移量）的Date对象。

```java
long getTimeInMillis()
```

返回此日历的时间值（以毫秒为单位）。



### 20JDK8新增日期API

JDK8开始，java.time包提供了新的日期和时间API，主要涉及的类型有：

**LocalDate：**不包含具体时间的日期。

**LocalTime：**不含日期的时间。

**LocalDateTime：**包含了日期及时间。

**Instant：**代表的是时间戳。

**DateTimeFormatter**：用于做时间的格式化和解析的

**Duration：**用于计算两个“时间“间隔

**Period：**用于计算两个“日期”间隔

新增的Api严格区分了时刻、本地日期、本地时间，并且对日期和时间进行运算更加方便。

其次，新api类型几乎全部是不变类型（和String的使用类似），可以放心使用不必担心被修改。



#### **LocalDate LocalTime LocalDateTime：**

分别表示日期 时间 日期时间对象，他们的类的实例是不可变对象。

他们**三者构建对象和API都是通用的。**

**构建对象：**

```java
static LocalDate/LocalTime/LocalDateTime now()
```

静态方法，根据当前时间创建对象

```java
static LocalDate/LocalTime/LocalDateTime of()
```

静态方法，根据指定时间/日期创建对象

**LocalDateTime可以转换成LocalDate/LocalTime**：

```java
LocalDate toLocalDate()
LocalTime toLocalTime()
```

时间修改相关API：

LocalDateTime综合了LocalDate LocalTime 里面的方法，所以只用后两者来举例：

这些**方法返回的是一个新的实例引用，因为他们都是不可变的。**

**1向当前对象加：反之减：minus开头**

```
plusDays(long days)
```

```
plusHours(long hours)
```

```
plusMinutes(long minutes)
```

```
plusMonths(long months)
```

```
plusNanos(long nanos)
```

```
plusSeconds(long seconds)
```

```
plusWeeks(long weeks)
```

```
plusYears(long years)
```

**2将xxx修改为指定值并返回新的对象**

```
withDayOfMonth(int dayOfMonth)
```

```
withDayOfYear(int dayOfYear)
```

```
withHour(int hour)
```

```
withMinute(int minute)
```

```
withMonth(int month)
```

**3判断日期前后**

```java
boolean isAfter(ChronoLocalDateTime<?> other)
```

```java
boolean isBefore(ChronoLocalDateTime<?> other)
```



#### Instant时间戳

jdk8获取时间戳更简单，功能更丰富。

Instant类由一个静态的工厂方法now()可以返回当前时间戳:

```java
Instant instant = Instant.now();
Date date = Date.from(instant);
instant=date.toInstant();
```

时间戳是包含日期和时间的，与java.util.Date很类似，事实上Instant就是类似JDK8以前的Date。

**Instant和Date可以相互转换。Instant默认是全球标准时间**

例：拿到此刻时间

```
Instant instant = Instant.now();
instant.atZone(ZoneId.systemDefault());//拿到本地时区id以获取本地时间
```



#### DateTimeFormatter

jdk8中引入的全新的日期时间格式器DateTimeFromatter。

正反都能调用format方法。

```java
LocalDateTime ldt = LocalDateTime.now();//日期时间对象
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");//格式器
String s1=ldt.format(dtf);//正反都能调用format方法。
String s2=dtf.format(ldt);//正向格式化
```

解析字符串时间成本地日期时间对象：

```
DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm:ss");//格式器
LocalDateTime ldt = LocalDateTime.parse("2017-12-28 22:54:21",dft);
```



#### Duration Period

分别表示：用于计算两个“时间“间隔、用于计算两个“日期”间隔



**Duration**主要的类方法：toDays(),toHours();toMinutes(),toMillis(),toNanos()两个时间相差的天数/小时。。。

用于localDateTime，也可用于Instant之间的比较：静态方法between()

```java
Duration duration = Duration.between(birthDate,today);//比较两个localDateTime实例，第二个参数减去第一个参数
duration.toDays()();//间隔的天数
```



**Period**主要的类方法：getYears(),getMonth();getDays()，只能精确到年月日。

用于localDate之间的比较：静态方法between()

```java
Period period = Period.between(birthDate,today);//比较两个localDate实例
period.getDays();//间隔的天数
```



#### ChronoUnit

ChronoUnit类是一个枚举类，可以用于在单个时间单位内测量一段时间，这个工具类是最全的了，可以**用于比较所有的时间单位。**



### 21包装类

其实就是8种基本数据类型对应的引用类型。

基本数据类型    引用数据类型

byte					Byte

short				   Short

int						**Integer**

long					 Long

char					**Character**

float					Float

double				Double

boolean			  Boolean

Java为了实现**一切皆对象**，为8种基本类型提供了对应的引用数据类型。

后面的**集合和泛型其实也只能支持包装类型**，不支持基本数据类型

**自动装箱：**基本类型数据变量可以直接赋值给包装类型的变量。

**自动拆箱：**包装类型的变量可以直接赋值给基本数据类型的变量。



**包装类的特有功能：**

1**包装类的变量的默认值可以是null，容错率更高**

2可以把**基本类型数据转换成字符串类型**（用处不大）

```java
integer.toString(10);//实例方法
Integer.toString(10);//静态方法
可以直接+"";
```

3可以把**字符串类型的数值转换成真实的数据类型**（真的很有用）

```java
Integer.parseInt("字符串类型的整数");
Double.parseDouble("字符串类型的小数");
```

可以使用静态方法：**valueOf()更方便**

```java
Integer.valueOf()("字符串类型的整数");
Double.valueOf()("字符串类型的小数");
```



### 22正则表达式

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/regex/Pattern.html

| 字符类          |                                                              |
| --------------- | ------------------------------------------------------------ |
| `[abc]`         | `a`, `b`, or `c` (simple class)                              |
| `[^abc]`        | 除a、b或c以外的任何字符                                      |
| `[a-zA-Z]`      | `a` through `z` or `A` through `Z`, inclusive (range范围)    |
| `[a-d[m-p]]`    | `a` through `d`, or `m` through `p`: `[a-dm-p]` (union并集)  |
| `[a-z&&[def]]`  | `d`, `e`, or `f` (intersection交集)                          |
| `[a-z&&[^bc]]`  | `a` through `z`, except for `b` and `c`: `[ad-z]` (subtraction减法) |
| `[a-z&&[^m-p]]` | `a` through `z`, and not `m` through `p`: `[a-lq-z]`(subtraction减法) |

| 预定义字符类别 |                                                              |
| -------------- | ------------------------------------------------------------ |
| `.`            | Any character (may or may not match [line terminators](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/regex/Pattern.html#lt))任何字符 |
| `\d`           | A digit: `[0-9]`一个数字                                     |
| `\D`           | A non-digit: `[^0-9]`非数字                                  |
| `\h`           | A horizontal whitespace character: `[ \t\xA0\u1680\u180e\u2000-\u200a\u202f\u205f\u3000]` |
| `\H`           | A non-horizontal whitespace character: `[^\h]`非水平空白字符： |
| `\s`           | A whitespace character: `[ \t\n\x0B\f\r]`空白字符            |
| `\S`           | A non-whitespace character: `[^\s]`非空白字符                |
| `\v`           | A vertical whitespace character: `[\n\x0B\f\r\x85\u2028\u2029]垂直空白字符：` |
| `\V`           | A non-vertical whitespace character: `[^\v]`                 |
| `\w`           | A word character: `[a-zA-Z_0-9]`英文数字下划线               |
| `\W`           | A non-word character: `[^\w]`一个非单词字符                  |

| 贪婪量词           |                                                              |
| ------------------ | ------------------------------------------------------------ |
| *X*`?`             | *X*, once or not at all一次或者0次                           |
| *X*`*`             | *X*, zero or more times零次或多次                            |
| *X*`+`             | *X*, one or more times一次或多次                             |
| *X*`{`*n*`}`       | *X*, exactly *n* times正好n次                                |
| *X*`{`*n*`,`}      | *X*, at least *n* times至少n次                               |
| *X*`{`*n*`,`*m*`}` | *X*, at least *n* but not more than *m* times至少n但不超过m次 |

#### **字符串对象提供了匹配正则表达式规则的API**

```java
public boolean matches(String regex);
```

正则在字符串方法中的使用：

```java
String replaceAll(String regex, String replacement)
```

替换此字符串中与给定[正则表达式]匹配的每个子字符串

```java
String[] split(String regex)
```

围绕给定[正则表达式]的匹配项拆分此字符串,返回一个字符串数组。

#### 正则表达式爬取信息

```java
String s="dawdwahdawhuiahhhhhhhhq12131321hhhhh321312";
//1定义爬取规则
String regex="[0-9]";
//2编译正则表达式成为一个匹配规则对象
Pattern p = Pattern.compile(regex);
//3通过匹配规则对象得到一个匹配数据内容的匹配器对象
Matcher m = p.matcher(s);
//4通过匹配器去内容中爬取数据
while(m.find()){
    System.out.println(m.group());
}
//boolean b = m.matches();
```



### 23Arrays类

#### 概述，常用功能

cao数组操作工具类，专门用于操作数组元素的。

常用api：

```java
static String toString(类型[] a)//返回指定数组内容的字符串表示形式。
    
static void sort(类型[] a)//对数组进行排序，默认升序
   
//只能比较引用类型
static <T> void sort(T[] a, Comparator<? super T> c)//根据指定比较器产生的顺序对指定的对象数组进行排序。
    
//二分查找，必须排好序在调用。找不到返回复数: -(应存在位置)-1
static int binarySearch(int[] a, int key)//使用二分查找算法在指定的int数组中搜索指定的值。返回索引。
```



#### Arrays类对于Comparator比较器的支持

自定义排序规则

设置**Comparator接口**（是函数式接口，可以简写成Lambda函数）对应的比较器对象，来定制比较规则。

```java
static <T> void sort(T[] a, Comparator<? super T> c)//根据指定比较器产生的顺序对指定的对象数组进行排序。
```

排序的时候要实现Comparator接口，用匿名类。实现比较方法，这个方法返回：

如果认为  左边数据 > 右边数据  返回正整数

如果认为  左边数据 < 右边数据  返回负整数

如果认为  左边数据 = 右边数据  返回 0

```
Double.compare();//比较浮点型，返回-1，1，0
```



### 24算法-选择排序 二分查找





### 25Lambda表达式

jdk8以后的新语法。

**作用：简化匿名内部类的代码写法。**

**格式：**

```java
(匿名内部类被重写方法的形参列表) -> {
	被重写方法的方法体代码。
}
```

**注意：**Lambda表达式只能简化**函数式接口**的匿名内部类的写法形式



#### 函数式接口：

首先必须是**接口**、其次接口中**有且仅有一个抽象方法**的形式。

通常我们会在**接口上加一个@FunctionalInterface注解**，标记该接口必须是**满足函数式接口**。

**常见函数式接口：**

**Comparator比较器，ActionListener时间监听器**



**Lanbda表达式的省略写法：**（类似js的箭头函数的规则，但是Java里代表匿名内部类）

1参数类型可以不写

2如果只有一个参数，参数类型可以省略，括号也可以省略

3方法体只有一行代码，大括号也可以省略，同时省略分号，此时，如果这行代码是return语句，必须省略return不写，也必须省略分号。



### 26集合

集合和数组都是容器。

**数组**定义完成后，长度固定，类型确定。

**集合**是java中**存储对象**的一种容器，大小不固定，启动后可以动态变化，类型也不固定，适合做元素增删操作。



集合类体系结构：

**Collection**单列：（接口）

​		**List：**添加的元素是**有序、可重复、有索引**的。（接口）

​				**ArrayList**：有序、可重复、有索引（实现类）

​				**LinkedList**：有序、可重复、有索引（实现类）

​		**Set：**添加的元素是**无序、不重复、无索引**的。（接口）

​				**HashSet：**无序、不重复、无索引（实现类）

​							**LinkedHashSet**：有序、不重复、无索引（实现类）

​				**TreeSet**：按照大小默认升序排序、不重复、无索引。（实现类）



**Map**双列：（接口）





#### Collection集合常用Api

Collection是单列集合的祖宗接口，它的功能是全部单列集合都可以继承使用的。

```java
boolean add(E e)//添加元素
```

```java
boolean addAll(Collection<? extends E> c)//将指定集合中的所有元素添加到此集合（可选操作）。
```

```java
void clear()//清空集合
```

```java
boolean contains(Object o)//如果此集合包含指定的元素，则返回“true”。
```

```java
boolean containsAll(Collection<?> c)//如果此集合包含指定集合中的所有元素，则返回“true”。
```

```java
boolean equals(Object o)//将指定对象与此集合进行相等性比较。
```

```java
int hashCode()//返回此集合的哈希代码值。
```

```java
boolean isEmpty()//如果此集合不包含元素，则返回“true”。
```

```java
Iterator<E> iterator()//返回此集合中元素的迭代器。
```

```java
default Stream<E> parallelStream()//返回一个可能并行的“流”，此集合作为其源。
```

```java
boolean remove(Object o)//从此集合中删除指定元素的单个实例（如果存在）（可选操作）。
```

```java
boolean removeAll(Collection<?> c)//删除此集合中也包含在指定集合中的所有元素（可选操作）。
```

```java
default boolean removeIf(Predicate<? super E> filter)//删除此集合中满足给定谓词的所有元素。
```

```java
boolean retainAll(Collection<?> c)//仅保留此集合中包含在指定集合中的元素（可选操作）。
```

```java
int size()//返回此集合中的元素数。
```

```java
default Spliterator<E> spliterator()//在此集合中的元素上创建[`Spliterator`]。
```

```java
default Stream<E> stream()//返回以此集合为源的顺序“流”。
```

```java
Object[] toArray()//返回包含此集合中所有元素的数组。
```

```java
default <T> T[] toArray(IntFunction<T[]> generator)//返回包含此集合中所有元素的数组，使用提供的“generator”函数分配返回的数组。
```

```java
<T> T[] toArray(T[] a)//返回包含此集合中所有元素的数组；返回的数组的运行时类型是指定数组的类型。
```



#### Collection常用遍历方式

##### 1迭代器遍历-所有集合通用

迭代器Iterator是集合的专用遍历方式。

Collection集合获取迭代器

```JAVA
Iterator<E> iterator()//返回集合中迭代器对象，该迭代器对象默认指向当前集合的0索引
```

Iterator中的常用方法：

```java
boolean hasNext();//如果迭代有更多元素，则返回“true”。
```

```java
E next();//返回迭代中的下一个元素。先get()取值，在++指针
```

##### 2foreach/增强for循环

既可以遍历数组也可以遍历集合。

jdk5之后出现的，内部原理是一个Iterator迭代器，遍历集合相于是迭代器的简化写法。

实现iterable接口的类才可以使用迭代器和增强for，Collection接口已经实现了Iterable接口。

格式：

```java
for(元素数据类型 变量名：数组或者Collection集合){
	//在此处使用变量即可，该变量就是元素
}
```

##### 3Lambda表达式

Collection结合Lambda遍历的API

```java
default void forEach(Consumer<? super T> action)//结合lambda遍历集合,内部也有增强for循环，然后回调accept()
```

```java
Collection<String> lists = new ArrayList<>;
lists.forEach(new Consumer<String>()){
	@override
	piblic void accept(String s){
		System.out.println(S);
	}
}

lists.forEach(s->System.out.println(s));
lists.forEach(System.out::println);//简写上行
```

### 27常见数据结构

**栈**

**队列**

**数组**：查询快，增删慢

**链表：**

​		**单链表：**查询慢、增删快

​		**双链表：**增删首位元素最快，其他不好说

**二叉树：**

​		**二叉查找树（二叉排序树，二叉搜索树）：**左子树的值都小于根节点的值，右子树的值都大于根结点的值。**提高检索数据性能**

​																				 添加节点：小的存左边，大的存右边，一样的不存。**增删改查都挺快。**

​		**平衡二叉树：**在满足查找二叉树的大小规则下，让树尽可能矮小。以此提高查数据的性能。

​							   要求：**任意节点**的左右**两颗子树的高度差不超过1**，任意节点的左右子树都是一颗平衡二叉树。

​							   平衡二叉树添加元素后可能导致不平衡。基本策略是：**左旋，右旋**保证平衡

​		**红黑树：**是一种**自平衡的二叉查找树（**以前被称为二叉平衡B树），**每个节点多存出了一个颜色值，增删改查性能都好**

​						每一个节点可以是红或者黑；红黑树不是通过高度平衡的，而是通过红黑规则来实现。

​						**红黑规则：**每一个节点或是红色的，或者是黑色的**，根节点必须是黑色。**

​											如果一个节点没有子节点或者父节点，则该节点相应的指针属性值为Nil，**这些Nil视为叶节点，叶节点是黑色的**

​											如果某一个节点是红色，那么它的子节点必须是黑色（**不能出现两个红色节点相连的情况**）

​											**对每一个节点，从该节点到其所有后代叶节点的简单路径上，均包含相同数目的黑色节点**

​						**添加节点：**添加的节点的颜色，可以是红色的，也可以是黑色的，但是**默认红色效率高**，添加三个元素一共需要调整一次。



### 28List系列集合、集合的并发修改异常问题

List系列集合特点：Arraylist，LinekdList：有序可重复，有索引。

List集合特有方法：因为其支持索引，所以多了很多索引操作的独特api。其他collection的功能List也都继承了。

```java
void add(int index, E element)//在此列表中的指定位置插入指定元素（可选操作）。
```

```java
E remove(int index)//删除此列表中指定位置的元素（可选操作）。
```

```java
E set(int index, E element)//用指定的元素替换此列表中指定位置的元素（可选操作）。
```

```java
E get(int index)//返回此列表中指定位置的元素。
```

ArrayList底层是**基于数组**实现的，根据索引查询元素快，增删相对慢

LinkedList底层是**基于双链表**实现的，查询元素慢，增删首位元素是非常快的。

#### List集合的遍历方式：

1迭代器Iterator

2增强for循环

3Lambda表达式

4for循环（因为他存在索引）

#### ArrayList底层

是**基于数组**实现的，根据索引查询元素快，增删相对慢。

第一次创建集合并添加第一个元素的时候，在底层创建一个默认长度为10的数组。

用size()记录长度，如果超过了长度，扩容到原来的1.5倍。

#### LinkedList底层

是**基于双链表**实现的，查询元素慢，增删首位元素是非常快的。

所以多了很多首尾操作。

```java
void addFirst(E e)//push();在此列表的开头插入指定的元素。
```

```java
void addLast(E e)//offerLast();将指定的元素追加到此列表的末尾。
```

```java
E getFirst()//返回此列表中的第一个元素。
```

```java
E getLast()//返回此列表中的最后一个元素。
```

```java
E removeFirst()//pop();删除并返回此列表中的第一个元素。
```

```java
E removeLast()//删除并返回此列表中的最后一个元素。
```

LInkedList可以完成队列结构、栈结构（双链表）



#### 集合的并发修改异常问题(同时遍历且删除元素)

**只有普通for和迭代器可以解决！**

当我们从集合中找出某个元素并删除的时候可能出现一种并发修改异常问题。

**1（可解决）迭代器**遍历集合且使用集合删除元素的时候可能出现。

```java
List<String> list=new ArrayList();
Iterator<String> it=list.iterator();
while(it.hasNext()){
	String ele=it.next();
	if("Java".equals(ele)){
		//list.remove("Java");//此时删除元素会导致指针往前遍历！出错
		it.remove();//用迭代器删除当前所在元素，并且不会后移指针,会自己i--，成功遍历到所有元素
	}
}
```

**2（不可解决）增强for循环**遍历集合且直接用集合删除元素的时候可能出现。

```java
List<String> list=new ArrayList();
Iterator<String> it=list.iterator();
for(String s : List){
	if("Java".equals(s)){
		//list.remove("Java");//此时删除元素会导致指针往前遍历！出错【解决不了】
	}
}
```

**3（不可解决）Lambda表达式**也会出现，底层也是用的foreach

```java
List<String> list=new ArrayList();
list.foreach(s->{
    if("Java".equals(s)){
		//list.remove("Java");//此时删除元素会导致指针往前遍历！出错【解决不了】
	}
})
```

**4（可解决）普通for循环不会出现**，可以倒着循环或者自行i--



### **29泛型深入**

#### 泛型的概述和优势

jdk5引入特性，在编译阶段约束操作的数据类型，并进行检查。

只能支持引用数据类型。集合体系所有接口和实现类都支持泛型。

**优势：**统一数据类型，把运行时期的问题提前到了编译期间，避免了强制类型转换可能出现的异常，因为编译阶段类型就确定下来了。

类后面     -> 泛型类（Arraylist）

方法后面 -> 泛型方法

接口后面 -> 泛型接口（Collection）



#### 自定义泛型类

定义类的同时定义了泛型的类就是泛型类。

泛型类格式：

```java
修饰符 class 类名<泛型变量>{ }
public class MyArrayList<T>{ }//此处泛型变量T可以写成任意标识，常见的E,T,K,V
```

原理：把出现泛型变量的地方全部替换成传输的真实数据类型。



#### 自定义泛型方法

定义方法的同时定义了泛型的方法就是泛型方法。

泛型方法格式：

```java
修饰符 <泛型变量> 方法返回值 方法名(形参列表){ }
public <T> void show(T t){ }//此处泛型变量T可以写成任意标识，常见的E,T,K,V
```

作用：方法中使用泛型接受一切实际类型的参数，方法更具备通用性。

原理：把出现泛型变量的地方全部替换成传输的真实数据类型。



#### 自定义泛型接口

使用泛型定义的接口就是泛型接口。

泛型接口的格式：

```java
修饰符 interface 接口名称<泛型变量>{ }
public interface Date<T>//此处泛型变量T可以写成任意标识，常见的E,T,K,V
```

作用：泛型接口可以让**实现类选择当前功能需要操作的数据类型。**

原理：实现类可以在实现接口的时候传入自己操作的数据类型，这样重写的方法都将是针对于该类型的操作。



#### 泛型通配符、上下限

通配符：?

?可以在 **使用泛型** 的时候代表一切类型。比如在方法参数中使用泛型时

E T K V是在 **定义泛型** 的时候使用的。

虽然BMW BENZ都继承了Car，但是ArrayList<BMW>和ArrayList<BENZ>与ArrayList<Car>**没有关系**。！！

所以需要使用？通配符

例如：

```java
public static void go(Array<?> cars){
}
```

但是通配符会使所有类型都可以，所以加一个泛型上下限！

```java
?extends Car:
```

?必须是Car或者其子类 **泛型上限** **用得多**

```java
? super Car:
```

?必须是Car或者其父类 **泛型下限**

例如：

```java
public static void go(Array<? extends Car> cars){
    
}
```



### 30Set集合

#### **特点：**

无序：顺序不一致(第一次)

不重复：可以去除重复

无索引：没有带索引的方法，所以不能使用普通for循环遍历，也不能使用索引来获取元素。

**Set集合实现类特点：**

HashSet：无序、不重复、无索引

LinkeHashSet：**有序**、不重复、无索引。

TreeSet：**排序（默认升序）、**不重复、无索引

**Set集合的功能上基本与Collection的Api一致。**



#### HashSet元素无序的底层原理：哈希表

**HashSet底层原理**：

HashSet集合底层采取哈希表存储的数据。

哈希表是一种对于增删改查数据性能都较好的结构。

**哈希表的组成**：

jdk8之前：底层使用数组+链表组成

jdk8开始，底层采用数据+链表+红黑树组成。

**哈希值：**是jdk根据**对象的地址**，按照某种规则算出来的int类型的**数值。**

Object类的Api

```java
public int hashCode():返回对象的哈希值
```

**对象的hash值特点**：

同一个对象多次调用hashcode返回的哈希值是相同的

默认情况下，不同对象的哈希值是不同的。



**HashSet1.7版本原理解析**：**数组+链表+（结合hash算法）**

1，创建一个**默认长度16的数组**，默认加载因为0.75的数组，数组名table

2，根据元素的**hash值跟数组的长度求余**计算出应存入的位置（hash算法）

3，判断当前位**置是否为null**，如果是null直接存入

4，如果位置不为null，表示有元素，则调用**equals方法**比较

5，如果一样，则不存，如果不一样，则存入数组，

​		jdk7新元素占老元素的位置，指向老元素

​		jdk8新元素挂在老元素下面

6.当数组存到16*0.75=12时，会自动扩容，每次扩容为原先的两倍。

结论：hash表是一种对于**增删改查数据性能都较好**的结构。



**HashSet1.8开始原理解析**：**数组+链表+红黑树**

因为之前那种如果挂在元素下面的数据过多时，查询性能降低，所以jdk1.8开始，**当链表长度超过8的时候，会自动转换为红黑树！**

结论：进一步提高了增删改查性能



**hashSet判断去重**

是先判断哈希值（地址值转换而来），再判断equals()，所以如果要去重对象的话要**重写hashCode()、equals**()两个值。



#### LinkedHashSet集合

有序、不重复、无索引

这里的有序：保证存储和取出的元素顺序一致。

原理：底层数据结构依然是**哈希表**、只是每个元素又额外多了一个**双链表的机制记录存储的顺序**。



#### TreeSet集合

可排序，不重复、无索引

可排序：按照元素的大小默认升序（由小到大）排序！

TreeSet集合底层是基于**红黑树的数据结构**实现排序的，增删改查性能都比较好。

注意：TreeSet集合底层是**一定要排序的，可将元素按照指定的规则进行排序。**

**默认排序规则：**

对于**数值**类型：Integer，Double，官方默认按照**大小**进行升序排序。

对于**字符串**类型：默认按照**首字符的编号**(A65，a97)升序排序。

对于**自定义类型**如Student对象，TreeSet**无法直接排序**。(需要**自己制定排序规则**)

**自己制定排序规则**:

**方式一：**让自定义的类（如学生类）实现Comparable接口重写comparaTo方法来制定比较规则。

当两个值一样，只保留一个

如果想都保留：

```
public int compareTo(Apple o){
	return this.weight - o.weight >= 0 ? 1 : -1;
}
```

**方式二：**TreeSet集合有参构造器，可以设置Comparator接口对应的比较器对象，来指定比较规则。【常用，可简写->】

```java
TreeSet(Comparator<? super E> comparator)//构造一个新的空树集，根据指定的比较器排序。
```



### 31可变参数 ...

可变参数用在形参中可以接受多个数据。

**可变参数格式：数据类型...参数名称**

**可变参数的作用：**传输参数非常灵活，可以不传参，也可以传一个或多个，还可以传入一个数组。

```java
public static void sum(int...nums){
	//可变参数在方法内部本质上就是一个数组	
}
```

注意：一个形参列表中可变参数只能有一个；**可变参数必须放在形参列表的最后面。**



### 32Collections集合工具类

作用：Collections并不属于集合，是用来操作集合的工具类

```java
static <T> boolean addAll(Collection<? super T> c, T... elements)
```

将所有指定元素添加到指定集合。

```java
static void shuffle(List<?> list, Random rnd)
```

使用指定的随机性源随机排列指定的列表。【打乱List集合元素的排序】//Set本身就是无序，按照自己的规则无序的



排序方式：

```java
static <T extends Comparable<? super T>>void sort(List<T> list)
```

根据[自然排序]将指定列表按升序排序，如果要排序对象，必须实现Comparator接口并重写其比较方法。

```java
static <T> void sort(List<T> list, Comparator<? super T> c)
```

根据指定比较器产生的顺序对指定列表进行排序。





### 32Map集合

#### Map集合概述和使用

Map集合是一种双列集合，每个元素都包含两个数据。

Map集合的每个元素的格式：key=value（键值对元素）

Map集合也被称为键值对集合



collection集合的格式：[元素1，元素2，...]

Map集合的格式：{key1=value1, key2=value2,...}



#### Map集合体系特点

Map**（接口）**

​		HashMap**（实现类）**

​				LinkedHashMap**（实现类）**

​		HashTable**（实现类）**

​				Properties**（实现类）**

​		。。。**（接口）**

​				TreeMap**（实现类）**

使用最对的是HashMap

重点掌握HashMap，LinkedHashMap，TreeMap

Map集合**键无序、不重复、无索引的**，**值可以重复**

Map集合**后面**重复的键对应的值会**覆盖前面**重复键的值。

Map集合键值对都可以为null



#### Map集合实现类特点

HashMap：元素按照**键是无序**，不重复，无索引，值不做要求。（与Map体系一致）

LinkedHashMap：元素按照**键是有序**，不重复，无索引，值不做要求。

TreeMap：元素按照**键是排序**，不重复，无索引的，值不做要求。



#### Map集合常用Api

Map集合是双列集合的祖宗接口，它的功能是全部双列集合都可以继承使用的。

```java
V put(K key, V value)//添加元素，将指定值与此映射中的指定键相关联（可选操作）。
```

```java
V remove(Object key)//如果键存在，则从该映射中移除该键的映射（可选操作）。
```

```java
default boolean remove(Object key, Object value)//仅当指定键当前映射到指定值时，才删除该项。
```

```java
void clear()//从此映射中删除所有映射（可选操作）。
```

```java
boolean containsKey(Object key)//如果此映射包含指定键的映射，则返回“true”。
```

```java
boolean containsValue(Object value)//如果此映射将一个或多个键映射到指定值，则返回“true”。
```

```java
boolean isEmpty()//如果此映射不包含键值映射，则返回true。
```

```java
int size()//返回此映射中键值映射的数量。
```

```java
Collection<V> values()//返回此映射中包含的值的集合视图。
```

```java
Set<K> keySet()//返回此映射中包含的键的Set视图。
```

```java
void putAll(Map<? extends K,? extends V> m)//把map2的元素拷贝一份到map1中去
```



#### Map集合的遍历方式

##### 键找值：

先获取Map集合的全部键的Set集合。**KeySet()**方法

遍历键的Set集合，然后通过提取对应值。**get()**方法



##### 键值对：

先把Map集合转换成Set集合，Set集合中每个元素都是键值对实体类型了。**entrySet()**

```java
Set<Map.Entry<K,V>> entrySet()//返回此映射中包含的映射的Set视图。
```

遍历Set集合，然后提取键以及提取值。**getKey(), getValue();**

**原因**：使用foreach遍历map集合，发现Map集合的键值对元素是没有类型的，所以不可以直接foreach遍历map集合。

通过调用Map的方法entrySet把Map集合转换成Set集合形式。

```java
Set<Map.Entry<String,Integer>> entries = [(手表,10),(手机,20),(电视,89)]
```

此时就可以用foreach了。



##### lambda表达式：

Map结合Lambda遍历的API，内部也是使用entrySet()

```java
default void forEach(BiConsumer<? super K,? super V> action)//遍历Map集合，为此映射中的每个条目执行给定的操作，直到处理完所有条目或该操作引发异常。
```

```java
maps.forEach((k,v)->{
	System.out.println(k+"->"+v);
})
```



### 33 Map集合的实现类

#### HashMap

直接使用Map的方法就好

**HashMap和HashSet底层原理是一模一样**的，都是Hash表结构，只是HashMap的每个元素包含两个值

Set系列集合底层就是Map，只是Set集合中元素只要键数据，不要值数据而已。

HashMap底层是哈希表结构，依赖hashCode和equals方法保证键的唯一。

如果键是存的自定义对象，需要重写hashCode和equals方法。

基于哈希表增删改查都挺好



#### LinkedHashMap

原理：底层数据结构依然是哈希表，只是对每个键值对元素又额外的多了一个**双链表的机制**记录存储的顺序。



#### TreeMap

按照键排序；

TreeMap一定要排序的，可以默认排序，也可以按照指定规则排序。

**TreeMap和TreeSet一样底层原理是一样的**



自定义排序规则有两种：

类实现Comparable接口，重写比较规则。

集合自定义Comparator比较器对象，重写比较规则。



### 34不可变集合

不可变集合：不可被修改的集合

集合数据项在创建时提供，**并且在整个生命周期中都不可改变**。否则报错。

如果某个数据不能被修改，把他防御性拷贝到不可变集合中是个很好的实践。

或者当集合对象被不可信的库调用时，不可变形式是安全的

在List、Set、Map接口中，都存在of方法，可以创建一个不可变的集合。

```java
static <E> List<E> of(E... elements);//创建一个具有指定元素的List集合，返回包含任意数量元素的【不可修改列表。】
static <E> Set<E> of(E... elements);//创建一个具有指定元素的Set集合，返回包含任意数量元素的【不可修改集合。】
static <K,V> Map<K,V> of(E... elements);//创建一个具有指定元素的Map集合，返回包含任意数量元素的【不可修改映射。】
```

```java
List<Double> lists = list.of(569.5,434,557);
```



### 35Stream流

在java8中，得益于Lambda所带来的函数式编程，引入了一个全新的stream流概念。

**目的：简化集合和数组操作的API**

eg:

```java
names.stream().filter(s->s.startWith("张")&&s->s.length()==3).forEach(s->System.out.println(s));
```

Stream流的三类方法：

**获取stream流**：

创建一条流水线，并把数据放到流水线上准备进行操作。

**中间方法**：

流水线上的操作

**终结方法：**

一个Stream流只有一个终结方法，是流水线上的最后一个操作。



**获取stream流**：

集合：

```java
default Stream<E> stream()//返回以该集合为源的连续“流”。
```

arraylist:

```java
Collection<String> list=new ArrayList<>();
Stream<String> s=list.stream();
```

map:

```java
Map<String,Integer> maps= new HashMap<>();
//键流
Stream<String> keyStream=maps.keySet().stream();
//值流
Stream<Integer> valueStream=maps.values().stream();
//键值对流
Stream<Map.Entry<String,Integer>> keyAndValueStream=maps.entrySet().stream();
```

数组：

```java
static <T> Stream<T> stream(T[] array)//返回一个以指定数组为源的连续Stream。
```

```java
static <T> Stream<T> stream(T[] array, int startInclusive, int endExclusive)//返回以指定数组的指定范围为源的连续Stream。
```

```java
static <T> Stream<T> of(T... values)//获取当前数组的Stream，可变数据的Stream
```

 eg:

```java
String[] names={"ac","sa","sas"};
Stream<String> nameStream =Arrays.stream(names);

Stream<String> nameStream2=Stream.of(names)
```



**中间方法：**（非终结方法，调用完返回新的stream流方法可以继续使用，支持链式编程，不会改变原来集合、数组的数据）

```java
Stream<T> limit(long maxSize)//获取前几个元素
```

```java
<R> Stream<R> map(Function<? super T,? extends R> mapper)//返回一个流，该流由将给定函数应用到此流的元素的结果组成。
```

```java
Stream<T> skip(long n)//跳过前几个元素
```

```java
Stream<T> distinct()//去除流中重复的元素，依赖（hashcode和equals方法）
```

```java
static <T> Stream<T> concat(Stream<? extends T> a, Stream<? extends T> b)//合并ab两个流为一个流
```

```java
Stream<T> filter(Predicate<? super T> predicate)//用于过滤流中的数据
```



**终结方法：（ 不会返回stream流了）**

```java
long count()//返回此流中的元素数
```

```java
void forEach(Consumer<? super T> action)//对流每个元素遍历操作
```



#### stream的收集操作

把Stream流操作后的结果数据转回到集合或者数组中去。

stream流：方便操作集合、数组的手段。

集合、数组：才是开发中的目的。

**流只能收集一次。**

```java
List<String> mylist=s1.collect(Collectors.toList());
//有直接的toList()方法，但是是转换成了不可变集合
```

```java
Set<String> mylist=s1.collect(Collectors.toSet());
```

收到数组中：

```java
Object[] arrs= s3.toArray();
//如果要指定数组类型
String[] arrs=s3.toArray(s->new String[s])
```



### 36异常

是在执行和编译过程中可能出现的问题，注意：语法错误不算。

比如数组索引越界，空指针异常，日期格式化异常。



#### 异常体系：

**Throwable:**



​		**Error：**系统级别问题，jvm退出等，代码无法控制。



​		**Exception：**java.lang包下，称为异常类，他表示程序本身可以处理的问题。



​				**RuntimeException及其子类**：**运行时异常**（运行字节码文件  ），编译阶段不会报错。（空指针，数组索引越界）



​				**除RuntimeException之外的所有异常**：**编译时异常**（编译成class文件时），编译器必须处理，否则程序不能通过编译。（日期格式化异常）



#### 默认异常处理机制：（并不好，程序死亡）

默认会在出现异常的代码那里自动的创建一个异常对象：ArithmeticException。

异常会从方法中出现的点这里抛出给调用者，调用者最终会抛出给JVM虚拟机

虚拟机收到异常对象后，先在控制台直接输出异常栈信息数据。

直接从当前执行的异常点干掉当前程序。

后续代码没有执行机会了，程序已经死亡。



#### 编译时异常处理机制

处理形式有三种

1.**出现异常直接抛出给调用者，调用者也抛出去**。



**throws：**用在方法上，可以将方法内部出现的异常抛出去给本方法的调用者处理。

（并不好，发生异常的方法自己不处理异常，如果出现异常最终抛出去给虚拟机将引起程序死亡。）

格式：

```java
方法 throws 异常一,异常二,异常三..{

}
```

规范做法：

```java
方法 throws Exception{

}
```



**2.出现异常自己捕获处理，不麻烦别人。**



**try...catch...finally**

监视捕获异常，用在方法内部，可以将方法内部出现的异常直接捕获处理。

（还可以，发生异常的方法自己独立完成异常的处理，程序可以继续往下执行。）

格式：

```java
try{
//监视可能出现异常的代码
}catch(异常类型1 变量){
//处理异常
}catch(异常类型2 变量){
//处理异常
}
```

建议格式：

```java
try{
//监视可能出现异常的代码
}catch(Exception e){
  e.printStackTrace();
}finally{
    //即使前面return了这里也会执行，所以不要在这里return，会覆盖前面的return。除非前面exit(0)终止jvm
}
Exception可以捕获处理一切异常类型
```



**3.前两者结合，出现异常直接抛出给调用者，调用者捕获处理。**

方法直接将异常throws抛出去给调用者。

调用者收到异常后直接捕获处理。

（按照开发规范来说是最好的方式，底层的跑出去给外层，最外层集中捕获处理，实际上每一种抛出异常方法都行。）



#### 运行时异常处理机制

在最外层集中处理捕获，底层不需要我们throws，会自动抛出异常的。



#### 自定义异常

如果企业要通过异常的方式来管理自己的某个业务问题，就需要自定义异常类了。



好处：使用异常机制管理，清晰指出错误。



##### **1自定义编译时异常**

a定义一个异常类继承Exception

b重写构造器

c在出现异常的地方用throw new自定义对象抛出。

（编译时异常是编译阶段就报错，提醒更加强烈，一定需要处理）

throw：在方法内部直接创建一个异常对象，并从此点抛出；

throws：用在方法申明上，抛出方法内部的异常

##### 2自定义运行时异常

a定义一个异常类继承RuntimeException

b重写构造器

c在出现异常的地方用throw new自定义对象抛出。

（运行时异常是编译阶段不报错，运行时才可能出现）



### 37日志框架

记录程序运行的信息，并可以永久存储。

可以将系统执行的信息选择性记录到指定的位置

可以随时以开关形式控制是否记录日志，无需修改源代码。

#### Logback日志框架

https://logback.qos.ch/index.html

主要分为三个技术模块：

logback-core：为其它两个模块奠定了基础，必须有

logback-classic：是log4j的一个改良版本，同时完整实现了slf4jApi

logback-access模块与Tomcat和jetty等servlet容器集成，以提供http访问日志功能



```java
public class Test {
//    1将项目文件下新建lib，导入logback相关jar包，并添加到依赖库中去
//    2将logback的核心配置文件logback.xml直接拷贝到src目录下（必须是src下）
//    3在代码中获取日志的对象
//    4使用日志对象输出日志信息
    
    //创建logback日志对象，代表了日志技术
    public static final Logger LOGGER= LoggerFactory.getLogger(Test.class);
    public static void main(String[] args) {
        try{
            LOGGER.debug("main开始");
            LOGGER.info("第二行");
            int a =10;
            int b=0;
            LOGGER.trace("a="+a);
            System.out.println(a / b);
        }catch(Exception e){
            e.printStackTrace();
            LOGGER.error("出现异常"+e);
        }

    }
}
```



logback日志系统的特性都是通过核心配置文件logback.xml控制的。

**logback日志输出位置、格式设置：**

通过logback.xml中的<append>标签可以设置**输出位置和日志信息的详细格式**。

通常可以设置2个日志输出位置：一个是控制台，一个是系统文件中



日志级别：

控制系统中那些日志级别是可以输出的，TRACE<DEBUG< INFO< WARN< ERROR，默认级别是Debug**，只输出不低于当前级别的日志。**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <!--
        CONSOLE ：表示当前的日志信息是可以输出到控制台的。
    -->
    <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
        <!--输出流对象 默认 System.out 改为 System.err-->
        <target>System.out</target>
        <encoder>
            <!--格式化输出：%d表示日期，%thread表示线程名，%-5level：级别从左显示5个字符宽度
                %msg：日志消息，%n是换行符-->
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%-5level]  %c [%thread] : %msg%n</pattern>
        </encoder>
    </appender>

    <!-- File是输出的方向通向文件的 -->
    <appender name="FILE" class="ch.qos.logback.core.rolling.RollingFileAppender">
        <encoder>
            <pattern>%d{yyyy-MM-dd HH:mm:ss.SSS} [%thread] %-5level %logger{36} - %msg%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!--日志输出路径-->
        <file>C:/Users/方前林/Desktop/java基础学习/itheima-data.log</file>
        <!--指定日志文件拆分和压缩规则-->
        <rollingPolicy
                class="ch.qos.logback.core.rolling.SizeAndTimeBasedRollingPolicy">
            <!--通过指定压缩文件名称，来确定分割文件方式-->
            <fileNamePattern>C:/Users/方前林/Desktop/java基础学习/fql-data2-%d{yyyy-MMdd}.log%i.gz</fileNamePattern>
            <!--文件拆分大小-->
            <maxFileSize>1MB</maxFileSize>
        </rollingPolicy>
    </appender>

    <!--

    level:用来设置打印级别，大小写无关：TRACE, DEBUG, INFO, WARN, ERROR, ALL 和 OFF
   ， 默认debug
    <root>可以包含零个或多个<appender-ref>元素，标识这个输出位置将会被本日志级别控制。
    -->
    <root level="ALL">
        <appender-ref ref="CONSOLE"/>
        <appender-ref ref="FILE" />
    </root>
</configuration>
```



### 38文件操作

#### File概述

File类可以定位文件：进行删除、获取文本本身信息等操作。但是不能读写文件内容。

IO流技术可以对硬盘中的文件进行读写。



File类创建对象

```java
File(File parent, String child)//根据父路径对应文件对象和子路径名字字符串创建文件对象
```

```java
File(String pathname)//根据文件路径创建文件对象
```

```java
File(String parent, String child)//跟据父路径名字字符串和子路径名字符串创建文件对象
```

```java
File(URI uri)//通过将给定的File:URI转换为抽象路径名来创建一个新的File实例。
```



```java
File f= new file("C:\\data.jpg");
long size=f.length();//是文件的字节大小
system.out.println(size);
```

File对象可以**定位文件和文件夹**

File封装好的对象仅仅是一个**路径名**，这个路径是可以存在的，也可以是不存在的。



绝对路径

相对路径：默认到当前工程下的目录寻找文件

```java
File file3 = new File("模块名\\a.txt")
```



#### File类的常用Api

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/io/File.html#method-summary

**判断文件类型**

```java
boolean isDirectory()//判断是否为文件夹
```

```java
boolean isFile()//是否为文件
```

```java
boolean exists()//判断file是否存在
```

**获取文件信息**

```java
String getAbsolutePath()//返回绝对路径字符串
```

```java
String getPath()//将此抽象路径名转换为路径名字字符串
```

```java
String getName()//返回由此抽象路径名表示的文件或文件夹的名称
```

```java
long lastModified()//返回文件最后修改的时间毫秒值
```

**创建文件**

```java
boolean mkdir()//只能创建一级文件夹
```

```java
boolean mkdirs()//可以创建多级文件夹
```

```java
boolean createNewFile()//创建一个新的空文件
```

**删除文件功能**

```java
boolean delete()//删除由此抽象路径名表示的文件或空文件夹
```

```java
void deleteOnExit()//请求在虚拟机终止时删除此抽象路径名表示的文件或目录。
```

delete方法直接删除不走回收站；如果删除的是文件，文件被占用也可以删除。

delete方法默认只能删除空文件夹。

**遍历文件夹**

```java
String[] list()//获取当前目录下所有的“一级文件名称”到一个字符串数组中去返回。
```

```java
File[] listFiles()//获取当前目录下所有的“一级文件对象”到一个文件对象数组中去返回。【常用】
```

listFiles注意：

当调用者不存在时，返回null

当调用者是一个文件时，返回null

当调用者是一个空文件夹时，返回一个长度为0的数组

当调用者是一个有内容的文件夹时，将里面所有文件和文件夹的路径放在File数组中返回。

当调用者是一个有隐藏文件的文件夹时，将里面所有文件和文件夹的路径放在file数组中返回，包含隐藏内容

当调用者是一个需要权限才能进入的文件夹时，返回null



### 39IO流

#### 字符集

英文和数字在任何字符集都占一个字节

gbk字符中一个中文占2字节

utf-8一个中文占3字节

编码前的字符集和编码后字符集必须一致，否则会出现字符乱码。

英文和数字在任何字符集都不会乱码

#### String解码

字节转换成文字

构造器

```java
String(byte[] bytes)//通过使用平台的默认字符集解码指定的字节数组来构造新的String
```

```java
String(byte[] bytes, String charsetName)//通过指定的字符集解码指定的字节数组来构造新的String
```

#### String编码

把文字转换成字节

方法

```java
byte[] getBytes()//使用默认字符集将该String编码为一系列字节，将结果存储到新的字节数组中
```

```java
byte[] getBytes(String charsetName)//使用指定字符集将该String编码为一系列字节，将结果存储到新的字节数组中
```

#### IO流

也称为输入输出流，就是用来读写数据的。

I：表示input，是数据从硬盘文件**读入到内存**的过程，称之输入，负责读。

O：表示output，是内存程序的数据**从内存到写出**到硬盘文件的过程，称之输出，负责写。

按流中数据最小单位分：

字节流：操作所有类型文件，例如音视频

字符流：操作纯文本文件，例如文本

#### 四大流：(抽象类:实现类)

字节输入流：以内存为基准，来自磁盘、网络的数据以字节形式读入到内存中去。**InputStream**：FileInputStream

字节输出流：以内存为基准，内存的数据以字节形式写出到磁盘、网络中去。**OutputStream**:FileOutputStream

字符输入流：以内存为基准，来自磁盘、网络的数据以字符形式读入到内存中去。**Reader**:FileReader

字符输出流：以内存为基准，内存的数据以字符形式写出到磁盘、网络中去。**Writer**:FileWriter



#### FileInputStream

```java
FileInputStream(File file)//通过打开与实际文件的连接来创建“FileInputStream”，该文件由文件系统中的“file”对象“file”命名
```

```java
FileInputStream(FileDescriptor fdObj)//使用文件描述符“fdObj”创建“FileInputStream”，该描述符表示与文件系统中实际文件的现有连接。
```

```java
FileInputStream(String name)//创建字节输入流管道与原文件路径接通
```

```java
int read()//每次读取一个字节返回，如果字节已经没有可读的返回-1
```

```java
int read(byte[] b)//每次读取一个字节数组返回，如果字节已经没有可读的返回-1
```

这种读取容易造成乱码，建议一次性读完所有字节：readAllBytes()，但是文件过大定义的字节数组可能会出现内存溢出。

#### FileOutputStream

```java
FileOutputStream(File file)//创建字节输出流管道与源文件对象接通，每次重新创建会清空
```

```java
FileOutputStream(File file, boolean append)//创建字节输出流管道与源文件对象接通，可追加数据
```

```java
FileOutputStream(String name)//创建字节输出流管道与源文件路径接通
```

```java
FileOutputStream(String name, boolean append)////创建字节输出流管道与源文件路径接通，可追加数据
```

```java
void write(byte[] b)//写一个字节数组出去
```

```java
void write(byte[] b, int off, int len)//写一个字节数组出去的一部分出去
```

```java
void write(int b)//写一个字节出去
```

**流的关闭与刷新**

flush()刷新流，还可以继续写数据

close()关闭流，释放资源，但是在关闭之前会先刷新流。一旦关闭就不能再写数据

**案例：拷贝文件**:

1根据数据源创建字节输入流对象

2根据目的地创建字节输出流对象

3读写数据，复制视频

4释放资源

```java
package com.xfzy.filecopy;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class Copydemo {
    public static void main(String[] args) {
        InputStream is=null;
        OutputStream os=null;
        try{
            //1根据数据源创建字节输入流对象
            is =new FileInputStream("C:\\Users\\方前林\\Desktop\\java基础学习\\code\\javasepromax\\filecopy\\家庭情况证明.jpg");
            //2根据目的地创建字节输出流对象
            os =new FileOutputStream("C:\\Users\\方前林\\Desktop\\java基础学习\\new.jpg");
            //3读写数据，复制视频
            byte[] buffer = new byte[1024];
            int len;//记录每次的字节数
            while((len=is.read(buffer))!=-1){
                os.write(buffer,0,len);
            }
            System.out.println("复制完成");

        }catch(Exception e){
            e.printStackTrace();
        }finally{
            //4关闭流释放资源
            try {
                if(os!=null) os.close();
            }catch (Exception e){
                e.printStackTrace();
            }
            try {
                if(is!=null) is.close();
            }catch (Exception e){
                e.printStackTrace();
            }
        }
    }
}
```

**字节流适合做一切文件数据拷贝。但不适合中文输出**

#### 简化资源释放操作

```java
try{
//监视可能出现异常的代码
}catch(Exception e){
  e.printStackTrace();
}finally{
	//执行所有资源释放操作
    //即使前面return了这里也会执行，所以不要在这里return，会覆盖前面的return。除非前面exit(0)终止jvm
}
```

###### jdk7:

```java
try(定义流对象){
//监视可能出现异常的代码
}catch(Exception e){
}
```

资源用完最终自动释放。

```java
package com.xfzy.filecopy;

import java.io.FileInputStream;
import java.io.FileOutputStream;
import java.io.InputStream;
import java.io.OutputStream;

public class Copydemo {
    public static void main(String[] args) {
        //1根据数据源创建字节输入流对象
        //2根据目的地创建字节输出流对象
        try(InputStream is =new FileInputStream("C:\\Users\\方前林\\Desktop\\java基础学习\\code\\javasepromax\\filecopy\\家庭情况证明.jpg");
            OutputStream os =new FileOutputStream("C:\\Users\\方前林\\Desktop\\java基础学习\\new.jpg");
            ){
            //3读写数据，复制视频
            byte[] buffer = new byte[1024];
            int len;//记录每次的字节数
            while((len=is.read(buffer))!=-1){
                os.write(buffer,0,len);
            }
            System.out.println("复制完成");

        }catch(Exception e){
            e.printStackTrace();
        }
    }
}

```

###### jdk9:不建议使用

```java
定义输入流对象;
定义输出流对象;
try(输入流对象，输出流对象){
//监视可能出现异常的代码
}catch(Exception e){
}
```

资源用完最终自动释放。

###### 资源用完最终自动释放的原因

实现了AutoCloseable接口



#### FileReader

字符输入流，每次读取一个字符时，如果代码和文件编码一致，则不会出现乱码。

构造器:

```java
public FileReader(File file);//创建字符输入流管道与源文件对象接通
```

```java
public FileReader(String pathname);//创建字符输入流管道与源文件路径接通
```

方法：读取字符

```java
public int read()//每次读取一个字符返回，如果字符已经没有可读的返回-1
```

```java
public int read(char[] buffer)//每次读取一个字符数组返回，返回读取字符个数，如果字符已经没有可读的返回-1
```



#### FileWriter

构造器：

```java
public FilWriter(File file);//创建字符输出流管道与源文件对象接通
```

```java
public FilWriter(File file,boolean append);//创建字符输出流管道与源文件对象接通,可追加
```

```java
public FilWriter(String filepath);//创建字符输出流管道与源文件路径接通
```

```java
public FilWriter(String filepath,boolean append);//创建字符输出流管道与源文件路径接通,可追加
```

方法：

```java
void write();//可以写字符，字符数组，字符数组的一部分，字符串，字符串的一部分
```



### 40、IO流（二）

#### 缓冲流

缓冲流也称为高级流，高效流。之前字节流称为原始流。

**作用：缓冲流自带缓冲区、可以提高原始字节流、字符流读写数据的性能。**

字节缓冲流优化原理：

字节缓冲输入流自带了8kb缓冲池，以后我们可以直接从缓冲池读取数据，所以性能好。

字节缓冲输出流自带了8kb缓冲池，数据就直接写入到缓冲池中去，写数据性能级高了。

功能没有太大变化，都是继承的字节输入流InputStream，OutputStream



##### BufferedInputStream字节缓冲输入流

构造器

```java
BufferedInputStream(InputStream in)//把低级的字节输入流包装成一个高级的缓冲字节输入流管道，从而提高字节输入流读数据的性能
```

```java
BufferedInputStream(InputStream in, int size)//创建一个具有指定缓冲区大小的BufferedInputStream，并将其参数输入流保存在中，以备日后使用。
```



##### BufferedOutputStream字节缓冲输出流

```java
BufferedOutputStream(OutputStream os)//把低级的字节输出流包装成一个高级的缓冲字节输出流管道，从而提高写数据的性能
```



##### BufferedReader字符缓冲输入流

提高字符输入流读取数据的性能，除此之外多了**按照行读取数据**的功能。

构造器：

```java
BufferedReader(Reader in)//可以把低级的字符输入流包装成一个高级的缓冲字符输入流管道，从而提高字符输入流读数据的性能
```

新增功能：

```java
String readLine()//读取一行数据返回，如果读取没有完毕，无行可读返回null
```



##### BufferedWriter字符缓冲输出流

构造器：

```java
BufferedWriter(Writer out)//可以把低级的字符输出流包装成一个高级的缓冲字符输出流管道，从而提高字符输出流写数据性能
```

新增方法：

```java
public void newLine()//换行操作
```



#### 转换流

字符流直接读取文本时，如果代码编码和读取的文件编码不一致，会出现乱码。

解决：**使用字符输入转换流:**

可以**提取文件gbk的原始字节流**，原始字节不会存在问题。

然后把**字节流以指定编码转换成字符输入流**，这样字符输入流中的字符就不乱码了



##### InputStreamReader：字符输入转换流

把原始字节流按照指定编码转换成字符输入流。

构造器：

```java
InputStreamReader(InputStream in, String charsetName)//把原始字节流转换成字符输入流
```



##### OutputStreamWrite：字符输出转换流

需要控制写出去的字符使用的编码：

把字符以指定编码获取字节后再使用字节输出流写出去："我爱你中国".getBytes(编码)

也可以使用字符输出转换流实现。

构造器：

```java
OutputStreamWriter(OutputStream out, String charsetName)//指定编码把字节输出流转换成字符输出流，从而可以指定写出取得字符编码。
```

#### 序列化对象

以内存为基准，把**内存中的对象存储到磁盘文件中去**，称为**对象序列化**。

使用的流是**对象字节输出流**：ObjectOutputStream

构造器

```java
ObjectOutputStream(OutputStream out)//把低级字节输出流包装成高级的对象字节输出流。
```

方法：

```java
final void writeObject(Object obj)//把对象写出去到对象序列化流的文件中去
```

**对象如果要序列化:必须先实现Serializable序列化接口。**

1创建对象

2对象序列化：使用对象字节输出流包装字节输出流管道。

3直接调用序列化方法，weriteObject(类)

4释放资源close



以内存为基准，把**存储到磁盘文件中去的对象数据恢复成内存中的对象**，称为**对象反序列化**

使用的是**对象字节输入流**：ObjectInputStream

构造器：

```java
ObjectInputStream(InputStream in)//把低级字节输入流包装成高级的对象字节输入流
```

方法：

```java
final Object readObject()//把存储到磁盘文件中的对象数据恢复成内存中的对象返回
```



##### 敏感字段不参与序列化-transient：

注意：如果有成员变量不参与序列化，例如密码，可以在成员变量之前加上修饰符**transient**

##### 版本号:

申明序列化版本号，序列化版本号与反序列版本号必须一致才不会出错。

```java
private static final long serialVersionUID=1;
```



#### 打印流

可以实现方便高效的打印数据到文件中去，打印流一般是指：PrintStream，PrintWrite两个类。

可以实现打印什么就是什么。

##### PrintStream字节输出流

构造器：

```java
PrintStream(OutputStream out)//打印流直接通向字节输出流管道
```

```java
PrintStream(File file)//打印流直接通向文件对象
```

```java
PrintStream(String fileName)//打印流直接通向文件路径
```

方法：

```java
void print()
void println()
```

##### PrintWriter字符输出流

构造器：

```java
PrintWriter(OutputStream out)//打印流直接通向字节输出流管道
PrintWriter(Writer out)//打印流直接通向字符输出流管道
```

```java
PrintWriter(File file)//打印流直接通向文件对象
```

```java
PrintWriter(String fileName)//打印流直接通向文件路径
```

方法：

```java
void print()
void println()
```

##### 

**如果要追加数据，必须使用低级管道的构造器。**



##### 他俩区别：

打印上没有区别，都是使用方便

**PrintStream继承自字节输出流OutputStream**，支持写字节数据的方法

**PrintWriter继承自字符输出流Writer**，支持写字符数据出去。



##### 输出语句重定向：

属于打印流的一种应用，可以把**输出语句的打印位置改到文件。**

```java
PrintStream = new PrintStream("文件地址")
System.setOut(ps)//把系统打印流改成我们自己的打印流
```



#### Properties属性集对象

其实就是一个map集合，但是我们一般不会当集合使用，因为HashMap更好用。



**properties核心作用**：

代表的是一个属性文件，可以把自己对象中的键值对信息存储到一个属性文件中去。

属性文件：后缀是**.properties结尾**的文件，**里面内容都是key=value，后续做系统配置信息的**。



Peoperties结合IO流的方法：

```java
void load(InputStream inStream)//从输入字节流读取属性列表（键和元素对）
```

```java
void load(Reader reader)//从输入字符流读取属性列表（键和元素对）
```

```java
void store(OutputStream out, String comments)//将此属性列表（键和元素对）写入此Properties表中，以适合用load(InputStream)方法的格式写入输出字符流
```

```java
void store(Writer writer, String comments)//将此属性列表（键和元素对）写入此Properties表中，以适合用load(reader)方法的格式写入输出字符流
```

```java
Object setProperty(String key, String value)//保存键值对（put）
```

```java
String getProperty(String key)//使用此属性列表中指定的键搜索属性值
```

```java
Set<String> stringPropertyNames()//所有键的名称合集
```



#### IO框架 commons-io

第三方工具包，提供了很多有关io操作的类，有两个主要的类FileUtils，IOUtils

**导入commins-io-2.6.jar**

1在项目中创建一个文件夹lib

2将jar文件复制到lib

3在jar文件右键Add as Library->OK

4在类中导包使用

##### FileUtils

方法：

```java
String readFileToString(File file,String encoding)//读取文件数据，返回字符串
void copyFile(File src,File dest)//复制文件
void copyDirectoryToDirectory(File src,File dest)//复制文件夹
```



##### NIO : public final class **Files**

java1.7开始自己也做了相关类api

https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/nio/file/Files.html#method-summary



### 41线程

线程thread是一个程序内部的一条执行路径。

我们之前启动程序执行后，main方法的执行其实就是一条单独的执行路径。

程序中如果只有一条执行路径，那么这个程序就是**单线程**的程序。

**多线程**：是从**软硬件上实现多条执行流程**的技术。



#### 多线程的创建

##### 一、继承Thread类

1定义一个子类MyThread继承线程类Java.lang.Thread，重写run()方法

2创建MyThread类的对象

3调用线程对象的start()方法启动线程（启动后还是执行run方法的）

```java
package com.xfzy.d1_creat;

public class ThreadDemo01 {
    public static void main(String[] args) {
        //3 new一个新线程对象
        Thread t =new MyThread();
        //4 调用start方法启动线程（执行的还是run）
        t.start();//告诉操作系统以线程方式启动run方法，直接run会认为是普通方法。
        for(int i=0;i<5;i++){
            System.out.println("主线程执行输出"+i);
        }
    }
}

/**
 * 1 定义一个线程类继承Thread类
 */
class MyThread extends Thread{
    /**
     * 2 重写run方法，里面是定义线程以后要干啥
     */
    @Override
    public void run() {
        for(int i=0;i<5;i++){
            System.out.println("子线程执行输出"+i);
        }
    }
}

```

**优缺点：**

1.只能继承一个Thread类，无法继承其他类，不利于扩展。

2.编码简单。

**注意：**

1为什么不直接调用run而用start：

t.start();//告诉操作系统以线程方式启动run方法，直接run会认为是普通方法。

2把主线程任务放在子线程任务t.start();之后：

不然会先跑完主线程，没起到多线程的作用。



##### 二、实现Runnable接口

1定义一个线程任务类MyRunnable实现Runnable()接口，重写run()方法

2创建MyRunnable任务对象

3把MyRunnable任务对象交给Thread处理

4调用线程对象的start()方法启动线程（启动后还是执行run方法的）

**Thread构造器：**

```java
Thread(Runnable target)//封装Runnable对象为线程对象
Thread(Runnable target, String name)//封装Runnable对象为线程对象，并指定线程名称
Thread(String name)//可以为当前线程指定名称
```

```java
package com.xfzy.d1_creat;

public class ThreadDemo02 {
    public static void main(String[] args) {
        //2创建MyRunnable任务对象
        Runnable target = new myRunnable();
        //3把MyRunnable任务对象交给Thread处理
        //4调用线程对象的start()方法启动线程（启动后还是执行run方法的）
        new Thread(target).start();
        for(int i=0;i<5;i++){
            System.out.println("主线程执行输出"+i);
        }
    }
}

/**
 * 1定义一个线程任务类MyRunnable实现Runnable()接口，重写run()方法
 */
class myRunnable implements Runnable{
    @Override
    public void run() {
        for(int i=0;i<5;i++){
            System.out.println("子线程执行输出"+i);
        }
    }
}
```

**方式二匿名内部类写法**：

```java
package com.xfzy.d1_creat;

public class ThreadDemo02 {
    public static void main(String[] args) {
        //1线程任务类MyRunnable实现Runnable()接口，重写run()方法
        //2创建MyRunnable任务对象
//        Runnable target = new Runnable() {
//            @Override
//            public void run() {
//                for(int i=0;i<5;i++){
//                    System.out.println("子线程执行输出"+i);
//                }
//            }
//        };
//        //3把MyRunnable任务对象交给Thread处理
//        //4调用线程对象的start()方法启动线程（启动后还是执行run方法的）
//        new Thread(target).start();
        //3把MyRunnable任务对象交给Thread处理
        //4调用线程对象的start()方法启动线程（启动后还是执行run方法的）
        new Thread(()->{
                for(int i=0;i<5;i++){
                    System.out.println("子线程执行输出"+i);
                }
            }
        ).start();
        for(int i=0;i<5;i++){
            System.out.println("主线程执行输出"+i);
        }
    }
}

```



**优缺点：**

优点：线程任务类只是实现接口，可以继续继承类和实现接口，扩展性强

缺点：编程多一层对象包装，如果线程有执行结果是不可以直接返回的【只能跑功能】。



##### 三、JDK5新增：实现Callable接口，结合FutureTask类

前两种方法run方法都不能返回结果，不适合做有线程返回结果的业务场景

解决：jdk5提供了Callable和FutureTask来实现

1得到任务对象：

定义类实现Callable接口，重写call方法，封装要做的事情。

用FutureTask把Callable对象封装成线程任务对象。

2把线程任务对象交给Thread处理

3调用Thread的start方法启动线程，执行任务

4线程执行完毕后，通过FutureTask的get方法去获取任务执行的结果

Future构造器

```java
FutureTask(Callable<V> callable)//把Callable任务对象封装成FutureTask线程任务对象
```

API

```java
V get() throws Exception//获取线程执行call方法返回的结果
```

例如：

```java
package com.xfzy.d1_creat;

import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

public class ThreadDemo03 {
    public static void main(String[] args) {
        //3创建Callable任务对象
        Callable<String> call=new MyCallable(100);
        //4用FutureTask把Callable对象封装成线程任务对象。
        //      Future对象是Runnable的对象（实现了Runnable其接口），可以交给Thread了
        //      可以在线程执行完毕之后通过调用其get方法得到线程执行完成的结果
        FutureTask<String> f1=new FutureTask<>(call);
        //5交给线程处理
        Thread t1 = new Thread(f1);
        //6启动线程
        t1.start();


        Callable<String> call2=new MyCallable(200);
        FutureTask<String> f2=new FutureTask<>(call2);
        Thread t2 = new Thread(f2);
        t2.start();

        try {
            //如果f1任务没有执行完毕，这里的代码会等待，直到线程一跑完才提取结果
            String s1=f1.get();
            System.out.println("第一个结果"+s1);
            //如果f2任务没有执行完毕，这里的代码会等待，直到线程二跑完才提取结果
            String s2=f2.get();
            System.out.println("第二个结果"+s2);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
/**
 * 1定义MyCallable类实现Callable接口，应该申明线程任务执行完毕后的结果的数据类型。
 */
class MyCallable implements Callable<String>{
    private int n;
    public MyCallable(int n) {
        this.n = n;
    }
    /**
     * 2重写call方法，封装要做的事情。
     * @return
     * @throws Exception
     */
    @Override
    public String call() throws Exception {
        int sum=0;
        for (int i =0;i<n;i++){
            sum+=i;
        }
        return "子线程执行结果是"+sum;
    }
}
```

**优缺点：**

优点：线程任务类只是实现接口，可以继续继承类和实现接口，扩展性强。

​			**可以在线程执行完毕后去获取线程执行的结果。**

缺点：代码麻烦点



#### Thread常用方法

```java
final String getName()//获取线程名称
final void setName(String name)//设置名称
static Thread currentThread()//获取当前线程对象
    
//Thread类的线程休眠方法
public static void sleep(long time)//让当前线程休眠指定的时间后再继续执行，单位为毫秒
    
void run()//线程任务方法
void start()//线程启动方法
```

#### 构造器

```java
public Thread(String name)//可以为当前线程指定名称
public Thread(Runnable target, String name)//封装Runnable对象为线程对象，并指定线程名称
```



#### 线程安全问题

多个线程同时操作同一个共享资源的时候会出现业务安全问题，称为线程安全问题。

**出现的原因：**

存在多线程并发

同时访问共享资源

存在修改共享资源

**如何解决：**

让多个线程实现先后依次访问共享资源。

**线程同步核心思想：**

加锁，把共享资源进行上锁，每次只能一个线程进入访问完毕后解锁，然后其他线程才能进来。



##### 同步代码块

作用：把出现线程安全问题的核心代码上锁

原理：每次只能一个线程进入，执行完毕后自动解锁，其他线程才可以进来执行。

```java
synchronized(同步锁对象){
	操作共享资源的核心代码(核心代码)
}
```

锁对象要求：

理论上：锁对象只要对于当前同时执行的线程来说是同一个对象即可。

规范上： 建议使用共享资源作为锁对象,

​				对于实例方法建议使用this作为锁对象,

​				对于静态方法建议使用字节码(类名.class)对象作为锁对象



##### 同步方法

作用：把出现线程安全问题的核心方法上锁

原理：每次只能一个线程进入，执行完毕后自动解锁，其他线程才可以进来执行。

```java
修饰符 synchronized 返回值类型 方法名称(形参列表){
	操作共享资源的代码
}
```

**同步方法底层原理:**

底层也是有隐式锁对象的,只是锁的范围是整个方法代码.

实例方法： 同步方法默认用this作为锁对象,但是代码要高度面向对象!

静态方法:    同步方法默认用字节码(类名.class)对象作为锁对象



##### Lock锁:

为了更清晰的表达如何加锁放锁,jdk5以后提供了一个新的锁对象Lock,更灵活方便.

Lock是接口不能直接实例化,这里采用它的实现类ReentrantLock来构建Lock锁对象.

```java
ReentrantLock()//获得Lock锁的实现类对象
```

Lock的Api

```java
void lock()//获得锁
void unlock()//释放锁
```

```java
 class X {
   private final ReentrantLock lock = new ReentrantLock();
   // ...

   public void m() {
     lock.lock();  // block until condition holds
     try {
       // ... method body
     } finally {
       lock.unlock();//异常结构防止死锁
     }
   }
 }
```



#### 线程通信

线程通信:线程间相互发送数据,通常通过一个共享数据的方式实现.

线程间会根据共享数据的情况决定自己该怎么做,以及通知其他线程怎么做.

##### 常见模型:

生产者与消费者模型:生产者线程负责生产数据,消费者线程负责消费数据.

要求:生产者线程生产完数据后,唤醒消费者,然后等待自己.消费者消费完该数据后,唤醒生产者,然后等待自己.

Object类的等待和唤醒:

```java
final void wait()//让线程等待并释放所占锁,直到另一个线程调用notify()方法或notifyAll()方法
final void notify()//唤醒正在等待的单个线程
final void notifyAll()//唤醒正在等待的所有线程
```

上述方法应该使用**当前同步锁对象**进行调用.





#### 线程池

线程池就是一个可以复用线程的技术.

**不使用线程池的问题**

如果用户每发起一个请求,后台就创建一个新线程来处理,下次任务来了又创建新线程,而**创建新线程的开销是很大的**,这样会严重影响系统的性能.

线程池:工作线程+任务队列.

任务接口:Runnable  Callable



JDK5提供了代表线程池的接口: ExecutorService

##### 如何得到线程池对象:

**方式一:**使用**ExectorService**的实现类**ThreadPoolExecutor**自创建一个线程池对象

**构造器:**七个参数

```java
ThreadPoolExecutor(int corePoolSize, //核心线程数量
                   int maximumPoolSize, //指定线程池可支持的最大线程数,最大数量>=核心线程数量
                   long keepAliveTime, //指定临时线程的最大存活时间
                   TimeUnit unit, //指定存活时间的单位(s,h,min,day)
                   BlockingQueue<Runnable> workQueue, //指定任务队列
                   ThreadFactory threadFactory, //指定用哪个线程工厂创建线程
                   RejectedExecutionHandler handler)//指定任务忙,任务满的时候,新任务来了怎么办
```

现实世界ktv例子.

**面试题:**

**临时线程什么时候创建:**

新任务提交时发现**核心线程都在忙,** **任务队列也满了**,并且还可以创建临时线程,此时才会创建临时线程.

**什么时候开始拒绝任务**:

核心线程和临时线程都在忙,任务队列也满了,新的任务过来的时候才会开始任务拒绝.

**新任务拒绝策略：**

```java
static class ThreadPoolExecutor.AbortPolicy//丢弃任务并抛出异常，是默认策略
static class ThreadPoolExecutor.CallerRunsPolicy//由主线程负责调用任务的run()方法从而绕过线程池直接执行【老板亲自服务】
static class ThreadPoolExecutor.DiscardOldestPolicy//抛弃任务队列中等待最久的任务，然后把当前任务加入队列中
static class ThreadPoolExecutor.DiscardPolicy//丢弃任务，不抛出异常，不推荐
```

**线程池处理Runnable任务**

**线程池如何处理Runnable任务：**

```java
void execute(Runnable target)//执行任务，命令，一般用来执行Runnable任务
```

例如：

```java
package com.xfzy.d8_threadPool;

import java.util.concurrent.*;

public class ThreadPoolDemo01 {
    public static void main(String[] args) {
        //1创建线程池对象
        ExecutorService pool = new ThreadPoolExecutor(3,5,
                6, TimeUnit.SECONDS,new ArrayBlockingQueue<>(5),
                Executors.defaultThreadFactory(),new ThreadPoolExecutor.AbortPolicy());
        //2给任务线程池处理
        Runnable target =new MyRunnable();
        pool.execute(target);
        pool.execute(target);
        pool.execute(target);

        pool.execute(target);
        pool.execute(target);
        pool.execute(target);
        pool.execute(target);
        pool.execute(target);

        //创建临时线程
        pool.execute(target);
        pool.execute(target);

        //不创建，拒绝策略被触发
        pool.execute(target);

        //关闭线程池（开发一般不会用）
        pool.shutdownNow();//立即关闭，即使任务没有完成，丢失任务的。返回任务队列中未执行的任务
        pool.shutdown();//会等待全部任务执行完毕之后再关闭。（柔和一点）
    }
}
public class MyRunnable implements Runnable{
    @Override
    public void run() {
        for (int i=0;i<5;i++){
            System.out.println(Thread.currentThread().getName()+"输出了：helloword"+i);
        }
    }
}

```

**线程池处理Callable任务**

```java
Future<T> submit(Callable<T> task)//执行Callable任务，返回未来任务对象获取线程结果
```



例如：

```java
package com.xfzy.d8_threadPool;

import java.util.concurrent.*;

public class ThreadPoolDemo02 {
    public static void main(String[] args) throws Exception {
        //1创建线程池对象
        ExecutorService pool = new ThreadPoolExecutor(3,5,
                6, TimeUnit.SECONDS,new ArrayBlockingQueue<>(5),
                Executors.defaultThreadFactory(),new ThreadPoolExecutor.AbortPolicy());
        //2给任务线程池处理
        Future<String> f1=pool.submit(new MyCallable(100));
        Future<String> f2=pool.submit(new MyCallable(200));
        Future<String> f3=pool.submit(new MyCallable(300));
        Future<String> f4=pool.submit(new MyCallable(400));
        Future<String> f5=pool.submit(new MyCallable(500));

        System.out.println(f1.get());
        System.out.println(f2.get());
        System.out.println(f3.get());
        System.out.println(f4.get());
        System.out.println(f5.get());


        //创建临时线程
//        pool.submit(new MyCallable(100));
//        pool.submit(new MyCallable(100));

        //不创建，拒绝策略被触发
//        pool.submit(new MyCallable(100));

        //关闭线程池（开发一般不会用）
//        pool.shutdownNow();//立即关闭，即使任务没有完成，丢失任务的。
        pool.shutdown();//会等待全部任务执行完毕之后再关闭。（柔和一点）
    }
}


package com.xfzy.d8_threadPool;

import java.util.concurrent.Callable;


public class MyCallable implements Callable<String>{
    private int n;
    public MyCallable(int n) {
        this.n = n;
    }
    @Override
    public String call() throws Exception {
        int sum=0;
        for (int i =0;i<n;i++){
            sum+=i;
        }
        return Thread.currentThread().getName()+"子线程执行1-"+n+"结果是"+sum;
    }
}

```



方式二:使用Executors(线程池的工具类)**调用方法**返回**不同特点的线程池对象**.

```java
static ExecutorService newCachedThreadPool()//线程任务随任务增加而增加，如果线程任务执行完毕且空闲了一段时间则会被回收掉
static ExecutorService newFixedThreadPool(int nThreads)//创建固定线程数量的线程池，如果某个线程出现异常而结束，那么线程池会补充一个新线程替代他。
static ExecutorService newSingleThreadExecutor()//创建只有一个线程的线程池对象，如果该线程出现异常而结束，那么线程池会补充一个新线程。
static ScheduledExecutorService newScheduledThreadPool(int corePoolSize)//创建一个线程池，可以实现在给定的延迟后运行任务，或者定期执行任务。
```

Executors的底层其实也是基于线程池的实现类ThreadPoolExcutor创建线程池对象的。

Executors在某些**大型系统环境**中，如果**不注意将会出现系统风险**（任务队列长度不受限、创建线程数不受限，可能会出现outofmemoryError）



#### 定时器

控制任务延时调用、周期调用

作用：闹钟、定时邮件发送。

定时器实现方式：

1、Timer

```java
Timer()
```

```java
void schedule(TimerTask task, long delay, long period)
```

timer存在的问题：是**单线程，处理多个任务按照顺序执行，存在延时与设置定时器的时间有出入**。

可能因为其中**某个任务的异常使Timer线程死掉，从而影响后续任务执行**。

2、ScheduledExecutorService

jdk1.5中引入了并发包，目的是为了弥补Timer的缺陷，ScheduledExecutorService内部为线程池。

Executors的方法：

```java
static ScheduledExecutorService newScheduledThreadPool(int corePoolSize)
```


ScheduledExecutorService的方法：

```java
ScheduledFuture<?> scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit)
```

ScheduledExecutorService优点：基于线程池，某个任务执行情况不会影响其他定时任务的执行。



#### 线程并发、并行

线程生命周期中的6种状态。

并发：cpu同时处理线程的数量有限。

​			cpu会**分时轮询**为系统的每个线程服务，由于cpu切换的速度很快，给我们感觉这些线程就是在同时执行，这就是并发。

并行：在同一时刻，同时有多个线程在被cpu处理并执行。



#### 线程的生命周期：

线程的状态：6种，定义在Thread类的内部枚举类中。

New新建：刚创建没有启动

Runnable可运行：调用了start等待cpu调度

Teminated被终止：run正常推出，或者没有捕获的异常终止了run

Blocked锁阻塞：线程执行时未竞争到锁对象

Waiting无限等待：只有另一个线程调用notify、notifyAll才能唤醒这个线程

Timed Waiting计时等待：有几个方法由超时参数，调用他们就会进入此状态，Thread.sleep,Object.wait



### 42网络编程

网络通信三要素：ip  端口  协议

#### ip地址操作类：InetAddress
