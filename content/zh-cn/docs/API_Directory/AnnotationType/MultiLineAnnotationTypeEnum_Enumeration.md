---
title: "MultiLineAnnotationTypeEnum 枚举"
date: 2023-08-14T23:28:35+08:00
draft: false
---

## 概述

包含了可在模板设计文件中`.pymd`使用的多行注释的类型。

模块：[pymaidol.AnnotationType]({{< ref "_index.md" >}})

继承自：[pymaidol.AnnotationType.AnnotationTypeEnum]({{< ref "AnnotationTypeEnum_Enumeration.md" >}})

## 导入

```python
from pymaidol import MultiLineAnnotationTypeEnum
```

或

```python
from pymaidol.AnnotationType import MultiLineAnnotationTypeEnum
```

## 枚举项

名称 | 值 | 描述
--- | --- | ---
Python | ''' | Python 的多行注释，即以 `'''` 开头和结尾的注释。
C | /\* | C 的多行注释，即以 `/\*` 开头和 `*/` 结尾的注释。
HTML | \<!-- | HTML 的多行注释，即以 `<!--` 开头和 `-->` 结尾的注释。
