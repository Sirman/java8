#java8的新特性
一、Java8允许我们给接口添加一个非抽象的方法实现，需要用default关键字，这个特征又叫扩展方法
interface Formula
{
    double calculate(int a);

    default double sqrt(int a) {
        return Math.sqrt(a);
    }
}
Formula方法在拥有calculate方法的同时，定义了sqrt方法，则其子类只需实现calculate方法，默认方法sqrt将在子类上直接使用。因为java是单继承，所以让一个类拥有新的特性，通常使用接口实现。
二、Lambda表达式
lambda运算符:所有的lambda表达式都是用新的lambda运算符"=>"，称为“转到”或者“成为“，运算符将表达式分为两个部分，左边指定参数，右边是lambda的主体。
