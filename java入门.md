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
