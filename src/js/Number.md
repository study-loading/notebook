## Number类型

### 定义

  let n = 1;
  let n = new Number(1)

number字面量是基本类型，number对象是引用类型，在直接访问n.toString()时，其表现和String一样

> js中不管整数还是小数都是用8字节表示的，每个字节包含8位二进制，总共64位，0-51（共52位）用来表示分数部分，52-63（共11位）用来表示指数部分，63位位符号位
> js表示一个数的公式为abs = 1.f * 2 ^ (e - 1023)，其中abs为结果，f为分数部分的值，e为指数部分的值，而且根据上面可知，0<f<2^52-1，0<e<2^11-1

###静态属性

* Number.EPSILON

> 两个可表示(representable)数之间的最小间隔。

* Number.NaN

> 特殊的“非数字”值，和window.NaN一样

* Number.MAX_VALUE

> 能表示的最大正数，该数为1.7976931348623157e+308，最小的负数是-MAX_VALUE

* Number.MIN_VALUE

> 能表示的最小正数（5e-324），即最接近 0 的正数 (实际上不会变成 0)，最大的负数是-MIN_VALUE

* Number.MAX_SAFE_INTEGER

> 表示最大安全整数，即从0到该数之间的整数是连续的，那么最小的安全整数就是-Number.MAX_SAFE_INTEGER
> 超过安全整数的数进行运算，可能会出现误差，因为之后的整数并不是每一个都能表示出来

* Number.MIN_SAFE_INTEGER

> 表示最小安全整数，即从该数到0之间的整数是连续的，那么最大的安全整数就是-Number.MIN_SAFE_INTEGER
> 超过安全整数的数进行运算，可能会出现误差，因为之后的整数并不是每一个都能表示出来

* Number.NEGATIVE_INFINITY

> 特殊值，表示负无穷，NEGATIVE_INFINITY和[自身，-POSITIVE_INFINITY]相比为true，和-window.Infinity相等

* Number.POSITIVE_INFINITY

> 特殊值，表示负无穷，POSITIVE_INFINITY和[自身，-NEGATIVE_INFINITY]相比为true，和window.Infinity相等

* prototype

> 原型对象

###静态法法

* isNaN(num) (es6)

> 判断一个数是否是NaN
> 要注意的是不能用===来判断是否为NaN，得到的结果为false，其内部是使用Object.is()方法来判断是否为NaN

* isInteger(num)

> 判断num是否是整数

* isSafeInteger(num)

> 判断是否为安全整数( -(2^53 - 1) 至 2^53 - 1之间)

* isFinite(num) (es6)

> 判断是否为有限数
