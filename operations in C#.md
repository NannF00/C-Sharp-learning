# ?

1. 可空类型修饰符(？)：
引用类型可以使用空引用表示一个不存在的值,而值类型通常不能表示为空。

例如:

    string str=null;//是正确的。
    int i=null；//编译器将报错。
    
为了使值类型也可为空,可空类型出现了,可空类型使用可空类型修饰符？来表示,表现形式为T?。

例：int?表示是可空的整形,DateTime?表示为可空的时间。

    int? i=null;//表示可空
    
T?其实是System.Nullable<T>（泛型结构）的缩写形式,也就意味着当你用到T？时编译器在编译时会把T？编译成System.Nullable<T>的形式,

例如：int?,编译后便是System.Nullable<int>的形式。
  
2. 三元（运算符）表达式(？:)：
  
语法为：条件表达式？表达式1：表达式2；
  
该操作首先求出条件表达式的值(bool类型),为true时调用表达式1,为flase时调用表达式2。
  
其逻辑为："如果为真执行第一个,否则执行第二个。"

例：
      test ? expression1 : expression2
test 任何 Boolean 表达式。
expression1 test 为 true 时返回的表达式。可能是逗点表达式。
expression2 test 为 false 时返回的表达式。可能是逗点表达式。

例如：
  
      string prm1="4"; 
      string prm2="5";
      string prm3 = prm1==prm2?"yes":"no" // 此时prm3值为"no".
  
3.   空合并运算符(？？)：
  
空合并运算符 (null coalescing operator) ??
  
用于定义可空类型和引用类型的默认值。如果此运算符的左操作数不为 null，则此运算符将返回左操作数；否则返回右操作数。
  
例：a??b 如果 a 为非空，则 a ?? b 的结果为 a；否则结果为 b 。
  
      List<string> list=null;
      List<string> list1=list??new List<string>();//如果list为null，list1就会为一个新
      //的实例
  
空合并运算符为右结合运算符，即操作时从右向左进行组合的。

例：“a??b??c”的形式按“a??(b??c)”计算。  
  
4. 实体变量名之后加？
  
          string s = "123456789";
          var r1 = s?.Last();
          s = null;
          var r2 = s?.Last();  
  
  当变量不为null时，正常执行；当变量为null时，返回null。
