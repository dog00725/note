# 内部类

> 内部类是定义在另外一个类或方法中的类
>
> 可分为：
>
> * 成员内部类
>
>   定义在类中，作为类的成员变量
>
>   ```java
>   public class Outer{
>       //这是一个成员变量
>       private int m = 4;
>       
>       //这是一个成员内部类
>       public class Inner(){
>           private void test(){
>               System.out.println();
>           }
>       }
>   }
>   ```
>
>   因为是作为类的成员变量，所以具有和成员变量、成员方法相同的一些特点，例如：
>
>   1. 可以被*所有*的访问修饰符修饰
>   2. 成员内部类可以访问外部类的*所有*成员变量，包括私有成员变量
>   3. 可以使用this访问成员变量，当外部类的成员变量名被覆盖时可以使用外部类名+this+成员变量名 进行访问 例如：Outer.this.m
>
>   此外还有一些其他特点：
>
>   1. 成员内部类包含一个外部类的指针引用，成员内部类在编译时会默认增加一个以外部类指针作为参数的构造方法
>
>      ![](F:\hqs_git_note\imag\内部类反编译.png)
>
>   2. 成员内部类不可以定义static成员（[为什么不能声明static](https://zhidao.baidu.com/question/332261019838736725.html)）
>
> * 局部内部类
>
> * 匿名内部类
>
> * 静态内部类