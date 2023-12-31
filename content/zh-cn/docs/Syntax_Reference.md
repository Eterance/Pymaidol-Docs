---
title: 语法参考
date: 2023-08-14T23:28:35+08:00
draft: false
weight: 2
---

## Pymaidol 模板文件的创建与结构

### 使用命令行创建模板文件（推荐）

使用以下命令创建模板文件：

``` bash
python -m pymaidol -n <类名> [-d <目录>]
```

会在当前目录下生成 `<类名>.pymd` 和 `<类名>.py` 两个文件。

### Pymaidol 模板文件的组成

模板文件由模板设计文件 `.pymd` 和模板后台文件 `.py` 组成。

模板设计文件 `.pymd`：包含了模板的设计内容，如字符串和使用 Pymaidol 语法嵌入的 Python 代码/呈现表达式。

模板后台文件 `.py`：包含了模板的后台逻辑，如模板类的定义。

可以在设计文件中访问在后台文件中定义的变量和方法，但不能在后台文件中访问在设计文件中定义的元素。此外，两者的 `import` 语句是独立的。

> 若手动创建 Pymaidol 模板文件，模板设计文件 `.pymd` 和模板后台文件 `.py` 的文件名必须相同，且位于同一个文件夹下；模板后台文件的文件名必须与模板类的类名相同。

## Pymaidol 语法

Pymaidol 使用 `@` 作为标记符，用于标记 Pymaidol 表达式、关键字和代码块。若要在文本中使用 `@`，请使用 `@@` 代替。

## Pymaidol 表达式

Pymaidol 表达式用于向模板中嵌入/呈现数据。Pymaidol 表达式的格式为 `@(<表达式>)` ，如：

``` python
@("Hello World!")
```

渲染后的文本为：

``` python
Hello World!
```

### Pymaidol 关键字

关键字的格式为 `@<关键字>;`，如：

``` python
@break; # 跳出当前循环
@continue; # 跳过当前循环
```

### Pymaidol 代码块

Pymaidol 代码块用于在模板渲染时执行一些 python 代码。格式为 `@{<代码块>}`，如：

``` python
@{answer = 42}
The answer of this universe is @(answer)
```

渲染后的文本为：

``` python
The answer of this universe is 42
```

因为渲染 Pymaidol 代码块是按照由上至下、由左至右的顺序进行的，所以可以使用 Pymaidol 代码块来定义一些变量、函数等，在之后的表达式或代码块中使用。

### if, elif, else 代码块

使用方式为 `@if (<条件表达式>){<模板设计语句>}`，如：

``` python
@{answer = 42}
@if (answer > 0) {answer == @(answer), and it is positive.}
@elif (answer < 0) {answer == @(answer), and it is negative.}
@else {answer == @(answer), and it is zero.}
```

渲染后的文本为：

``` python
answer == 42, and it is positive.
```

### while 代码块

使用方式为 `@while (<条件表达式>){<模板设计语句>}`，如：

``` python
@{i = 0}
@while (i < 5){
i = @(i)
@{i += 1}
}
```

渲染后的文本为：

``` python
i = 0
i = 1
i = 2
i = 3
i = 4
```

### for 代码块

使用方式为 `@for (<变量> in <可迭代对象>){<模板设计语句>}`，如：

``` python
@for (i in range(5)){
i = @(i)
@if (i == 3) {@break;}
}
```

渲染后的文本为：

``` python
i = 0
i = 1
i = 2
i = 3
```
