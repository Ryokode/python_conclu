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
##### []取值与使用get()取值的区别
- []如果字典中不存在指定的key，抛出KeyError异常
- get()方法取值，如果字典中不存在指定的key，并不会抛出KeyError而是返回None，可以通过参数设置默认的value，以便指定的key不存在时
##### 使用[]
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