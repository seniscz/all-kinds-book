## final基础应用
### final类
- final修饰的类不能被继承。
- final类中的成员变量可以根据需要设为final，但是要注意final类中的所有成员方法都会被隐式地指定为final方法。
- 在使用final修饰类的时候，要注意谨慎选择，除非这个类真的在以后不会用来继承或者出于安全的考虑，尽量不要将类设计为final类。

## 并发编程中的应用
- 在构造函数内对一个final域的写入，与随后把这个被构造对象的引用赋值给一个引用变量，这两个操作之间不能重排序。
- 编译器会在final域的写之后，插入一个StoreStore屏障，这个屏障可以禁止处理器把final域的写重排序到构造函数之外。