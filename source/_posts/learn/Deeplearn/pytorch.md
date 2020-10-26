---
title: __init__和self
date: 2020-10-24 23:05:19
tags: deeplearn 
categories: learn
---

## 1.类中的方法和属性
方法：也就是各类中定义的函数，比如我们定义一个车的类，描述车的函数就是一个方法。  

属性：车的品牌、型号、生产日期等信息就是它的属性.

## 1.1__init__方法：无需直接调用，生成实例对象的时候自动调用。
“init”的全称是“initialize”，也就是初始化的意思，所以__init__又称构造方法。  

在定义类的时候__init__()方法是必不可少的。 

>(1)双下划线开头的函数为私有函数，不能在类的外部被调用或直接访问；  
>(2)init()，支持带参数的初始化，例如：def init(self,ai_settings,screen)；  
>(3)init()函数的第一个参数必须为self（也可是别的名字），后续参数可自由指定；

init()这种初始化方法，用来初始化新创建对象的属性，在一个对象被创建以后会立即调用，比如像实例化一个类：
  
  ``` 
  class Car():
    def __init__(self,make,model,year):    ###
        self.make = make
        self.model = model
        self.year = year 
my_car = Car('aodi','A4','2010')
print(my_car.model)           
   ```
程序中没有直接调用__init__方法，但make，model，year等属性通过Car()类自动调用了__init__方法，生成了属性。
  
## 1.2self参数
“self”的英文意思很明显，是自己的意思。即实际指的是，类实例对象本身。

同时，由于说到“自己”这个词，都是和相对而言的“其他”而说的；而此处的其他，指的是，类Class，和其他变量，比如局部变量，全局变量等。
此处的self，是个对象（Object），是当前类的实例。
因此，对应的self.valueName 和 self.function()中的valueName：表示self对象，即实例的变量。与其他的，Class的变量，全局的变量，局部的变量，是相对应的。
function：表示是调用的是self对象，即实例的函数。与其他的全局的函数，是相对应的。

因为Python已经规定：函数的第一个参数，就必须是实例对象本身，并且约定俗成，把其名字写为self。因此我们再定义类中的所有函数时必须传入self参数。  
```
class Car():
    def __init__(self,make,model,year):    ###
        self.make = make
        self.model = model
        self.year = year 
    def get_descriptive_name(self):
        long_name = self.year+' '+self.make+" "+self.model
        print(self)                    ###看下self指向哪里
        print(type(self))              ###看下self类型是什么
        return long_name
my_car = Car('aodi','A4','2010')
my_car.get_descriptive_name()          
```  
