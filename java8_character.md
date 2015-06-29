#java8的新特性
**一、Java8允许我们给接口添加一个非抽象的方法实现，需要用default关键字，这个特征又叫扩展方法**
interface Formula
{
    double calculate(int a);

    default double sqrt(int a) {
        return Math.sqrt(a);
    }
}
Formula方法在拥有calculate方法的同时，定义了sqrt方法，则其子类只需实现calculate方法，默认方法sqrt将在子类上直接使用。因为java是单继承，所以让一个类拥有新的特性，通常使用接口实现。
**二、Lambda表达式函数式接口**

函数式接口（functional interface 也叫功能性接口，其实是同一个东西）。简单来说，函数式接口是只包含一个方法的接口。比如Java标准库中的java.lang.Runnable和java.util.Comparator都是典型的函数式接口。java 8提供 @FunctionalInterface作为注解,这个注解是非必须的，只要接口符合函数式接口的标准（即只包含一个方法的接口），虚拟机会自动判断，但 最好在接口上使用注解@FunctionalInterface进行声明，以免团队的其他人员错误地往接口中添加新的方法。
Java中的lambda无法单独出现，它需要一个函数式接口来盛放，lambda表达式方法体其实就是函数接口的实现。

Lambda语法包含三个部分

    一个括号内用逗号分隔的形式参数，参数是函数式接口里面方法的参数

    一个箭头符号：->

    方法体，可以是表达式和代码块，方法体函数式接口里面方法的实现，如果是代码块，则必须用{}来包裹起来，且需要一个return 返回值，但有个例外，若函数式接口里面方法返回值是void，则无需{}
    总体看起来像这样
	(parameters) -> expression 或者 (parameters) -> { statements;
lambda实例

	public class Calculator {
    interface IntegerMath {
    int operation(int a, int b);
    }
    public int operateBinary(int a, int b, IntegerMath op) {
    return op.operation(a, b);
    }
    public static void main(String... args) {
        Calculator myApp = new Calculator();
        IntegerMath multi = (a, b) -> a * b;
        IntegerMath divide = (a, b) -> a / b;
        System.out.println("40 * 2 = " +
            myApp.operateBinary(40, 2, multi ));
        System.out.println("20 / 10 = " +
            myApp.operateBinary(20, 10, divide));
    }
	}
