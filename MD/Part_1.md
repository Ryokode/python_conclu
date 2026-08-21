## ASCII 字符代码表
![e6ff5e187d7c6bade4d191224b19efd1.jpg](https://raw.githubusercontent.com/Ryokode/PicGo/main/e6ff5e187d7c6bade4d191224b19efd1.jpg)


## 条件表达式
- ......if...else......，结果为True则执行或输出if前的内容，False则执行或输出else后的内容


## Pass
- pass语句什么都不做，只是一个占位符，用到需要写语句的地方保证不报错


## range()
- range(start,stop,step)创建一个(start,stop)之间的整数序列，步长为step
	- start不填写则默认从0开始
	- stop的数字表示到这个数为止(不包括stop)即最后一个数为stop-step
	- step表示列表中增减的步长
	- num in or not in range(start,stop,step)表示num在或不在range所创的列表中，一般用一个变量来接收range生成的列表，返回值为True/False


## else语句
- 与else语句配合使用的三种情况
	- else与if搭配使用时，if条件表达式不成立时执行else
	- else与while或for搭配使用时，没有碰到break时执行else（即正常情况下循环体中没有break时程序执行完循环体内else前的内容时会继续执行else后的内容）
e.g:
```python
	  for item in range(3):
		  pwd = input('请输入密码：')
		  if pwd == '8888':
			  print('密码正确')
			  break
		  else:
			  print('密码错误')
	  else:
		    print('对不起，三次密码均错误')
```


## 二重循 环中的break和continue
- 二重循环中的break和continue用于控制本层循环


## 列表
<div align="center"><img src= "https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819170618593.png" alt=""></div>

![](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819171737582.png)
### 创建列表方式
```python
#第一种方式，使用[]
	lst = ['hello','world',98];
#第二种方式，使用内置函数list()
	lst2 = list(['hello','world',98]);
```

### 列表的特点
- 列表元素按顺序有序排序
- 索引映射唯一数据
- 列表可以存储重复数据
- 任意数据类型混存
- 根据需要动态分配和回收内存

### 列表的查询操作
#### 获取列表中指定元素的索引
<div align="center"><img src= "https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819173430644.png" alt=""></div>

#### 获取列表中的单个元素
<div align="center"><img src= "https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819173704322.png" alt=""></div>

#### 获取列表中的多个元素
<div align="center"><img src= "https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819180100372.png" alt=""></div>

- 切片范围左闭右开$[start,stop)$不包括stop本身
e.g:
```python
  lst = [10,20,30,40,50,60,70,80];
  print('原列表',lst);
  print('原列表',id(lst));
  lst2 = lst[1:6:1];
  print('切的片段：',lst2);
  print('切的片段：',id(lst2));
  
  print(lst[1:6:]);
  #默认步长为1
  print(lst[:6:2]);
  #start默认为0
  print(lst[1::2]);
  #stop默认截到最后一个元素
  
  #step为负数时，将列表逆序输出
  print(lst[::-1]);
  print(lst[7::-1]);
  #结果相同，均为[80,70,60,50,40,30,20,10]
  
  print(lst[6:0:-2]);
  #结果为[70,50,30]，不包括stop=0
```
#### 判断指定元素在列表中是否存在
- 使用in或not in来判断
	- 元素 in 列表名
	- 元素 not in 列表名
- 列表元素的遍历
	- for 迭代变量 in 列表名 :

e.g:
```python
lst = [10,20,'python','hello'];
print(10 in lst);#True
print(100 in lst);#False
print(10 not in lst);#False
print(100 not in lst);#True

for item in lst:
	print(item);
```

### 列表元素的增删改排操作
#### 列表元素的增加操作
|  方法/其他   |       操作描述       |
| :------: | :--------------: |
| append() |   在列表的末尾添加一个元素   |
| extend() |  在列表的末尾至少添加一个元素  |
| insert() |  在列表的任意位置添加一个元素  |
|    切片    | 在列表的任意位置至少添加一个元素 |

e.g:
```python
#像列表的末尾添加一个元素
lst = [10,20,30];
print('添加元素前：',lst,id(lst));
lst.append(100);
print('添加元素后：',lst,id(lst));
#两者id显示结果一样

lst2 = ['hello','world'];
lst.append(lst2);    #将lst2作为一个元素添加到列表的末尾
print(lst);
#结果显示：[10,20,30,100,['hello','world']]

lst2 = ['hello','world'];
lst.extend(lst2);    #向列表的末尾一次性添加多个元素
print(lst);
#结果显示：[10,20,30,100,'hello','world']

#在任意位置上插入一个元素
lst.insert(1,90);
print(lst);
#结果显示：[10,90,30,100,'hello','world']

#在任意位置上插入N个元素，正确来说是将切片[start:stop:step]中start的位置部分切掉(包括start)再替换成后面的列表
lst3 = [True,False,'hi'];
lst[1:] = lst3;
print(lst);
#结果显示：[10,True,False,'hi']
```

#### 列表元素的删除操作

<table style="width:100%;text-align: center;vertical-align: middle">
	<tr>
		<th style="text-align: center; vertical-align: middle">方法/其他</th>
		<th style="text-align: center; vertical-align: middle">操作描述</th>
	</tr>
	<tr>
		<td rowspan="3" style="text-align: center; vertical-align: middle">remove()</td>
		<td>一次删除一个元素</td>
	</tr>
	<tr>
	    <td>重复元素只能删除一个</td>
	</tr>
	<tr>
		<td>元素不存在则抛出ValueError</td>
	</tr>
	<tr>
		<td rowspan="3" style="text-align: center; vertical-align: middle">pop()</td>
		<td>删除一个指定索引位置上的元素</td>
	</tr>
	<tr>
	    <td>指定索引不存在则抛出IndexError</td>
	</tr>
	<tr>
		<td>不指定索引，删除列表中最后一个元素</td>
	</tr>
	<tr>
		<td style="text-align: center; vertical-align: middle">切片</td>
		<td>一次至少删除一个元素</td>
	</tr>
	<tr>
		<td style="text-align: center; vertical-align: middle">clear()</td>
		<td>清空列表</td>
	</tr>
	<tr>
		<td style="text-align: center; vertical-align: middle">del</td>
		<td>删除列表</td>
	</tr>
</table>

e.g:
```python
#remove()
lst=[10,20,30,40,50,60,30];
lst.remove(30);    #30为重复元素，只删除第一个30
print(lst);
#结果显示：[10,20,40,50,60,30]

#pop()根据索引移除元素
lst.pop(1);
print(lst);
#结果显示：[10,40,50,60,30]
lst.pop();    #不指定索引，删除列表中最后一个元素
print(lst);
#结果显示：[10,40,50,60]

#切片
new_list = lst[1:3];  #取切片索引1到3的数据，不包括3，生成一个新列表对象
print(lst);
#结果显示：[10,40,50,60] 
print(new_list);
#结果显示：[40,50] 
lst[1:3] = [];#不产生新列表对象，而是删除原列表内容，即用空列表替代切片内容
print(lst);
#结果显示：[10,60]

#clear()
lst.clear();
print(lst);
#结果显示：[]

#del
lst.del;
print(lst);
#结果显示：NameError:name 'lst' is not defined
```

#### 列表元素的修改操作
- 为指定索引的元素赋予一个新值
- 为指定的切片赋予一个新值

e.g:
```python
#一次修改一个值
lst = [10,20,30,40];
lst[2] = 100;
print(lst);
#结果为：[10,20,100,40]

#修改列表当中的多个值
lst[1:3] = [300,400,500,600];#将索引为1,2的值替换为300,400,500,600
print(lst);
#结果为：[10,300,400,500,600,40]
```

#### 列表元素的排序操作
- 常见的两种方法
	- 调用sort()方法，列表中的所有元素默认按照从小到大的顺序排序，可以指定reverse=True进行降序排序
	- 调用内置函数sorted()，可以指定reverse=True进行降序排序，**原列表不发生改变**

e.g:
```python
#使用sort()方法
lst = [20,40,10,98,54];
print('排序前的列表',lst,id(lst));
lst.sort();
print('排序后的列表',lst,id(lst));
#排序后升序排序，列表id相同，说明sort()方法是在原列表的基础上进行的
lst.sort(reverse=True);
print(lst);
lst.sort(reverse=False);
print(lst);
#reverse=True表示降序排序，reverse=False表示升序排序

#使用内置函数sorted()，生成一个新列表，原列表不变
new_list = sorted(lst);
print(lst);
#结果为：[20,40,10,98,54]
print(new_list);
#结果为：[10,20,40,54,98]
#同样reverse
desc_list = sorted(lst,reverse=True);
print(desc_list);
#结果为：[98,54,40,20,10]
```

### 列表生成式
- 列表生成式简称“生成列表的公式“
	- 语法格式：
	 ![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819225546262.png)
	- 注意事项：”表示列表元素的表达式“中通常包含自定义变量

e.g:
```python
lst = [i for i in range(1,10)];
print(lst);
#结果为：[1,2,3,4,5,6,7,8,9]

lst = [i*i for i in range(1,10)];
print(lst);
#结果为：[1,4,9,16,25,36,49,64,81]

#生成一个元素值为2、4、6、8、10的列表
lst2 = [i*2 for i in range(1,6)]
#结果为：[2,4,6,8,10]
```


## 字典
### 字典
- Python内置的数据结构之一，与列表一样是一个可变序列
- 以键值对的方式存储数据，字典是一个**无序**的序列
<div align="center"><img src= "https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819230643374.png" alt=""></div>

### 字典的创建
#### 使用{}创建字典
```python
scores = {'张三':100,'李四':98,'王五':67};
print(scores);
#结果显示：{'张三':100,'李四':98,'王五':67}
print(type(scores));
#结果显示：<class 'dict'>
```
#### 使用内置函数dict()创建
```python
student = dict(name = 'jack',age = 20);
print(student);
#结果显示：{'name':'jack','age':20}
```
#### 空字典
```python
d = {};
print(d);
#结果显示：{}
```
### 字典的常用操作
#### 字典中元素的获取
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821121137715.png)
##### \[]取值与使用get()取值的区别
- \[]如果字典中不存在指定的key，抛出KeyError异常
- get()方法取值，如果字典中不存在指定的key，并不会抛出KeyError而是返回None，可以通过参数设置默认的value，以便指定的key不存在时
##### 使用\[]
```python
scores = {'张三':100,'李四':98,'王五':67};
print(scores['张三']);
#结果显示：100
print(scores['陈六']);
#结果显示：KeyError:'陈六'
```
##### 使用get()方法
```python
scores = {'张三':100,'李四':98,'王五':67};
print(scores.get('张三'));
#结果显示：100
print(scores.get('陈六'));
#结果显示：None
print(scores.get('麻七',99));#99是在查找'麻七'所对应的value不存在时，自定义提供的一个默认值
#结果显示：99
```
#### key的判断

| 判断     | Bool值               | 结果                  |
| ------ | ------------------- | ------------------- |
| in     | 指定的key在字典中存在返回True  | '张三' in scores      |
| not in | 指定的key在字典中不存在返回True | '张三'  not in scores |
#### 字典元素的删除
```python
del scores['张三'];    #删除指定的键值对
scores.clear();    #清空字典的元素
```
#### 字典元素的新增
```python
scores['Jack'] = 90;    #新增元素，增的是一个键值对
```
#### 字典元素的修改
```python
scores['Jack'] = 100;    #修改元素
```
#### 获取字典视图的三个方法

| 方法       | 获取的值                  |
| -------- | --------------------- |
| keys()   | 获取字典中所有key            |
| values() | 获取字典中所有value          |
| items()  | 获取字典中所有键值对（key和value） |

e.g:
```python
scores = {'张三':100,'李四':98,'王五':67};

#获取所有的key
keys = scores.keys();
print(keys);
#结果显示：dict_keys(['张三','李四','王五'])
print(type(keys));
#结果显示：<class 'dict_keys'>
print(list(keys));    #将所有键组成的视图转成列表
#结果显示：['张三','李四','王五']

#获取所有的value
values = scores.values();
print(values);
#结果显示：dict_values([100,98,67])
print(type(values));
#结果显示：<class 'dict_values'>
print(list(values));    #将所有值组成的视图转成列表
#结果显示：[100,98,67]

#获取所有键值对
items = scores.items();
print(items);
#结果显示：dict_items([('张三',100),('李四',98),('王五',67)])
print(type(items));
#结果显示：<class 'dict_items'>
print(list(items));    #将所有键值对组成的视图转成列表，转换之后的列表元素是由元组组成的
#结果显示：[('张三',100),('李四',98),('王五',67)]
```
#### 字典元素的遍历
e.g:
```python
scores = {'张三':100,'李四':98,'王五':67};

for item in scores:    #item获取的是字典中的键，[]或get()方法来获取值
	print(item,scores[item],scores.get(item))
```

### 字典的特点
 - 字典中的所有元素都是一个键值对，key不允许重复，value可以重复
 - 字典中的元素是无序的
 - 字典中的key必须是不可变对象，例如列表是可变对象，则列表不可做为字典的key
 - 字典也可以根据需要动态的伸缩
 - 字典会浪费较大的内存，是一种空间换时间的数据结构

### 字典生成式
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821131704838.png)
#### 内置函数zip()
- 用于将可迭代的对象作为参数，将对象中对应的元素打包成一个元组，然后返回这些元组组成的列表
#### 字典生成式
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821131916494.png)
e.g:
```python
items = ['Fruits','Books','Others'];
prices = [96,78,85];

d = {item.upper():price for item,price in zip(items,prices)};
print(d);
#结果为：{'FRUITS':96,'BOOKS':78,'OTHERS':85}
#zip()当可迭代对象列表内元素个数不同时会以元素小的那个为基准
```

## 元组
### 元组
- Python内置数据结构之一，是一个不可变序列
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821133330680.png)

#### 不可变序列与可变序列
- 不可变序列：字符串、元组
	- 不可变序列没有增删改的操作
- 可变序列：列表、字典
	- 可变序列可以对序列执行增删改操作，对象地址不发生更改

### 元组的创建方式
#### 小括号
```python
t = ('Python','Hello',90);

t2 = 'Python','Hello',90;    #省略了小括号
#多个字符串需要用加号连接在一起才是一个字符串，而这三个以逗号隔开，赋值给t2, 实际是个元组
#二者type都是tuple
```
#### 使用内置函数tuple()
```python
t = tuple(('Python','Hello',90));
```
#### 只包含一个元组的元素需要使用逗号和小括号
```python
t = (10,);
#如果不加,的话就会认为时这个值本身的数据类型即int，加了,则数据类型为tuple
```
#### 空元组
```python
t = ();
t2 = tuple();
```

### 为什么将元组设计为不可变序列
- 在多任务环境下，同时操作对象时不需要加锁
- 因此，在程序中尽量使用不可变序列
- **注意事项**：元组中存储的是对象的引用
	- 如果元组中对象本身是不可变对象，则不能再引用其他对象
	- 如果元组中的对象是可变对象，则可变对象的引用不允许改变，但数据可以改变 

![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821135545055.png)
e.g:
```python
t = (10,[20,30],9);

t[1] = 100;#元组是不允许修改元素的
#TypeError:'tuple' object does not support item assignment

#由于[20,30]是列表，而列表是可变序列，所以可以向列中添加元素，而列表的内存地址不变
t[1].append(100);
print(t);
#结果为：(10,[20,30,100],9)
```

### 元组的遍历
- 元组是可迭代对象，所以可以使用for...in...进行遍历
```python
t = tuple(('Python','Hello',90));
for item in t:
	print(item);
```

## 集合
### 集合
- Python内置数据结构之一，是一个可变序列
- **集合是没有value的字典**
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821140911623.png)

### 集合的创建方式
#### 直接{}
```python
s = {'Python','hello',90};    #集合中的元素不允许重复
```
#### 使用内置函数set()
```python
s1= set(range(6));
print(s1,type(s1));
#结果为：{0,1,2,3,4,5} <class 'set'>

s2 = set([1,2,3,3,4,4,5,5,6,6,6]);
print(s2,type(s2));
#结果为：{1,2,3,4,5,6} <class 'set'>
#将列表转化为集合并且去除了重复的元素

s3 = set((1,2,4,4,5,65));    #集合中的元素是无序的
print(s3,type(s3));
#结果为：{65,1,2,4,5} <class 'set'>

s4 = set('Python');
print(s4,type(s4));
#结果为：{'p','n','y','o','h','t'} <class 'set'>
#集合中的元素是无序的

s5 = set({12,4,34,55,66,44,4});
print(s5,type(s5));
#结果为：{34,66,4,55,12,44} <class 'set'>

#定义一个空集合
s6 = {};
print(type(s6));
#结果为：<class 'dict'>
#定义空集合不能直接用{}要用set()
s7 = set()
print(type(s7));
#结果为：<class 'set'>
```

### 集合的相关操作
#### 集合元素的判断操作
 - in或not in
#### 集合元素的新增操作
- 调用add()方法，一次添加一个元素
- 调用update()方法，一次至少添加一个元素，update中还可以添加列表、元组等
#### 集合元素的删除操作
 - 调用remove()方法，一次删除一个指定元素，如果指定的元素不存在抛出KeyError
 - 调用discard()方法，一次删除一个指定元素，如果指定的元素不存在不抛出异常
 - 调用pop()方法，一次只删除一个任意元素，pop()方法不能指定参数，只能写无参的，一般都是删除最左侧第一个元素
 - 调用clear()方法，清空集合

### 集合间的关系
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821144736846.png)

#### 两个集合是否相等
- 使用运算符\==或!=进行判断
```python
s = {10,20,30,40};
s2 = {20,30,10,40};
print(s == s2);#True
print(s != s2);#False
#集合是无序的，只要元素内容相同即相等
```
#### 一个集合是否是另一个集合的子集
- 可以使用调用方法issubset()进行判断
- B是A的子集
#### 一个集合是否是另一个集合的超集
- 可以使用调用方法issuperset()进行判断
- A是B的超集
#### 两个集合是否没有交集
- 可以使用调用方法isdisjoint()进行判断，没有交集为True

### 集合的数据操作
#### 集合的数学操作
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821145008364.png)
```python
#交集
s1 = {10,20,30,40};
s2 = {20,30,40,50,60};
print(s1.intersection(s2));
print(s1 & s2);#intersection()与&等价
#结果为：{40,20,30}

#并集
print(s1.union(s2));
print(s1 | s2);#union()与|等价
#结果为：{40,10,50,20,60,30}

#差集
print(s1.difference(s2));
print(s1 - s2);#difference()与-等价
#结果为：{10}

#对称差集
print(s1.symmetric_difference(s2));
print(s1 ^ s2);#symmetric_difference()与^等价
#结果为：{10,50,60}
```

### 集合生成式
- 用于生成集合的公式
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821150405797.png)
- 将{}修改为\[]就是列表生成式
- 没有元组生成式
```python
s = {i for i in range(1,10)};
print(s);
#结果为：{1,2,3,4,5,6,7,8,9}

s2 = {i*i for i in range(1,10)};
print();
#结果为：{64,4,25,16,9,36,49,1,81}
#集合是无序的

#生成一个元素值为2、4、6、8、10的集合
s3 = {i*2 for i in range(1,6)}
#结果为：{2,4,6,8,10}
```

## 字符串
### 字符串的创建与驻留机制
#### 字符串
- Python中字符串是基本数据类型，是一个不可变的字符序列
#### 什么叫字符串的驻留机制
- 仅保存一份相同且不可变字符串的方法，不同的值被存放在字符串的驻留池中，Python的驻留机制对相同的字符串只保留一份拷贝，后续创建相同字符串时，不会开辟新空间，而是把该字符串的地址赋给新创建的变量
- ![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821151228432.png)
```python
a = 'Python';
b = "Python";
c = '''Python''';
print(a,id(a));
print(b,id(b));
print(c,id(c));
#结果显示三个字符串的内存地址都是相同的
```
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821151853565.png)
#### 字符串的驻留机制
##### 驻留机制的几种情况（交互模式）
- 字符串的长度为0或1时
- 符合标识符的字符串
- 字符串只在编译时进行驻留，而非运行时
- \[-5,256\]之间的整数数字
```python
s1 = 'a';
s2 = 'a';
s1 is s2;#True

s1 = '%';
s2 = '%';
s1 is s2;#True，字符串长度为1，但%不属于符合标识符的字符串_属于

s1 = 'a%';
s2 = 'a%';
s1 == s2;#True
s1 is s2;#False，因为%不属于符合标识符的字符串，id不同

a = 'abc';
b = 'ab' + 'c';
c = ''.join(['ab','c']);
a is b;#True
a is c;#False，因为b是在运行前就编译好的，而c是需要在运行时调用jion()方法去合并的，字符串只在编译时进行驻留，而非运行时

a = -5;
b = -5;
a is b;#True

a = -6;
b = -6;
a is b;#False
```
##### sys中的intern方法强制2个字符串指向同一个对象
```python
import sys

a = 'a%';
b = 'a%';
a is b;#False

a = sys.intern(b);
a is b;#True
```
##### PyCharm对字符串进行了优化处理
#### 字符串驻留机制的优缺点
- 当需要值相同的字符串时，可以直接从字符串池里拿来使用，避免频繁的创建和销毁，提升效率和节约内存，因此拼接字符串和修改字符串是会比较影响性能的
- 在需要进行字符串拼接时建议使用str类型的join方法，而非+，因为join()方法是先计算出所有字符串的长度，然后再拷贝，只new一次对象，效率比+高

### 字符串的常用操作
#### 字符串的查询操作

| 方法       | 作用                                            |
| -------- | --------------------------------------------- |
| index()  | 查找子串substr第一次出现的位置，如果查找的子串不存在时，则抛出ValueError  |
| rindex() | 查找子串substr最后一次出现的位置，如果查找的子串不存在时，则抛出ValueError |
| find()   | 查找子串substr第一次出现的位置，如果查找的子串不存在时，则返回-1          |
| rfind()  | 查找子串substr最后一次出现的位置，如果查找的子串不存在时，则返回-1         |

```python
s = 'hello,hello';
print(s.index('lo'));#返回的是第一个'lo'中l的位置3
print(s.find('lo'));#返回的是第一个'lo'中l的位置3
print(s.rindex('lo'));#返回的是最后一个'lo'中l的位置9
print(s.index('lo'));#返回的是最后一个'lo'中l的位置9
```
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821164831940.png)
```python
print(s.index('k'));
#ValueError:substring not found
print(s.find('k'));
#-1
print(s.rindex('k'));
#ValueError:substring not found
print(s.rfind('k'));
#-1
```
#### 字符串的大小写转换

| 方法           | 作用                                 |
| ------------ | ---------------------------------- |
| upper()      | 把字符串中的所有字符都转成大写字母                  |
| lower()      | 把字符串中的所有字符都转成小写字母                  |
| swapcase()   | 把字符串中的所有大写字母转成小写字母，以及所有小写字母都转成大写字母 |
| capitalize() | 把第一个字符转换为大写，把其余字符转换为小写             |
| title()      | 把每个单词的第一个字符转换为大写，每个单词的剩余字符转换为小写    |

```python
s = 'hello,python';
a = s.upper();
print(s,id(s));
print(a,id(a));
#upper()会生成一个新的字符串对象给a，原来的s不变，a和s的内存地址不同
#剩余的其他方法类似
```
- **注意**：
	- 即使转换后的字符串和转换前的一样，也是重新开辟了一块内存空间存储的，id也不同
	- 例如原本是小写的，利用lower()方法后还是会生成一个全小写的新字符串对象
#### 字符串内容对齐操作

| 方法       | 作用                                                            |
| -------- | ------------------------------------------------------------- |
| center() | 居中对齐，第一个参数指定宽度，第二个参数指定填充符，第二个参数是可选的，默认是空格，如果设置宽度小于实际宽度则返回原字符串 |
| ljust()  | 左对齐，第一个参数指定宽度，第二个参数指定填充符，第二个参数是可选的，默认是空格，如果设置宽度小于实际宽度则返回原字符串  |
| rjust()  | 右对齐，第一个参数指定宽度，第二个参数指定填充符，第二个参数是可选的，默认是空格，如果设置宽度小于实际宽度则返回原字符串  |
| zfill()  | 右对齐，左边用0填充，该方法只接收一个参数，用于指定字符串的宽度，如果指定的宽度小于等于字符串的长度，返回字符串本身    |
```python
s = 'hello,python';
print(s.center(20,'*'));
#结果为：****hello,python****
#给出的宽度大于字符串内容的宽度，剩余宽度左右用填充符填充

print(s.ljust(10));
#结果为：hello,python
#如果设置宽度小于实际宽度则返回原字符串

#rjust()类似

print(s.zfill(20));
#结果为：00000000hello,python
#右对齐，左边用0填充，该方法只接收一个参数，用于指定字符串的宽度
print('-8910'.zfill(8));
#结果为：-0008910
#0会添加在负号右边且负号也算一位字符
```
#### 字符串的劈分操作

<table style="width:100%;text-align: center;vertical-align: middle">
	<tr>
		<th style="text-align: center; vertical-align: middle">方法</th>
		<th style="text-align: center; vertical-align: middle">作用</th>
	</tr>
	<tr>
		<td rowspan="3" style="text-align: center; vertical-align: middle">split()</td>
		<td>从字符串的左边开始劈分，默认的劈分字符是空格字符串，返回的值都是一个列表</td>
	</tr>
	<tr>
	    <td>以通过参数sep指定劈分字符串时的劈分符</td>
	</tr>
	<tr>
		<td>通过参数maxsplit指定劈分字符串时的最大劈分次数，在经过最大次劈分后，剩余的子串会单独作为一部份</td>
	</tr>
	<tr>
		<td rowspan="3" style="text-align: center; vertical-align: middle">rsplit()</td>
		<td>从字符串的右边开始劈分，默认的劈分字符是空格字符串，返回的值都是一个列表</td>
	</tr>
	<tr>
	    <td>以通过参数sep指定劈分字符串时的劈分符</td>
	</tr>
	<tr>
		<td>通过参数maxsplit指定劈分字符串时的最大劈分次数，在经过最大次劈分后，剩余的子串会单独作为一部份</td>
	</tr>
</table>

```python
s = 'hello world python';
lst = s.split();
print(lst);
#结果为：['hello','world','python']

s1 = 'hello|world|python';
print(s1.split(sep='|'));
#结果为：['hello','world','python']
print(s1.split(sep='|',maxsplit=1));
#结果为：['hello','world|python']

#rsplit()方法类似，只是方向相反
```

#### 判断字符串的操作

| 方法             | 作用                                                        |
| -------------- | --------------------------------------------------------- |
| isidentifier() | 判断指定的字符串是不是合法的标识符，空格和%等不是有效标识符                            |
| isspace()      | 判断指定的字符串是否全部有空白字符组成（回车、换行、水平制表符）                          |
| isalpha()      | 判断指定的字符串是否全部由字母组成，这里的中文、字母、拼音、等都属于字母（python3对非ASCII字符的支持） |
| isdecimal()    | 判断指定的字符串是否全部由十进制的数字组成                                     |
| isnumeric()    | 判断指定的字符串是否全部由数字组成                                         |
| isalnum()      | 判断指定的字符串是否全部由字母和数字组成                                      |
- **注意**：
	- ![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821174721601.png)

#### 字符串的替换与合并操作

| 方法        | 作用                                                                                |
| --------- | --------------------------------------------------------------------------------- |
| replace() | 第一个参数指定被替换的子串，第二个参数指定替换字串的字符串，该方法返回替换后得到的字符串，替换前的字符串不发生变化，调用该方法时可以通过第三个参数指定最大替换次数 |
| join()    | 将列表或元组中的字符串合并成一个字符串                                                               |
```python
s = 'hello,python';
print(s.replace('python','java'));
#结果为：hello,java

s1 = 'hello,python,python,python';
print(s1.replace('python','java',2));
#结果为：hello,java,java,python

lst = ['hello','java','python'];
print('|',join(lst));#|是设置的连接时的连接符
#结果为：hello|java|python
t = ('hello','java','python');
print('|',join(t));#|是设置的连接时的连接符
#结果为：hello|java|python

print('*',join('Python'));#将字符串作为字符串序列以*进行连接
#结果为：P*y*t*h*o*n
```

#### 字符串的比较操作
- **运算符**：>,>=,<,<=,\==,!=
- **比较规则**：首先比较两个字符串中的第一个字符，如果相等则继续比较下一个字符，依次比较下去，直到两个字符串中的所有后续字符将不再被比较
- **比较原理**：两个字符进行比较时，比较的是其ordinal value（原始值），调用内置函数ord可以得到指定字符的ordinal value。与内置函数ord对应的是内置函数chr，调用内置函数chr时指定ordinal value可以得到其对应的字符
```python
print('apple' > 'app')#True
print('apple' > 'banana')#False
print(ord('a'),ord('b'));
#结果为：97,98
#字符对应的原始值是Unicode码值，Unicode前128项就是ASCII码值
print(chr(97),chr(98));
#结果为：a,b
```
- **\==与is的区别**
	- \==比较的是value是否相等
	- is比较的是id是否相等
```python
a = b = 'python';
c = 'python';
print(a == b);#True
print(b == c);#True
print(a is b);#True
print(b is c);#True
#a,b,c的id相同
```
#### 字符串的切片操作
##### 字符串是不可变类型
- 不具备增删改等操作
- 切片操作将产生新的对象
![image.png](https://raw.githubusercontent.com/Ryokode/PicGo/main/20260821183218598.png)
