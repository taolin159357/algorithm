* 默认情况下，Python 3 源码文件以 UTF-8 编码，所有字符串都是 unicode 字符串。 当然你也可以为源码文件指定不同的编码：

  ```python
  # -*- coding:utf-8 -*-
  ```

* 标识符

  * 第一个字符必须是字母表中字母或下划线 _ 。
  * 标识符的其他的部分由字母、数字和下划线组成。
  * 标识符对大小写敏感。
  * 在 Python 3 中，可以用中文作为变量名，非 ASCII 标识符也是允许的了。

* python保留字

  保留字即关键字，我们不能把它们用作任何标识符名称。Python 的标准库提供了一个 keyword 模块，可以输出当前版本的所有关键字：

  ```python
  >>> import keyword
  >>> keyword.kwlist
  ['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 
  'del','elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 
  'is', 'lambda', 'nonlocal','not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 
  'yield']
  ```

* 注释：单行注释以 # 开头，多行注释有 ''' 和 """

* python最具特色的就是使用缩进来表示代码块，不需要使用大括号{}；缩进的空格数是可变的，但是同一个代码块的语句必须包含相同的缩进空格数。


* Python 通常是一行写完一条语句，但如果语句很长，我们可以使用反斜杠(\)来实现多行语句，在 [], {}, 或 () 中的多行语句，不需要使用反斜杠

* Python3 的六个标准数据类型中：

  * 不可变数据（3 个）：Number（数字）、String（字符串）、Tuple（元组）；

    * python中数字有四种类型：int (整数)、bool (布尔)、float (浮点数)和complex (复数)；可用math库

      内置的 type() 函数可以用来查询变量所指的对象类型，type()不会认为子类是一种父类类型；此外还可以用 isinstance 来判断isinstance(a, int)，isinstance()会认为子类是一种父类类型。

      在 Python2 中是没有布尔型的，它用数字 0 表示 False，用 1 表示 True；到 Python3 中，把 True 和 False 定义成关键字了，但它们的值还是 1 和 0，它们可以和数字相加。

    * 字符串(String)，常用内建函数

      * python中单引号和双引号使用完全相同。
      * 使用三引号('''或""")可以指定一个多行字符串。
      * 转义符 '\'反斜杠可以用来转义，使用r可以让反斜杠不发生转义。如 r"this is a line with \n" 则\n会显示，并不是换行。
      * 按字面意义级联字符串，如"this " "is " "string"会被自动转换为this is string。
      * 字符串可以用 + 运算符连接在一起，用 * 运算符重复。
      * Python 中的字符串有两种索引方式，从左往右以 0 开始，从右往左以 -1 开始。
      * Python中的字符串不能改变。
      * Python 没有单独的字符类型，一个字符就是长度为 1 的字符串。字符串的截取的语法格式如下：变量[头下标:尾下标:步长]
      * f-string 格式话字符串以 f 开头，后面跟着字符串，字符串中的表达式用大括号 {} 包起来，它会将变量或表达式计算后的值替换进去

    * 元组（tuple）与列表类似，不同之处在于元组的元素不能修改；元组写在小括号 () 里，元素之间用逗号隔开；元组中的元素类型也可以不相同；元组也可以使用+操作符进行拼接；我们可以使用del语句来删除整个元组；元组内置函数

  * 可变数据（3 个）：List（列表）、Dictionary（字典）、Set（集合）。

    * 列表中元素的类型可以不相同，它支持数字，字符串甚至可以包含列表（所谓嵌套）；和字符串一样，列表同样可以被索引和截取，列表被截取后返回一个包含所需元素的新列表；List可以使用+操作符进行拼接；可以使用 del 语句来删除列表的的元素；在序列中遍历时，索引位置和对应值可以使用 enumerate() 函数同时得到；同时遍历两个或更多的序列，可以使用 zip() 组合；列表函数&方法

    * 可以使用大括号 { } 或者 set() 函数创建集合，注意：创建一个空集合必须用 set() 而不是 { }，因为 { } 是用来创建一个空字典；集合内置方法

    * 字典是一种映射类型，字典用 { } 标识，它是一个无序的 键(key) : 值(value) 的集合；键(key)必须使用不可变类型；在同一个字典中，键(key)必须是唯一的；构造函数 dict() 可以直接从键值对序列中构建字典；在字典中遍历时，关键字和对应的值可以使用 items() 方法同时解读出来；内置函数&方法

      ```python
      >>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
      >>> for k, v in knights.items():
      ...     print(k, v)
      ...gallahad the pure
      robin the brave
      
      >>> for i, v in enumerate(['tic', 'tac', 'toe']):
      ...     print(i, v)
      ...
      0 tic
      1 tac
      2 toe
      
      >>> questions = ['name', 'quest', 'favorite color']
      >>> answers = ['lancelot', 'the holy grail', 'blue']
      >>> for q, a in zip(questions, answers):
      ...     print('What is your {0}?  It is {1}.'.format(q, a))
      ...
      What is your name?  It is lancelot.
      What is your quest?  It is the holy grail.
      What is your favorite color?  It is blue.
      
      >>> for i in reversed(range(1, 10, 2)):
      ...     print(i)
      ...
      9
      7
      5
      3
      1
      ```

* Python数据类型转换

  | 函数                  | 描述                                                |
  | --------------------- | --------------------------------------------------- |
  | int(x [,base])        | 将x转换为一个整数                                   |
  | float(x)              | 将x转换到一个浮点数                                 |
  | complex(real [,imag]) | 创建一个复数                                        |
  | str(x)                | 将对象 x 转换为字符串                               |
  | repr(x)               | 将对象 x 转换为表达式字符串                         |
  | eval(str)             | 用来计算在字符串中的有效Python表达式,并返回一个对象 |
  | tuple(s)              | 将序列 s 转换为一个元组                             |
  | list(s)               | 将序列 s 转换为一个列表                             |
  | set(s)                | 转换为可变集合                                      |
  | dict(d)               | 创建一个字典。d 必须是一个 (key, value)元组序列。   |
  | frozenset(s)          | 转换为不可变集合                                    |
  | chr(x)                | 将一个整数转换为一个字符                            |
  | ord(x)                | 将一个字符转换为它的整数值                          |
  | hex(x)                | 将一个整数转换为一个十六进制字符串                  |
  | oct(x)                | 将一个整数转换为一个八进制字符串                    |

* Python3 运算符

  **：幂 - 返回x的y次幂；

  //：取整除 - 向下取接近除数的整数；

  :=：海象运算符，可在表达式内部为变量赋值，Python3.8 版本新增运算符；

  ~：按位取反运算符，对数据的每个二进制位取反,即把1变为0,把0变为1，~x 类似于 -x-1；

  and、or、not；

  in、not in：包括字符串，列表或元组；

  身份运算符用于比较两个对象的存储单元：is：判断两个标识符是不是引用自一个对象，x is y, 类似 id(x) == id(y) ,id() 函数用于获取对象内存地址；is not：判断两个标识符是不是引用自不同对象

* Python可以在同一行中使用多条语句，语句之间使用分号(;)分割

* 缩进相同的一组语句构成一个代码块，我们称之代码组。像if、while、def和class这样的复合语句，首行以关键字开始，以冒号( : )结束，该行之后的一行或多行代码构成代码组。我们将首行及后面的代码组称为一个子句(clause)。


* print 默认输出是换行的，如果要实现不换行需要在变量末尾加上 end=""

* 在 python 用 import 或者 from...import 来导入相应的模块。

* Python 中的变量不需要声明。每个变量在使用前都必须赋值，变量赋值以后该变量才会被创建。在 Python 中，变量就是变量，它没有类型，我们所说的"类型"是变量所指的内存中对象的类型。


* Python 中用 elif 代替了 else if，所以if语句的关键字为：if – elif – else；每个条件后面要使用冒号 :，表示接下来是满足条件后要执行的语句块；在Python中没有switch – case语句
* 在 while … else 在条件语句为 false 时执行 else 的语句块

* for循环可以遍历任何序列的项目，如一个列表或者一个字符串；如果你需要遍历数字序列，可以使用内置range()函数，它会生成数列；

* Python pass是空语句，是为了保持程序结构的完整性。

* 迭代器有两个基本的方法：iter() 和 next()。

  ```python
  >>> list=[1,2,3,4]
  >>> it = iter(list)    # 创建迭代器对象
  >>> print (next(it))   # 输出迭代器的下一个元素
  1
  >>> print (next(it))
  2
  >>>
  
  # for循环使用迭代器
  list=[1,2,3,4]
  it = iter(list)    # 创建迭代器对象
  for x in it:
      print (x, end=" ")
  
  # 结合使用
  import sys         # 引入 sys 模块
  
  list=[1,2,3,4]
  it = iter(list)    # 创建迭代器对象
   
  while True:
      try:
          print (next(it))
      except StopIteration:
          sys.exit()
  ```

  把一个类作为一个迭代器使用需要在类中实现两个方法 \_\_iter\_\_() 与 \_\_next\_\_() ，StopIteration 异常用于标识迭代的完成，防止出现无限循环的情况，在 \_\_next\_\_() 方法中我们可以设置在完成指定循环次数后触发 StopIteration 异常来结束迭代。

  ```python
  class MyNumbers:
    def __iter__(self):
      self.a = 1
      return self
   
    def __next__(self):
      if self.a <= 20:
        x = self.a
        self.a += 1
        return x
      else:
        raise StopIteration
   
  myclass = MyNumbers()
  myiter = iter(myclass)
   
  for x in myiter:
    print(x)
  ```

  在 Python 中，使用了 yield 的函数被称为生成器（generator）。跟普通函数不同的是，生成器是一个返回迭代器的函数，只能用于迭代操作，更简单点理解生成器就是一个迭代器。在调用生成器运行的过程中，每次遇到 yield 时函数会暂停并保存当前所有的运行信息，返回 yield 的值, 并在下一次执行 next() 方法时从当前位置继续运行。调用一个生成器函数，返回的是一个迭代器对象。

  ```python
  import sys
   
  def fibonacci(n): # 生成器函数 - 斐波那契
      a, b, counter = 0, 1, 0
      while True:
          if (counter > n): 
              return
          yield a
          a, b = b, a + b
          counter += 1
  f = fibonacci(10) # f 是一个迭代器，由生成器返回生成
   
  while True:
      try:
          print (next(f), end=" ")
      except StopIteration:
          sys.exit()
          
  输出：0 1 1 2 3 5 8 13 21 34 55
  ```

* 函数不定长参数：加了星号 * 的参数会以元组(tuple)的形式导入，存放所有未命名的变量参数（默认）；加了两个星号 ** 的参数会以字典的形式导入。

* python 使用 lambda 来创建匿名函数：lambda [arg1 [,arg2,.....argn]]:expression

* Python3.8 新增了一个函数形参语法 / 用来指明/以前的函数形参必须使用指定位置参数，不能使用关键字参数的形式。

* 每个列表推导式都在 for 之后跟一个表达式，然后有零到多个 for 或 if 子句。返回结果是一个根据表达从其后的 for 和 if 上下文环境中生成出来的列表。如果希望表达式推导出一个元组，就必须使用括号。

  ```python
  >>> [3*x for x in vec if x > 3]
  [12, 18]
  >>> vec1 = [2, 4, 6]
  >>> vec2 = [4, 3, -9]
  >>> [x*y for x in vec1 for y in vec2]
  [8, 6, -18, 16, 12, -36, 24, 18, -54]
  >>> [x+y for x in vec1 for y in vec2]
  [6, 5, -7, 8, 7, -5, 10, 9, -3]
  >>> [vec1[i]*vec2[i] for i in range(len(vec1))]
  [8, 12, -54]
  ```

* import搜索路径被存储在sys模块中的path变量，可以使用模块名称来访问函数；内置的函数 dir() 可以找到模块内定义的所有名称，以一个字符串列表的形式返回

* 一个模块被另一个程序第一次引入时，其主程序将运行。如果我们想在模块被引入时，模块中的某一程序块不执行，我们可以用\_\_name\_\_属性来使该程序块仅在该模块自身运行时执行。每个模块都有一个\_\_name\_\_属性，当其值是'\_\_main\_\_'时，表明该模块自身在运行，否则是被引入。

* 包是一种管理 Python 模块命名空间的形式，采用"点模块名称"，比如一个模块的名称是 A.B， 那么他表示一个包 A中的子模块 B；目录只有包含一个叫做 \_\_init\_\_.py 的文件才会被认作是一个包；

  注意当使用 from package import item 这种形式的时候，对应的 item 既可以是包里面的子模块（子包），或者包里面定义的其他名称，比如函数，类或者变量。import 语法会首先把 item 当作一个包定义的名称，如果没找到，再试图按照一个模块去导入。如果还没找到，抛出一个 :exc:ImportError 异常。反之，如果使用形如 import item.subitem.subsubitem 这种导入形式，除了最后一项，都必须是包，而最后一项则可以是模块或者是包，但是不可以是类，函数或者变量的名字。

  导入语句遵循如下规则：如果包定义文件 \_\_init\_\_.py 存在一个叫做 \_\_all\_\_ 的列表变量，那么在使用 from package import * 的时候就把这个列表中的所有名字作为包内容导入。在:file:sounds/effects/\_\_init\_\_.py中包含如下代码:\_\_all\_\_ = ["echo", "surround", "reverse"]表示当你使用from sound.effects import *这种用法时，你只会导入包里面这三个子模块。

* 类有一个名为 \_\_init\_\_() 的特殊方法（构造方法），该方法在类实例化时会自动调用；类的方法与普通的函数只有一个特别的区别——它们必须有一个额外的第一个参数名称, 按照惯例它的名称是 self，self 代表的是类的实例，代表当前对象的地址，而 self.class 则指向类。

* Python同样有限的支持多继承形式，若是父类中有相同的方法名，而在子类使用时未指定，python从左至右搜索 即方法在子类中未找到时，从左到右查找父类中是否包含方法。

* 类的私有属性：\_\_private_attrs：两个下划线开头，声明该属性为私有，不能在类的外部被使用或直接访问。在类内部的方法中使用时 self.\_\_private_attrs；类的私有方法：\_private_method：两个下划线开头，声明该方法为私有方法，只能在类的内部调用 ，不能在类的外部调用self.\_\_private_methods。

* 类的专有方法：\_\_init\_\_ : 构造函数，在生成对象时调用；\_\_del\_\_ : 析构函数，释放对象时使用；\_\_repr\_\_ : 打印，转换；\_\_setitem\_\_ : 按照索引赋值；\_\_getitem\_\_: 按照索引获取值；\_\_len\_\_: 获得长度；\_\_cmp\_\_: 比较运算；\_\_call\_\_: 函数调用；\_\_add\_\_: 加运算；\_\_sub\_\_: 减运算；\_\_mul\_\_: 乘运算；\_\_truediv\_\_: 除运算；\_\_mod\_\_: 求余运算；\_\_pow\_\_: 乘方；

  Python同样支持运算符重载，我们可以对类的专有方法进行重载，重载就是重写上面的运算符方法

* 函数内的函数可以引用外部变量，但是不可以对其进行修改，当内部作用域想修改外部作用域的变量时，就要用到global和nonlocal关键字，如果要修改嵌套作用域（enclosing 作用域，外层非全局作用域）中的变量则需要 nonlocal 关键字；组合数据（如列表）除外；

* Python3 标准库概览
  * 操作系统接口：os模块
  * 文件通配符：glob模块
  * 字符串正则匹配：re模块
  * 数学：math模块
  * 访问互联网：urllib和smtplib
  * 日期和时间：datetime模块
  * 数据压缩：zlib，gzip，bz2，zipfile，以及 tarfile
  * 性能度量：timeit模块
  * 测试模块：doctest和unittest

* 函数注解：用 : 类型 的形式指定函数的参数类型，用 -> 类型 的形式指定函数的返回值类型。
