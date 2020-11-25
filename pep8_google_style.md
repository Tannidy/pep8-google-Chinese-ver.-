
# pep8 (google style)

### 1.行长度

每行不超过80个字符。 

例外:

1.长的导入模块语句

2.注释里的URL



不要使用反斜杠连接行。

Python会将 圆括号,中括号和花括号中的行隐式的连接起来,你可以利用这个特点。如果需要,你可以在表达式外围增加一对额外的圆括号。


```python
Yes: foo_bar(self, width, height, color='black', design=None, x='foo',
             emphasis=None, highlight=0)

     if (width == 0 and height == 0 and
         color == 'red' and emphasis == 'strong'):
```

如果一个文本字符串在一行放不下, 可以使用圆括号来实现隐式行连接:


```python
x = ('This will build a very long long '
     'long long long long long long string')
```

在注释中，如果必要，将长的URL放在一行上。


```python
Yes:  # See details at
      # http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```


```python
No:  # See details at
     # http://www.example.com/us/developer/documentation/api/content/\
     # v2.0/csv_file_name_extension_full_specification.html

```

### 2.缩进

用4个空格来缩进代码。

绝对不要用tab, 也不要tab和空格混用。


```python
Yes:   # Aligned with opening delimiter
       foo = long_function_name(var_one, var_two,
                                var_three, var_four)

       # Aligned with opening delimiter in a dictionary
       foo = {
           long_dictionary_key: value1 +
                                value2,
           ...
       }

       # 4-space hanging indent; nothing on first line
       foo = long_function_name(
           var_one, var_two, var_three,
           var_four)

       # 4-space hanging indent in a dictionary
       foo = {
           long_dictionary_key:
               long_dictionary_value,
           ...
       }
```


```python
No:    # Stuff on first line forbidden
      foo = long_function_name(var_one, var_two,
          var_three, var_four)

      # 2-space hanging indent forbidden
      foo = long_function_name(
        var_one, var_two, var_three,
        var_four)

      # No hanging indent in a dictionary
      foo = {
          long_dictionary_key:
              long_dictionary_value,
              ...
      }
```

### 3.空格

按照标准的排版规范来使用标点两边的空格。

括号内不要有空格。


```python
Yes: spam(ham[1], {eggs: 2}, [])
    
No:  spam( ham[ 1 ], { eggs: 2 }, [ ] )
```

不要在逗号, 分号, 冒号前面加空格, 但应该在它们后面加(除了在行尾)。


```python
Yes: if x == 4:
         print x, y
     x, y = y, x

```


```python
No:  if x == 4 :
         print x , y
     x , y = y , x

```

参数列表, 索引或切片的左括号前不应加空格。


```python
Yes: spam(1)
    
no: spam (1)
```


```python
Yes: dict['key'] = list[index]

No:  dict ['key'] = list [index]
```

在二元操作符两边都加上一个空格。

比如赋值(=), 比较(==, <, >, !=, <>, <=, >=, in, not in, is, is not), 布尔(and, or, not)。

至于算术操作符两边的空格该如何使用, 需要你自己好好判断. 不过两侧务必要保持一致.


```python
Yes: x == 1
    
No:  x<1
```

当’=’用于指示关键字参数或默认参数值时, 不要在其两侧使用空格。


```python
Yes: def complex(real, imag=0.0): return magic(r=real, i=imag)
```


```python
No:  def complex(real, imag = 0.0): return magic(r = real, i = imag)
```

不要用空格来垂直对齐多行间的标记, 因为这会成为维护的负担(适用于:, #, =等):


```python
Yes:
     foo = 1000  # comment
     long_name = 2  # comment that should not be aligned

     dictionary = {
         "foo": 1,
         "long_name": 2,
         }
```


```python
No:
     foo       = 1000  # comment
     long_name = 2     # comment that should not be aligned

     dictionary = {
         "foo"      : 1,
         "long_name": 2,
         }
```

### 4.注释

确保对模块, 函数, 方法和行内注释使用正确的风格

#### 文档字符串

我们对文档字符串的惯例是使用三重双引号”“”( PEP-257 )。

一个文档字符串应该这样组织: 首先是一行以句号, 问号或惊叹号结尾的概述(或者该文档字符串单纯只有一行)。

接着是一个空行. 接着是文档字符串剩下的部分, 它应该与文档字符串的第一行的第一个引号对齐。

下面有更多文档字符串的格式化规范。

#### 类

类应该在其定义下有一个用于描述该类的文档字符串。

如果你的类有公共属性(Attributes), 那么文档中应该有一个属性(Attributes)段。并且应该遵守和函数参数相同的格式。


```python
class SampleClass(object):
    """Summary of class here.

    Longer class information....
    Longer class information....

    Attributes:
        likes_spam: A boolean indicating if we like SPAM or not.
        eggs: An integer count of the eggs we have laid.
    """

    def __init__(self, likes_spam=False):
        """Inits SampleClass with blah."""
        self.likes_spam = likes_spam
        self.eggs = 0

    def public_method(self):
        """Performs operation blah."""

```

#### 块注释和行注释

最需要写注释的是代码中那些技巧性的部分。

如果你在下次 代码审查 的时候必须解释一下, 那么你应该现在就给它写注释。

对于复杂的操作, 应该在其操作开始前写上若干行注释。

对于不是一目了然的代码, 应在其行尾添加注释。


```python
# We use a weighted dictionary search to find out where i is in
# the array.  We extrapolate position based on the largest num
# in the array and the array size and then do binary search to
# get the exact number.

if i & (i-1) == 0:        # True if i is 0 or a power of 2.
```

为了提高可读性, 注释应该至少离开代码2个空格。

另一方面, 绝不要描述代码。假设阅读代码的人比你更懂Python, 他只是不知道你的代码要做什么。


```python
# BAD COMMENT: Now go through the b array and make sure whenever i occurs
# the next element is i+1
```

### 5.Main

即使是一个打算被用作脚本的文件, 也应该是可导入的。
并且简单的导入不应该导致这个脚本的主功能(main functionality)被执行, 这是一种副作用。
主功能应该放在一个main()函数中。

在Python中, pydoc以及单元测试要求模块必须是可导入的。
你的代码应该在执行主程序前总是检查 if __name__ == '__main__' , 这样当模块被导入时主程序就不会被执行。


```python
def main():
      ...

if __name__ == '__main__':
    main()
```

所有的顶级代码在模块导入时都会被执行. 要小心不要去调用函数, 创建对象, 或者执行那些不应该在使用pydoc时执行的操作。

### 6.命名

#### 应该避免的名称

1.单字符名称, 除了计数器和迭代器.

2.包/模块名中的连字符(-)

3.双下划线开头并结尾的名称(Python保留, 例如__init__)

#### 命名约定

1.所谓”内部(Internal)”表示仅模块内可用, 或者, 在类内是保护或私有的.

2.用单下划线(_)开头表示模块变量或函数是protected的(使用from module import *时不会包含).

3.用双下划线(__)开头的实例变量或方法表示类内私有.

4.将相关的类和顶级函数放在同一个模块里. 不像Java, 没必要限制一个类一个模块.

5.对类名使用大写字母开头的单词(如CapWords, 即Pascal风格), 但是模块名应该用小写加下划线的方式(如lower_with_under.py). 尽管已经有很多现存的模块使用类似于CapWords.py这样的命名, 但现在已经不鼓励这样做, 因为如果模块名碰巧和类名一致, 这会让人困扰.

#### Python之父Guido推荐的规范


```python

```
