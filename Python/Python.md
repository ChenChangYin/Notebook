# Python

**Python 是一个动态的解释型(字节码编译)语言，他在运行之前不会去对代码做额外的"翻译"的工作，计算机会直接在它被运行的时候，一边理解和执行它，一边判断程序中是否有造成没有办法执行的部分(语法错误).**

**Python的变量、参数、函数(方法)在声明时否是无需说明类型的；因为Python不需要对类型进行说明，所以用它写出的代码都显得比较短小，同时Python程序中的很多写法也因此而变得非常灵活.**

```python
#初始化
a = 6
print a
b = 'hello world'
print b
a = b
print a, b
#输入　input()
name = raw_input("what is your name:") // 将输入付给name
print 'your name is' + name

#运算
a = 1
b = 2
print a + b
print b * 3
print b + a * 2

#整除　取整除和精确除
print 3 / 2
print 3.0 / 2.0
print 2. / 2.


#从__future__ 包　导入division的方法
from __future__ import division
print 3 / 2
print 3.0 / 2.0
print 2. / 2.
print 3 // 2


#字符串链接
a = 'love '
b = 'China'
print a + b
print a * 3 + b

#字符串长度
#str函数是转换为字符串　len是求长度
a = 'China'
a_len = len(a)
b = 'length of a is'
print b + str(a_len)



def main():
    print 'Hello World'
    
if __name__ == '__main__':
    main()
```

**def 是定义函的关键字　在这个词后隔一个空格后，定义的是这个函数的名称，而在之后里定义的是这个函数所接收的函数的参数形式。而真正利用接收到的参数来进行函数功能性描述的函数的定义，则是在def这行之后，增加了缩进的一系列语句.**

```python
def max_pow(a, b): 
    if a > b:
        pow_ab = a ** b
        return pow_ab
    pow_ba = b ** a
    return pow_ba
```

**def这行以下的所有语句都是属于名为max_pow的这个接收了被定名为a和b的两个函数的参数形式的函数的定义部分.我们看到，在定义部分我们用到了可以被传入的a和b**

**如需调用　max_pow(3, 2)**

如果有需要继续使用函数中的结果，我们可以写上return并在return 语句后紧跟定义的函数被调用后的返回结果



**其中a, b pow_ab, pow_ba都只在函数内部有效**

函数定义要在调用前

```python
def yinhe(a):
    print '='+a+'='

def main():
    print 'niulang'
    yinhe('||')
    print 'zhinv'
    
if __name__ == '__main__':
    main()
```

### 缩进很重要

```python
def do_qingan(my_line):
    print 'gui'
    print 'bai ' * 3
    print my_line

def main():
    my_line = 'wansui'
    do_qingan(my_line)
    
if __name__ == '__main__':
    main()
```

help 和 dir　神器　

```python
import sys
help(len)
print dir(sys)
help(sys.exit)
help('china'.split)
print dir(list)
```

在sys下被定义的exit函数的形式和作用说明、一个字符串(str)下被定义的split函数的形式和作用说明、以及list下所有的被定义的函数方法的列表。

```python
a, b, c = (int(x) for x in raw_input().split(' '))
print a + b + c
```



### Python的字符串

Python 内建了一个专门用于处理字符串的“库”（实际上是一个名为 str 的类），它提供了丰富的功能。在 Python 中的字符串值区别于数值，是用单引号或者双引号进行包裹的（单引号用的更为普遍），如果我们写a = 3,变量ａ指向的是一个储存了数值３的“盒子”，如果我们写a = '3' 变量ａ指向的是一个储存了一个字符串'3'的“盒子”



转义符\ 

或者直接中双引号包含

a = "i don't know"

```python
#用多行来写
a = 'This is a string\
that is so good to \
let you to understand'

```

**Python 中的字符串是不可改变的　也就是一旦创建后皆不可以被做出任何改变**

**ａ = 'hello' + 'there' 实际上是两个已经被创建的字符串　'hello'  和　'there' 来创建的字符串'hellothere', 并且让ａ指向了装着这个新的字符串的“盒子''**

**str = 'hello'   其中str[1] 是e 也是从０位置开始的　如果不存在将会　给我们一个”超出合法范围“的错误**

****

```python
a = 'hello'
b = a[0] + 'i'
print b
print len(b)


#lower()将字符串转小写　　uppper()将字符串转大写

a = 'In\na line'
b = r'In\na line'
#r是单词raw ｂ的\n变为\N
print a
print b
print a.lower()
print b.upper()

s = 'HelloabcdWord'
print s.isalpha()
print s.isdigit()

print s.startswith('Hello')
print s.endswith('word')
```

**isalpha() 检测是否字符串全是由字母组成**

**isdigit()检测是否字符串全是由数字组成**

**isspace()检测是否字符串全是由空格组成**

**startswith()检测是否是一个子字符串开始的**

**endswith()检测是否是一个子字符串结束的**

逆序索引，这个每个字符的逆序索引的值等于它的位置索引的值减去字符串的长度。以我们刚刚提到的字符串 Hello 为例。这个字符串的长度为 5 ，那么它的位置索引为 0 的 H 的逆序索引就是 0 - 5 = -5， 位置索引为 1 的 e 的逆序索引就是 1 - 5 = -4，以此类推。

**例如　Hello**

**a = 'Hello'**

其中print  a[1] 和print a[-4]是一样的盒子

**切取**

tower[a:b] 只去ａ到ｂ的盒子

```python
tower = 'abcdefg'
print tower[1:4]
print tower[3:]
print tower[:-2]

```

### if语句

```python

if a > 0:
    c = a
elif a == 0:
    c = -1
else:
    c = -a
#与　and   或 or 
```

对于上面这个例子，这段程序对 a 进行了判断， 当 a 大于 0 的时候，让 c 被赋值为 a， 当 a 等于 0 的时候让 c 被赋值为 -1，其他情况下（其实这里就只剩下 a 小于 0 的情况），让 c 被赋值为 -a。

```python
#replace 是bag指向的字符串中的全部"nothing" 换为　umbrella
weather = 'rainy day'
bag = 'nothing in the bag'
if weather.find('rain') != -1:
    bag = bag.replace('nothing', 'umbrella')
print bag
```

**字符串格式化**

```python
name = 'Wangmu Niangniang'
age = 9000
height = 1.73
print name + ' is a ' + str(age) + '-year-old woman with height ' + str(height)
print '%s is a %d-year-old woman with height %g' % (name, age, height)

#前面加上u是将s变成Unicode编码的字符串
s = u'I want to say \u4e2d\u56fd\u4e07\u5c81'
print s
#s = s.encode("utd-8")

```

### 列表

```python
list = [100, 23, 45]
print list[0]
print list[1]
print list[2]
#len输出的是元素数量
print len(list)
```



```python
hello = ['hi', 'hello']
world = ['earth', 'field', 'universe']
#append 添加操作
hello.append('nihao')
print hello
#extend 添加列表
hello.extend(world)
print hello


hello = ['hi', 'hello']
#插入到第０位
hello.insert(0, 'nihao')
print hello
#查找hi的位置	
print hello.index('hi')

hello = ['nihao', 'hi', 'hello']
#将'nihao'移除
hello.remove('nihao')
print hello
#将0号移除
hello.pop(0)
print hello


manager = 'tuotatianwang,taibaijinxing,juanliandajiang'
#split函数切割
manager_list = manager.split(',')
print manager_list
new_manager = ' '.join(manager_list)
print new_manager
```

```python

gardens = [7204, 3640, 1200, 1240, 71800, 3200, 604]
total = 0
for num in gardens:
    total += num
print total
print sum(gardens)
```

### range函数

**range(10)将得到一个从0开始，到９结束的队列[0,1,2,3,4,5,6,7,8,9]**

**range第一个参数是起始位置，　第二个是　极值　第三个是差值**

**range(1,10)从１到9**

**range(10, 1, -2) 得到的是 [10, 8, 6, 4, 2]**

**xrange是变参函数与range函数参数一致**

```python
first = 0
second = 1
# Please write code here
while first < 100:
    print first
    first, second = second, first + second
print 'Everything is done'
```



###　斐波那契

```python
#coding=utf-8
n = input()
first = 2
a=1
b=1
c=1
while first < n:
    c = a + b
    a = b
    b = c
    first+=1
print c
```

### 简单的排序

```python
numbers = [1, 4, 2, 3, 8, 3, 0]
X=numbers.sort()
print numbers
print X

#sorted的使用方法　放在括号内
numbers = [1, 4, 2, 3, 8, 3, 0]
print sorted(numbers)
print sorted(numbers, reverse=True)



def china_first(item):
    if item == 'China':
        return 0
    else:
        return len(item)
country = ['jp', 'China', 'USA', 'Thai']
print sorted(country, key = len)
print sorted(country, key = china_first)
```



### 元组

**元组是一个固定大小的一组元素,比如说(x,y)坐标。元组看起来有点像列表，但是它的大小是固定的，不会改变的。访问元组内某个元组的方式和访问列表的元素是一致的**

```python
tuple = (1, 2, 'hi')
print len(tuple)
print tuple[2]
tuple = (1, 2, 'bye')
print tuple
```



```python
nums = [int(x) for x in raw_input().split()]
nums1 = []
nums2 = []
for i in xrange(len(nums)):
    ind = i + 1;
    if ind % 3 != 0 and ind % 2 == 0:
        nums1.append(nums[i])//添加
    elif ind % 3 == 0:
        nums2.append(nums[i])
nums1.sort()
nums2.sort(reverse = True)
for i in xrange(len(nums)):
    ind = i + 1;
    if ind % 3 != 0 and ind % 2 == 0:
        nums[i] = nums1.pop(0)
    elif ind % 3 == 0:
        nums[i] = nums2.pop(0)
print ' '.join(str(x) for x in nums)
```

### 字典

**在python中有一个将名字和值进行配对的结构，叫做字典。就像是一个生活中的字典的每一个词有具体的解释一样, 也有一系列类似的配对　我们称之为键值对，这里每个配对的“名字”叫做键名，这里的每个值我们称之为键值，　以冒号分隔的形式　键名:键值**

**字典在python被定义为一系列用{}包裹键值对的集合。取键值时，需要用字典对应的变量名加放在方括号里键名的方式的而形式，例如对于　dict = {'key1' : 100, 'key2' : 112, ...}的定义，访问print dict['key1']将会得到一个对应的100的输出，类似的，我们也可以使用dict['key1'] = 999的形式修改dict字典中key1键名对应的键值为999**

可以作为键名的常见数据类型包括了字符串、数值和元组，而键值则可以是任何类型的数值。如果使用了错误的键名，将无法取出正确的键值。

```python
bat = {} 
bat['b'] = 'baidu' 
bat['a'] = 'alibaba' 
bat['t'] = 'tencent'
print bat
print bat['a']
bat['a'] = 'amazon'
print bat['a']
print 'b' in bat
print 'x' in bat


bat = {'a': 'alibaba', 'b': 'baidu', 't': 'tencent'}
#键名
print bat.keys()
#键值
print bat.values()
#键名键值
print bat.items()



bat = {'a': 'alibaba', 'b': 'baidu', 't': 'tencent'}
for value in bat.values():
    print value
    
for key in bat:
    print key

for k, v in bat.items():
    print k, '>', v
    
    
boss = {} 
boss['name'] = 'robin' 
boss['age'] = 45
boss['height'] = 1.78
print 'The boss named %(name)s is %(age)d-year-old and %(height)g tall.' %boss


#删除表达式
num = 6
list = ['a', 'b', 'c', 'd']
dict = {'a': 1, 'b': 2, 'c': 3}
del list[0]
del list[-2:]
print list
del dict['b']
print dict
del num
print num
```

### 文件的使用

**Python有一个open函数，这个函数会返回一个可以用于独处和写入文件的文件操作符。我们可以通过　fd = open('filename', 'r')的方式，打开一个文件名叫做filename的文件获取它的文件操作符，并让变量fd指向这个操作符(这列的r标记了文件被打开用于读取).当我们用完这个文件不再继续使用时，我们可以用fd.close()结束对这个文件额的使用。**

**除了使用r来标记用于读取，我们还可以用ｗ来表示写入(a表示后继添加)，这些标记可以被放在一起使用，比如fd = open('filename', 'rw')则表示对这个文件会有读操作也会有写操作。**

**我们可以用标准的for循环来读取一个文件的每一行(仅对文件读取有效，对二进制读取并不能用)。**

```python
#按行输出整个文件
f = open('filename', 'rU')
for line in f:#访问文件每一行
    print line, #打印每一行　添加逗号可以不被额外添加换行
   
```

**每次读取一行的好处是不受内存限制　我们每次把文件的一部分放到内存进行处理**

**我们可以通过调用文件操作符的函数readline(写成fd.readline()),他会一次性加载完整的文件到内存，让文件的每一行作为它这个列表结构的被一个字符串元素。**

**fd.read()则会一次性将完整的文件作为一个字符串读入到内存内。但文件过大的时候这两个函数都会遇到内存问题**

**对于向文件中的写入，我们可以用write函数(写成fd.write(字符串))将指定的字符串写入到文件中，   print >> 文件操作符,字符串　能达到相同的效果**



**在python中有一些已经写好的功能性包称为模组，其中有一个名叫codecs的模组，它提供了读取一个非英文的文件所需要的unicode读取支持**

**让我们使用它时，我们需要通过import将它引入.之后再打开文件时，标记明确所需要的编码字符集(这里我们使用utf-8)**

```python
import codecs
fd = codecs.open('foo.txt', 'rU', 'utf-8')
```

**当读取完并且完成相关的处理成功时，我们需要注意。我们只可以使用fd.write()的形式来进行写出，print并没有完全支持unicode的写出过程。**









### 正则表达式

**正则表达式是一种用于匹配文本形式的强大逻辑表达式，在Pyhon中的re模组提拱了正则表达式的支持。正则表达式由一些普通字符和一些元字符(metacharacters)组成。普通字符包括大小写的字母和数字，而元字符则具有特殊的含义。当正则表达式为一个普通的字符串时，一个正则表达式的匹配行为就是一个普通的字符串查找过程。例如：正则表达式“testing"中没有包含任何元字符，他可以匹配"testing"和"testing23"等字符串，但因为大小太敏感，他不能匹配到"Testing"。其他一些元字符则不会被作为普通字符来处理，它们包括 .^$*+?{[]\\|()　**

**.会匹配除了换行以外的任何字符；**

**\w等价于[a-zA-Z0-9_]会匹配到单一字母、数字或下划线字符,**

**\W则会匹配任何非字母、数字和下划线的单一字符；**

**\b会匹配“单一字母、数字或下划线字符”和“任何非字母、数字和下划线的单一字符”之间的边界。**

**\s等价于[ \n\r\t\f]，会匹配一个空白字符（包括空格、换行、返回、制表符、表格）**

**\S则匹配所有非空白字符**

**\t \n \r依次用于匹配制表符、换行符、返回符**

**\d等价于[0-9]用于匹配十进制表示的的数字**

**^作为标记，**

**$作为结束标记，分别用于标记一个字符串**

**\用于一些字符的转义，比如\\.表示对于一个真实点字符的匹配，**

**\\\表示对于一个真实反斜杠字符的匹配等。如果你对不是很确定一些字符是否需要进行转义才能匹配，你大可都加上斜杠，比如对于@你写成\@是一定没有问题的**



**计算客　俩数求和**

```python
def two_sum(nums, target):
    ans = dict()
    for i in xrange(1, len(nums) + 1):
        num1 = nums[i - 1]
        num2 = target - nums[i - 1]
        if num1 in ans.keys():
            return ans[num1], i
        ans[num2] = i
    return 0, 0
if __name__ == "__main__":
    raw_input()
    nums = [int(x) for x in raw_input().split()]
    target = int(raw_input())
    print "%d %d" % two_sum(nums, target)
```

**正则表达式查找**

```python
import re
str = 'A cute word:cat!!'
match = re.search(r'word:\w\w\w', str)
if match:
    print 'found', match.group()
```

**基础正则使用**

```python
import re
print re.search(r'..g', 'piiig').group()
print re.search(r'\d\d\d', 'p123g').group()
print re.search(r'\w\w\w', '@@abcd!!').group()

输出
iig                                                                   
123                                                                   
abc
```





```python
import re
print re.search(r'pi+', 'piiig').group()
print re.search(r'pi*', 'pg').group()
```



```python
import re
#输出a-c
print re.search(r'[abc]+', 'xxxacbbcbbadddedede').group()
#输出a-d
print re.search(r'[a-d]+', 'xxxacbbcbbadddedede').group()



import re
str = 'purple alice-b@jisuanke.com monkey dishwasher'
match = re.search('[\w.-]+@([\w.-]+)', str)
if match:
    print match.group()
    print match.group(1)
    print match.group(2)
    
import re
str = 'purple alice@jisuanke.com, blah monkey bob@abc.com blah dishwasher'
tuplea = re.findall(r'([\w\.-]+)@([\w\.-]+)', str)
print tuplea
```



**选项与贪心匹配**

**在用于正则表达式的re模组中的函数有一些可选参数，我们可以对search()函数或者findall()函数传入额外的参数来进行使用，如re.search(pat, re.IGNORECASE)中的re.IGNOrECASE就是使用了re中的一个标记作为额外的参数。**

**在re模组中，提供了很多不同的可选参数，其中上面提到的IGNORECASE表示了让匹配是忽略大小写的区别；而另外一个可选参数DOTALL如果被添加，则会允许正则中的`.`去跨行匹配,加了这个参数之后`.*`这样的匹配方式，将可以跨行进行匹配，而不只是在行内进行。另外，还有一个可选参数是MUTILINE，使用他以后，对于一个多行文本组成的字符串，^和$将可以用于匹配每一行的开始和结束，而如果没有用它时^和$只会匹配整个字符串的开始和结束。除了可选参数之外，我们还需要理解一下正则匹配的“贪心情况”。　假设我们有一段文字`<b>foo</b> and <i>so on</i>`而你希望匹配(<.*>)提取的所用HTML标签，你觉得会是怎么样呢？我们可以得到期望的`<b>, </b>, <i>, </i>`这样的结果么？**

**事实上的结果可能会有点出乎你的意料，因为`.*` 这样的匹配是“贪心”的，它会尽可能去得到较长的匹配结果，因此我们会得到的是一整个`<b>foo</b> and <i>so on</i>`作为匹配出的结果。如果我们希望获得期望中的结果，我们就需要这个匹配是非贪心的，在正则表达式中，我们对于`*`和`+`这种默认贪心的匹配可以加上`?`使之变为不贪心的。也就是说，如果我们将`(<.*>)改成`(<.*?>)``正则表达式会先匹配`<b>``，然后匹配``</b>``,接下来分别是``<i>`` 和　``</i>``。这样的匹配结果与我们预期完全一致。相应的，对于一些用到了`+`的情况，我们可以将`+`变为`+?`来进行非贪心的匹配。**

### 统计字符个数

```python
def cnt_letter_number(string):
    t = (
         len([x for x in string if x.isalpha()]),
         len([x for x in string if x.isdigit()]),
         len([x for x in string if x == ' ']),
         )
    return t + (len(string) - sum(t),)

if __name__ == "__main__":
    print "%d %d %d %d" % cnt_letter_number(raw_input())
```

