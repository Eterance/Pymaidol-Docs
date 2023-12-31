---
title: TemplateBase 类
date: 2023-08-14T23:28:35+08:00
draft: false
---

## 概述

`TemplateBase` 类是 Pymaidol 模板的后台类，是所有 Pymaidol 模板类的基类。是不可实例化的抽象类，需要被继承使用。

模块：pymaidol.TemplateBase

继承自：abc.ABC

## 导入

```python
from pymaidol import TemplateBase
```

或

```python
from pymaidol.TemplateBase import TemplateBase
```

## 构造函数

### `TemplateBase(template, template_file_path, supported_annotation_types, disable_annotation_types)` (virtual)

#### 参数

- `template` (str, optional): 模板字符串。默认为 `None`。
- `template_file_path` (str, optional): 模板文件路径。默认为 `None`。
- `supported_annotation_types` (list[AnnotationTypeEnum], optional): 支持的注释类型列表。默认为所有注释类型（Python、C的单行与多行注释、HTML注释）。
- `disable_annotation_types` (list[AnnotationTypeEnum], optional): 禁用的注释类型列表，使这些注释出现在渲染后的文本中。默认为空。禁用的优先级高于支持。例如，如果 `disable_annotation_types` 中包含 `AnnotationTypeEnum.SingleLineAnnotationTypeEnum.Python` （python 单行注释），则 `supported_annotation_types` 中无论是否包含它，都将被视为禁用该注释类型。

当 `template` 与 `template_file_path` 都为 `None` 时，`TemplateBase` 类及其子类将试图读取在与其同一目录下、与其同名的模板文件 `.pymd`。如果两个都不为空，则优先使用 `template`。

## 属性

### `rendered`（str，readonly）

渲染后的字符串。如果自初始化或调用 `HotReload()` 方法以来没有调用过 `Render()` 方法，则为 `None`。

### `template`（str，readonly）

模板字符串。

## 方法

### `HotReload(template, template_file_path)` (final)

重新加载模板。

#### 参数

- `template` (str, optional): 模板字符串。默认为 `None`。
- `template_file_path` (str, optional): 模板文件路径。默认为 `None`。

当 `template` 与 `template_file_path` 都为 `None` 时，`TemplateBase` 类及其子类将试图读取在与其同一目录下、与其同名的模板文件 `.pymd`。如果两个都不为空，则优先使用 `template`。

#### 返回值 (`None`)

无。


### `Render(inject_kwargs)` (final)

给与数据并渲染模板字符串。

#### 参数

- `inject_kwargs` (dict, Optional): 用于渲染模板字符串的外部注入变量。默认为 `None`。注入的变量将会作为局部变量。

#### 返回值 (`str`)

渲染后的字符串。
