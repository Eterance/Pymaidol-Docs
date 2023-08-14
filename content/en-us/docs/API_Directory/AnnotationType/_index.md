---
title: "AnnotationType Module"
date: 2023-08-14T23:28:35+08:00
---

## Overview

The `AnnotationType` module provides an enumeration of annotations that can be used in template design files with the `.pymd` extension.

Module: `pymaidol`

## Import

```python
from pymaidol import AnnotationType
```

## Classes

Name | Description
--- | ---
[AnnotationTypeEnum Enumeration]({{< ref "AnnotationTypeEnum_Enumeration.md" >}}) | The `AnnotationTypeEnum` enumeration is the base class for all annotation type enumerations. It does not contain any enumeration values and is only used for inheritance.
[SingleLineAnnotationTypeEnum Enumeration]({{< ref "SingleLineAnnotationTypeEnum_Enumeration.md" >}}) | Contains the types of single-line annotations that can be used in template design files with the `.pymd` extension.
[MultiLineAnnotationTypeEnum Enumeration]({{< ref "MultiLineAnnotationTypeEnum_Enumeration.md" >}}) | Contains the types of multi-line annotations that can be used in template design files with the `.pymd` extension.

## Static Variables

Name | Type | Description
--- | --- | ---
FULL_ANNOTATION_TYPE | `list[AnnotationTypeEnum]` | A list that contains all the enumeration values of the annotation type enumerations.
