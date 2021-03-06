# 变量定义与赋值

python变量定义不需要声名类型。

使用`=`来赋值。

每个变量使用之前都需要赋值，变量赋值之后变量才会被创建。

```
val=100 #整型
val=100.0 #浮点型
val="Hello" #字符串
a = b = c = 1 #多个变量赋值
```

# 变量类型

python有五个标准的数据类型：

* Numbers 数字
* String 字符串
* List 列表
* Tuple 元组
* Dictionary 字典

## 数字类型

四种不同的数字类型：

* int 有符号整型
* long 长整型
* float 浮点型
* complex 复数
* boolean 布尔类型

> 数字类型用于存储数值，是不可改变的，每次赋值新的数据就是创建一个新的Number类型
>
> boolean类型也是一种数字类型

## 列表

列表使用`[]`标识，是python最通用的符合数据类型。例如:

```
val=['1', '2', '3']
print(val[0])
```

## 元组

元组是python的另一种数据类型，类似于List

元组使用`()`标识。

元组不能二次赋值，相当于只读列表。例如：

```
val=('1', '2', '3')
print(val[0])
```

## 字典

字典使用`{}`标识，由`key-value`组成，例如：

```
dict={'key1':'value1', 'key2':'value2'}
print(dict['key1'])
```



