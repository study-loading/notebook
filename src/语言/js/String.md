## String类型

### 定义

  let str = '123'
  let str = new String('123')

通过对象字面量得到的是一个基本类型，存储在栈中，通过new操作符得到的是一个对象，但是作为一个基本类型的str却可以调用String原型上的方法，这显然是一个对象才具备的行为

js在处理 
  let str = '123';
  let l = str.length
时，因为解析到需要读取length属性，js会new String(str)来创建一个临时对象，并将str指向它，然后读取length属性返回，将str再赋值成123，再销毁临时对象，好处是没有调用属性的话，具备栈存储的所有优势，疑问是如果进行频繁的属性读取操作，难道不会因为不断创建与销毁导致性能问题吗，类似于boolean，boolean都是这样的，那么像
  list = []
  obj = {}
和new操作符创建有什么区别呢，具体在Object.md中描述

### 属性

对于基本类型不具备任何属性

对象本身具有的属性（hasOwnProperty）, 例如 str = new String('123')， str如下
  {
    0: '1',
    1: '2',
    2: '3',
    length: 3,
    __proto__: String.prototype
  }
这很明显是一个类数组的结构，所有可以将数组上的一些方法（forEach，reverse...）通过call，apply来给str调用
String的split方法和Array的join方法很好的支持字符串与数据的转化，所以所有的方法都是互通的

### 方法

查找

* charAt(index = 0)

> 获取指定下标位置的字符，如果index不在length范围内则返回 '',
> 因为字符对象是类数组的结构，也可以str[index]取值，但是这种形式可以取到String上任何属性值（没有为undefined），charAt只能取得对应下标的字符
> 因为js中字符串是不可变的所以无法通过a[0] = '1'的形式来修改字符串，只能通过重新赋值再创建一个新的字符来替代

* charCodeAt(index = 0)

> 返回0-65535之间的整数，该整数位字符对应的ascii码值，表示给定索引处的utf-16代码单元，如果index超出length范围返回NaN
> 但在——例如 Unicode 编码单元 > 0x10000 的这种——不能被一个 UTF-16 编码单元单独表示的情况下，只能匹配 Unicode 代理对的第一个编码单元) 。如果你想要整个代码点的值，使用 codePointAt()。

* codePointAt(index = 0)

> 方法返回 一个 Unicode 编码点值的非负整数
> 如果在索引处没找到元素则返回 undefined
> 如果在索引处开始没有UTF-16 代理对，将直接返回在那个索引处的编码单元。

* fromCharCode(...numbers)

> 参数为一组序列数字，表示Unicode值，结果返回一个字符串，和charCodeAt方法相反
> fromCharCode为String上的静态方法，String.fromCharCode()

* fromCodePoint(...numbers)

> 参数为一组序列数字，表示Unicode值，结果返回一个字符串，和CodePointAt方法相反
> fromCodePoint为String上的静态方法，String.fromCodePoint()

* indexOf(char, fromIndex? = 0)

> @parmas
> char: 当char为''时，fromIndex <= 0 返回0，否则返回fromIndex
> fromIndex： 当小于0时视为0，大于等于str.length返回-1，
> 返回第一次出现指定字符串的第一个字符所在的下标，没找到返回-1
> 可用来查找字符串中是否存在某个子串

* lastIndexOf(char, beforeIndex? = str.length)

> beforeIndex：当小于0时视为0，大于等于str.length时视为str.length，
> 与indexOf相反，从指定的beforeIndex往前找，返回找到位置的第一个字符的下标，否则返回-1

* includes(str, position? = 0) es6

> 查找某个字符串，找到返回true，否则返回false

* search

* match

### 操作

* concat(..str)

> concat是将多个string拼接成一个字符串的方法
> 字符串的拼接也可以用str1 + str2 + str3，但一般大量字符串拼接时用+= +效率会更高

* slice(startIndex = 0, endIndex? = str.length)

> startIndex为负数时会从后往前数相应位数，为str.length + startIndex
> endIndex为结束位置的下标，如果endIndex为负数，则为str.length + endIndex
> 返回结果中不包括endIndex位置的字符

* substring(startIndex, endIndex? = str.length)

> 该方法与slice十分类似，区别是两个参数小于视为0，大于str.length视为str.length
> 如果参数大小顺序相反，会自动调转位置

* 

### 转换

* split(gap, limit)

> 将字符串以指定的字符为分割线，分割成数组，limit为限制分割数据的最大长度，如果在分割时达到了limit的限制，则会立即停止后续分割

* 
