# 类和实例

定义类可以使用`class`关键字

```
class Student(object):
    pass
```

`class`后面紧跟类名，类名后面的`(object)`表示该类是从哪里继承的。

创建实例是通过`类名+()`实现的

```
student = Student()
```

类中有一个`__init__(self)`方法类似于java中的构造函数

```
class Student(object):
    def __init__(self, name, score):
        self.name = name
        self.score = score
        
```

> self关键字指向当前实例，表示创建的实例本身，类似于java中的this

和普通函数相比，在类中定义的函数只有一点不同，就是第一个参数永远是`self`，并且调用时不用传递该参数。

# 访问限制

在python中要实现私有变量、私有方法可以在变量或函数名前加上`_`或`__`表示，例如：

```
class Student(object):
    def __init__(self, name, score):
        self.__name = name
        self.__score = score
    def get_name(self):
        return self.__name
```

> 注意：在python中，变量名或函数名类似`__xx__`这种以双下划线开头结尾的具有特殊含义，是可以直接访问的，不是私有变量

以`_`开头的变量外部是可以访问的，按照预定俗称的规定，我们将他们当成私有变量

以`__`开头的变量解释器将他改成了\_ClassName\_\_varName，所以仍然可以通过访问\_ClassName\_\_varName来直接访问变量

> 注意：不同的python解释器会把\_\_varName改变成不同的变量名，所以强烈不建议直接访问

# 继承和多态

继承：class 类名\(父类名\)

# 获取对象信息

### type\(\)

`type()`函数返回对应的Class类型

> 但这种方式在继承关系中就不是很方便了

### isinstance\(\)

```
isinstance(dog, Animal) # True
isinstance([1,2,3], (list, tuple)) # True 判断是否是某些类中的一种
```

### dir\(\)

获取一个对象的所有属性和方法，它返回一个包含字符串的list

# 实例属性和类属性

类属性类似于java中的静态变量

实例属性名尽量避免和类属性名相同，会覆盖类属性



