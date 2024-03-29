# 内部类

> 内部类是定义在另外一个类或方法中的类
>
> 可分为：
>
> * 匿名内部类
>* 静态内部类

* **成员内部类**

> 定义在类中，作为类的成员变量
>
> ```java
> public class Outer{
>     //这是一个成员变量
>     private int m = 4;
> 
>     //这是一个成员内部类
>     public class Inner(){
>         private void test(){
>             System.out.println();
>         }
>     }
> }
> ```
>
> 因为是作为类的成员变量，所以具有和成员变量、成员方法相同的一些特点，例如：
>
> 1. 可以被*所有*的访问修饰符修饰
> 2. 成员内部类可以访问外部类的*所有*成员变量，包括私有成员变量
> 3. 可以使用this访问成员变量，当外部类的成员变量名被覆盖时可以使用外部类名+this+成员变量名 进行访问 例如：Outer.this.m
>
> 此外还有一些其他特点：
>
> 1. 成员内部类包含一个外部类的指针引用，成员内部类在编译时会默认增加一个以外部类指针作为参数的构造方法
>
>    ![](..\imag\内部类反编译.png)
>
> 2. 成员内部类不可以定义static成员（[为什么不能声明static](https://zhidao.baidu.com/question/332261019838736725.html)）: 提示与生命周期有关、类加载机制



* **局部内部类**

> 定义在方法或作用域中的类，和成员内部类的区别在于**访问权限**
>
> ```java
> public class Outer{
>     public void test(){
>         class Inner{
>             
>         }
>     }
> }
> ```
>
> 与成员内部类相比具有以下几个区别：
>
> 1. 局部内部类**不能有**访问权限修饰符
> 2. 局部内部类**不能定义为static**
> 3. 外部类的成员变量都可以访问，但是对应<u>方法或域中的局部变量</u>**必须使用final才能访问**
>
> 同样具有和成员内部类相同的一些特点：
>
> 1. 局部内部类也可以使用Outer.this语法制定访问外部类成员
> 2. 局部内部类默认包含了外部类对象的引用
>
> ![](..\imag\局部内部类.png)