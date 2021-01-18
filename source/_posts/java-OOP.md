---
title: Java面向对象(Java基础知识学习)
top: false
cover: false
toc: true
mathjax: true
date: 2020-12-30 14:57:11
password:
summary: 根据视频整理了Java面向对象相关的知识。Java的重点知识（类与对象/构造方法/封装/继承/多态/抽象等）
tags:
- Java
- 面向对象
categories:
- 编程知识
---


#### 1.什么是OOP？
> - Object Oriented Programming，就是面向对象的编程，还有OOD（面向对象的设计），OOA（面向对象的分析）
> - **对象是类的实例**，对象能干什么，完全取决于类是如何定义的

#### 2.面向对象（侧重的是对象）
> - 强调的是**功能行为**，以**函数**为最小单位，考虑怎么做 
> - **面向对象的底层实际还是面向过程。把面向过程抽象成类，然后封装，方便我们使用就是面向对象了**。
> - 面向对象是**模型化**的，你只需抽象出一个类，这是一个封闭的盒子，在这里你拥有数据也拥有解决问题的方法。需要什么功能直接使用就可以了，不必去一步一步的实现，至于这个功能是如何实现的，管我们什么事？我们会用就可以了。
> - **可扩展性非常强，维护成本低**

#### 3.面向过程(侧重的是过程)
> - 强调的是**具备功能的对象**，以**类、对象**为最小单位，考虑谁来做
> - 面向过程是**具体化的，流程化的**，解决一个问题，你需要一步一步的分析，一步一步的实现。**第一步该做啥，下一步该做啥**
> - **代码简单，可维护性差**

#### 4.面向对象和面向过程举例分析
> - 举个最简单点的例子来区分 面向过程和面向对象
> - 有一天你想吃鱼香肉丝了，怎么办呢？你有两个选择
* 1、自己买材料，肉，鱼香肉丝调料，蒜苔，胡萝卜等等然后切菜切肉，开炒，盛到盘子里。
* 2、去饭店，张开嘴：老板！来一份鱼香肉丝！
> - 看出来区别了吗？这就是  1是面向过程，2是面向对象。面向对象有什么优势呢？首先你不需要知道鱼香肉丝是怎么做的，降低了耦合性。如果你突然不想吃鱼香肉丝了，想吃洛阳白菜，对于1你可能不太容易了，还需要重新买菜，买调料什么的。对于2，太容易了，大喊：老板！那个鱼香肉丝换成洛阳白菜吧，提高了可维护性。总的来说就是降低耦合，提高维护性！

#### 5.面向对象的重点知识
* 类与对象
* 构造方法
* 访问权限（private/public/protect）
* 继承
* **多态（最重要）**
* 抽象和接口
* 内存分析 


#### 6.类与对象
> - 类是使用`class`来定义的
> - 属性：成员变量来描述，直接写在类中的变量
> - 动作：成员方法，不写static就是成员方法

```java
public class car{
    // 成员变量
    String color;
    int speed;
    int seat = 5;
    
    // 成员方法
    public void run(){
        System.out.println(this.color);
        System.out.println(this.speed);
    }
    public void fly(){
    
    }
    
    
    public static void main(String[] args){
    // 写在方法里的变量是局部变量
        int a = 10;    
        Car car1 = new Car(); // 类的实例化
        car1.color = '蓝色'；
        car1.speed = 120;
        car1.run( );
        // 蓝色
        // 120
        
        Car car2 = new Car();
        car2.color = '红色'；
        car2.speed = 180;
         // 红色
        // 180 
    }
}
```

> - **创建对象** -- 类的实例化
> - 类  引用  =  new  类（）；
> - `Car  car = new  Car();`



#### 7.this关键字
> - 在类的方法中，默认会有一个this：代指当前正在执行这个方法的对象
> - `car.run();` : 在调用对象的方法的时候，**java会自动的把对象传递给方法**，在方法中通过`this`来接受对象

```java
public void run(){
    // 在类的方法中，默认会有一个this：代指当前正在执行这个方法的对象
    System.out.println(this.color);
    System.out.println(this.speed);
    System.out.println(this.seat);
}
```


#### 8.构造方法（构造器）
> - **Java会自动为每个类分配一个无参数的构造方法**
> - 在创建对象的时候，自动调用的方法
> - **语法：**
> public 类名（传参）{
>    
> }
> - **构造器作用：** ①、创建对象 ②、初始化对象结构 

**注意：**
* 1. **构造函数没有返回值**
* 2. 在我们new的时候，会自动的调用构造方法
* 3. 类名  引用  =  **New 类名()；**  => ***调用构造方法***

**此时，上面的代码可以通过构造方法进行优化**
```java
public class car{
    // 成员变量
    String color;
    int speed;
    int seat = 5;
    
    // Java会自动为每个类分配一个无参数的构造方法
    // 如果自己创建了，Java就不会进行分配了
    // 在进行类的实例化的时候，自动调用构造方法
    public Car(String color, int speed){
        this.color = color;
        this.speed = speed;
    }
    
    // 成员方法（没加static的都是成员方法）
    public void run(){
        System.out.println(this.color);
        System.out.println(this.speed);
    }
      
    public static void main(String[] args){
    // 写在方法里的变量是局部变量
        int a = 10;    
        Car car1 = new Car('蓝色'，120);
        // car1.color = '蓝色'；
        // car1.speed = 120;
        car1.run( );
        // 蓝色
        // 120
        
        Car car2 = new Car('红色'，180);
        // car2.color = '红色'；
        // car2.speed = 180;
         // 红色
        // 180 
    }
}
```

#### 9.构造方法的重载
```java
public class Daxia{
    String name;
    int age;
    String sex;
    String waihao; // 外号
    
   // 构造方法1
   public Daxia( String name, int age, String sex){
        this.name = name;
        this.age = age;
        this.sex = sex;
   }
   
   // 构造方法2 -- 重载
   public Daxia(String name, int age, String sex, String waihao){
        // this.name = name;
        // this.age = age;
        // this.sex = sex;
        
        // 省略为以上写法
        // this可以直接调用当前类中的其他构造方法
        this(name, age, sex);
        this.waihao = waihao;
   }

   public static void main(String[] args){
   
        // 岳不群
        Daxia  dx1 = new Daxia('岳不群'， 18 , '男')；
        // 武松（多一个外号）
        Daxia dx2  = new Daxia(' 武松 '， 19 ，'男' ，'打虎武松')
   }
}

```

#### 10.在类中使用static修饰成员变量（静态成员变量）
```
public Person{
    static  String country = "xxx";
    String sex;
}
```
> - 静态的内容在内存中是保留一份的，并且**各个对象之间进行共享**
> - country就是一个**静态成员变量**
> - 可以使用`对象.变量名` 进行访问   `Person.country;`
> - 属于类的，并不属于对象
> - 优先于对象产生

##### 创建对象的过程
```java
public class Test{
    // 通用构造器
    {
        System.out.println("这里是通用构造器！")；
    }
    // 静态构造器
    static {
        System.out.println("静态构造器！")；
    }
    // 构造方法
    public Test(){
        System.out.println("这里是构造方法！")；
    }
    
    public static void main(String[] args){
        new Test();
    }
}
```
> **静态构造器！**
> **这里是通用构造器！**
> **这里是构造方法！**



#### 11.包和导包
> - 包名：**com.公司域名.包的内容**
> - 导包：import 包+类名；
> - 报错需要导包的时候可以使用：`Alt + Enter` 快捷导包;

不需要导包的情况：
* 在自己的包中
* java.lang包下的所有内容都不需要导包


#### 12.访问权限
* public   **公共的，所有人都可以访问**
* default   **包访问权限，在自己的包中可以随便进行访问**
* private    **私有的，当前类可以使用**



#### 13.getter/setter
> - 使用IDEA创建类后，类的成员变量定义后可以快捷的进行getter/setter生成
> - 空白位置 -> 右键 -> generate -> getter and setter ->全选  ->  ok
```java
public class Person{
    private String name; 
    private int age;
    
    public void setName(String name){
        this.name = name;
    }
    
    public void setAge(int age){
        this.age = age;
    }
    
    public void chi(){
        System.out.println(this.name+"在吃东西")；
        
        Person p = new Person();
        p.setName("Joseph");
        p.setAge(22);
    }
}
```

#### 14.类的继承
> - 子类可以自动拥有父类中**除了私有内容外的其他所有内容**
> - public class 类名 extends 父类 { }

> - 作用：简化代码的开发

```java
// 妖怪的类
public class YaoGuai{
    public void chiRen(){
        System.out.println("妖怪会吃人！")
    }
}

// 黑妖怪
public class HeiYaoGuai extends YaoGuai{
    // 此时，黑妖怪的类中就包含这父类的 chiRen（）方法
    // 同时，黑妖怪可以拥有自己的 成员方法/成员变量
    
    public void chiRou(){
        System.out.println("黑妖怪会吃肉！")
    }
    
    public static void main(String[] args){
        // 黑妖怪类实例化
        HeiYaoGuai hy = new HeiYaoGuai();
        // 调用黑妖怪实例的方法
        hy.chiRen();
    }
}

// 妖怪会吃人！
```

#### 15.super关键字
> - 标识父类中的东西（**获取到父类中的内容**）
> - 在继承类中使用this时，子类会就近查找原则，没有的时候才会去查找父类的内容。   例：`this.name;`,子类会先在自己的类中查找是否有name成员变量，没有则去父类查找
> - 但是使用`super.name;`就可以确定的使用父类的内容
> - **用`super` 和`this` 区分父类和子类中的内容**


##### 对象的创建过程：
当创建一个类的子类（继承类）的时候，先是调用子类的构造方法，**但是在子类的构造方法的第一行会默认调用父类的构造方法**
```java
 // 父类
 public class Parents{
    String name = '父类中的名字';
    
    public Parents(){
        System.out.println("我是父类的构造方法！")；
    }
 }
 
 // 子类
 public class Children extends Parents{
 String name = '子类中的名字'；
     public Children(){
        // 还原程序，在子类的构造方法的第一行，默认调用父类的构造方法
        // super可以传递参数，父类的构造方法接收即可
        super();  
        System.out.println("我是子类的构造方法！")；
     }
     
     public void chi(){
        // 打印父类中的name
        System.out.println(super.name);
        // 先找到自己类的name，有的话就不往上找了
        System.out.println(this.name);
     }
     
     public static void main(String[] args){
        Children child = new Children();
        child.chi();
     }
 }
```
**控制台打印输出：**
* 我是父类的构造方法
* 我是子类的构造方法
* 父类中的名字
* 子类中的名字



#### 16.多态
> - 同一个对象有多种形态
> - 作用：**把不同的数据类型进行统一，提高程序的可扩展性**

![多态](1.png)


##### 小知识点
* 把子类的对象复制给父类的变量 --> 向上转型
    * 缺点：**屏蔽掉子类特有的方法**，如果需要使用子类特有的方法，需要向下转型
    * ![多态小知识点](2.png)
* 把父类的变量转化回子类的变量  --> 向下转型
（转换以后的数据类型）变量



#### 17.final
> **被final修饰的变量不能修改，又称为常量**

![Final类修饰的变量不能修改](3.png)
> **被final修饰的方法不可以被重写**

![被final修饰的方法不可以被重写](4.png)

> **被final修饰的类不可以被继承**

![被final修饰的类不可以被继承](5.png)



#### 18.抽象（abstract）
> - 在java中：只声明，不实现
> - 被`abstract`修饰的方法是一个抽象方法，**抽象方法没有方法体**，直接分号（；）结束
> - **类中如果有抽象方法，这个类也必须是一个抽象类**

![抽象（abstract）](6.png)


**特点**
* **抽象类不可以创建对象**
* **抽象类的子类必须要重写父类中的抽象方法**，否则这个子类也必须是一个抽象方法，***通过抽象类，强制要求子类必须有哪些方法***
* 抽象类中可以有正常的方法



#### 19.接口（Interface）
> - ***类只能单继承，接口可以实现多继承***
> - **接口实际上是一种特殊的抽象类**
> - **接口中的所有方法都是抽象方法，都是公开的**
> - **接口中的所有变量都是全局静态变量**
> - **接口使用`Interface`声明**

// 接口中的所有方法都是抽象方法,可以省略abstract
// 接口中所有的内容都是公开的，公共的

![接口](7.png)

> **接口的实现**

![接口的实现](8.png)

> **接口的多态性**

![接口的多态](9.png)

> **一个类可以继承自一个类，可以实现多个接口**
> **接口可以讲很多不相关的东西进行整和**

![一个类实现多个接口](10.png)


#### 20.成员变量初始值
> - 在Java中，变量需要先声明后赋值，再使用
> - java的成员变量，在创建对象的时候都会进行一次初始化操作，都会给一个默认值
> - 基本数据类型默认值都是0  包括boolean -> false
> - 引用数据类型：null
> - null表示空，什么都没有，起到占位作用


#### 21.Object
> - 万事万物皆为对象
> - 在Java中，所有的类都要继承Object


> **Student类继承的是Person类，但是Person会默认继承Object类，所以Student类间接继承了Object类**
> ![Object](11.png)


#### 22.equals和==
> - == 判断左右两端数据是否一样
> - equals: Object类提供的一个方法，用于判断两个对象是否相等
> - equals可以自己重写

![equals和==](12.png)



#### 23.instanceof
> **判断一个对象是否是一个类的实例**



#### 24.异常处理（try...catch...）
```java
try{
    // 尝试执行的代码
    System.out.println(1/0);
}catch(Exception e){
    // 处理异常的代码
    // e.printStackTrace(); // 打印错误信息
    System.out.println("系统出错了，请联系管理员！");
}finally {
    // 最终要执行的代码
    System.out.println("请下次再试！");
}
```


#### 25.自定义异常
> 自定义的异常**必须要继承Exception或者RuntimeException**


```java
// 出现错误的类
public class Person{
    public void nan(Person p) throws GenderException{
        if(xxx){
        
        }else{
            // 抛出自定义异常
            throw new GenderException("这里是错误信息！")
        }
    }
}
 


// 自定义异常GenderException类
public class GenderException{

    // 构造方法
    public GenderException(String msg){
        super(msg);   // 调用父类的构造方法 Exception(msg)
    }
}

```
**自定义错误**
![自定义错误额](13.png)


#### 26.MVC设计模式
> - **Model**:数据模型层
> - **View**：视图模型层
> - **Controller**：控制器层
> - **作用：** 这种将程序输入输出、数据处理、数据的展示分离开的设计模式使程序变的灵活而且清晰，同时也描述了程序各个对象间的通信方式，降低了程序的耦合性
> 

#### 27.封装性
> 高内聚、低耦合

