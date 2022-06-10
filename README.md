# 一. 通用规范
##  关于大括号
- 控制语句(if,for,while,switch)中，大括号开始与行尾
- 函数中，大括号要开始于行首

推荐这样写：
```
white(someCondition){
}
//函数
void function(param1,param2)
{
}  
```
## 运算符
1. 运算符与变量之间的间隔

1.1 一元运算符与变量之间没有空格：
 
```
!bValue
~iValue
++iCount
*strSource
&fSum
```

 1.2 二元运算符与变量之间必须有空格

```
fWidth = 5 + 5;
fLength = fWidth * 2;
fHeight = fWidth + fLength;
for(int i = 0; i < 10; i++)
```

2. 多个不同的运算符同时存在时应该使用括号来明确优先级

在多个不同的运算符同时存在的时候应该合理使用括号，不要盲目依赖操作符优先级。
因为有的时候不能保证阅读你代码的人就一定能了解你写的算式里面所有操作符的优先级。

来看一下这个算式：2 << 2 + 1 * 3 - 4

这里的&lt;&lt;是移位操作直观上却很容易认为它的优先级很高，所以就把这个算式误认为：(2 << 2) + 1 _ 3 - 4
但事实上，它的优先级是比加减法还要低的，所以该算式应该等同于：2 << (2 + 1 _ 3 - 4)。
所以在以后写这种复杂一点的算式的时候，尽量多加一点括号，避免让其他人误解（甚至是自己）。

## 变量

### 1. 一个变量有且只有一个功能，尽量不要把一个变量用作多种用途
### 2. 变量在使用前应初始化，防止未初始化的变量被引用
### 3. 局部变量应该尽量接近使用它的地方

推荐这样写：
```
func someFunction() {

  let index = ...;
  //Do something With index
  ...
  ...

  let count = ...;
  //Do something With count

}
```

不推荐这样写：
```
func someFunction() {

  let index = ...;
  let count = ...;
  //Do something With index
  ...
  ...

  //Do something With count
}
```

## if语句

1. 必须列出所有分支（穷举所有的情况），而且每个分支都必须给出明确的结果。

推荐这样写：
```
var hintStr;
if (count < 3) {
  hintStr = "Good";
} else {
  hintStr = "";
}  
```

不推荐这样写：
```
var hintStr;
if (count < 3) {
 hintStr = "Good";
}
```

### 2. 不要使用过多的分支，要善于使用return来提前返回错误的情况

推荐这样写：
```
- (void)someMethod { 
  if (!goodCondition) {
    return;
  }
  //Do something
}
```

不推荐这样写：
```
- (void)someMethod { 
  if (goodCondition) {
    //Do something
  }
}
```

### 3. 条件表达式如果很长，则需要将他们提取出来赋给一个BOOL值

推荐这样写：
```
let nameContainsSwift = sessionName.hasPrefix("Swift")
let isCurrentYear = sessionDateCompontents.year == 2014
let isSwiftSession = nameContainsSwift && isCurrentYear
if (isSwiftSession) { 
   // Do something
}
```

不推荐这样写：
```
if ( sessionName.hasPrefix("Swift") && (sessionDateCompontents.year == 2014) ) { 
    // Do something
}
```

