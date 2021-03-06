基础数据类型
> * 基础数据类型存储在栈内存中，每申明一个变量做入栈操作，当函数执行完成就会出栈，除非申明为全局变量
> * 栈里的值无法被改变

比如： a = 2, 会在内存中存入'a'和2, 那么对于栈来说它只是存储一个个key-value形式的list，其中必然是可以出现同名的变量，比如两个a，但是编程语言当中会限制在同一个作用域里一个变量只能定义一次，而且引出了作用域的概念。

基本数据类型申明a = 2， a可视为一个未知的结构体，其中保存了a在栈中的内存地址，当a进行运算时就会去栈里读取值，当a被赋值时，可参考下面java赋值的流程

引用数据类型
> 引用数据类型存储在堆里，类似与数据结构中的树，当申明 a = new Object()时，a是存储在栈中的，不过a在栈中的值是一个内存地址，指向了堆里的对象

栈与堆

> * 栈的内存由计算机自动分配和回收，堆可由程序员分配释放，若程序员不释放，则由垃圾回收机制回收
> * 引用java中int a = 3; int b = 3; 编译器先处理int a= 3；首先它会在栈中创建一个变量为a的内存空间，然后查找有没有字面值为3的地址，没找到，就开辟一个存放3这个字面值的地址，然后将a指向3的地址。接着处理int b= 3；在创建完b的引用变量后，由于在栈中已经有3这个字面值，便将b直接指向3的地址。这样，就出现了a与b同时均指向3的情况。
> * 特别注意的是，这种字面值的引用与类对象的引用不同。假定两个类对象的引用同时指向一个对象，如果一个对象引用变量修改了这个对象的内部状态，那么另一个对象引用变量也即刻反映出这个变化。相反，通过字面值的引用来修改其值，不会导致另一个指向此字面值的引用的值也跟着改变的情况。如上例，我们定义完a与b的值后，再令a=4；那么，b不会等于4，还是等于3。在编译器内部，遇到a=4；时，它就会重新搜索栈中是否有4的字面值，如果没有，重新开辟地址存放4的值；如果已经有了，则直接将a指向这个地址。因此a值的改变不会影响到b的值。
> * 对于js具体的堆栈运行过程还需调研
> * 栈读取速度比堆快，堆可以动态分配内存大小
> * js中的function是存在堆里的
