# java入门

## day1

### 1.编译和运行

编写：编写的代码保存在.java文件中

编译：使用javac.exe命令编译我们的java源文件，格式：javac 源文件名.java

运行：使用java.exe命令解释运行我们的字节码文件，格式：java 类名 

### 2.

在一个java源文件中可以声明多个class，但是只能最多有一个类声明为public的，而且声明为public的类的类名必须和源文件名相同。

### 3.

程序入口是main()方法，格式是固定的

```java
class HelloJava{
	public static void main(String[] args){
		System.out.println("hello world");	
	}
}
class Person{

}
```

### 4.

输出数据：

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
