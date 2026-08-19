## ASCII 字符代码表
![e6ff5e187d7c6bade4d191224b19efd1.jpg](https://raw.githubusercontent.com/Ryokode/PicGo/main/e6ff5e187d7c6bade4d191224b19efd1.jpg)

## 条件表达式
- ......if...else......，结果为true则执行或输出if前的内容，false则执行或输出else后的内容

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
- e.g:
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

## 二重循环中的break和continue
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
### 获取列表中的单个元素
<div align="center"><img src= "https://raw.githubusercontent.com/Ryokode/PicGo/main/20260819173704322.png
" alt=""></div>
