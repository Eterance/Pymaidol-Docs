---
title: 入门
date: 2023-08-14T23:28:35+08:00
weight: 1
---

## 环境要求与安装

python >= 3.10

``` bash
pip install Pymaidol -i https://pypi.python.org/simple
```

## 第一个 Pymaidol 模板

### 创建模板文件

首先，假设你创建了一个名为 `pymaidol_test` 的文件夹。使用编辑器或者 IDE 打开该文件夹作为工作目录。

在 `pymaidol_test` 文件夹下打开命令行，输入以下命令：

``` bash
python -m pymaidol -n FirstTemplate
```

`FirstTemplate` 是模板类的类名。命令行会输出以下内容，同时文件夹中会生成 `FirstTemplate.pymd` 和 `FirstTemplate.py` 两个文件：

``` bash
Success: file "FirstTemplate.pymd" created
Success: file "FirstTemplate.py" created
```

### 编写模板设计文件

首先，用以下代码将 `FirstTemplate.pymd` 中的全部内容替换掉：

``` python
from pymaidol import TemplateBase
from pymaidol.AnnotationType import FULL_ANNOTATION_TYPE, AnnotationTypeEnum

class FirstTemplate(TemplateBase):
    def __init__(self, 
                 package_name:str, 
                 template: str | None = None, 
                 template_file_path: str | None = None, 
                 supported_annotation_types: list[AnnotationTypeEnum] = FULL_ANNOTATION_TYPE,
                 disable_annotation_types: list[AnnotationTypeEnum] = []) -> None:
        super().__init__(template, template_file_path, supported_annotation_types, disable_annotation_types)
        self.package_name = package_name
        
def main():
    template = FirstTemplate("Pymaidol")
    string = template.Render({"says": "Hello World"})
    print(string)
    
if __name__ == "__main__":
    main()
```

这段代码主要修改了以下部分：

- 为 `FirstTemplate` 类添加了 `package_name` 属性。
- 添加了 `main` 函数，以实例化 `FirstTemplate` 类。向 `FirstTemplate` 类的构造函数传入了 `package_name` 参数，该参数的值为 `Pymaidol`。
- 调用了 `Render` 方法，向其传入了一个字典 `{"says": "Hello World"}`。

然后，用以下代码替换 `FirstTemplate` 类中的全部内容：

``` python
@{import time}
Now (@(time.ctime())), Say "@(says)" using @(self.package_name)!
```

运行 `FirstTemplate.py`，命令行会输出以下内容：

``` bash
Now (Tue May 23 19:21:19 2023), Say "Hello World" using Pymaidol!
```

## 另请参阅

- [Pymaidol 语法参考]({{< ref "Syntax_Reference.md" >}})
- [Pymaidol API 目录]({{< ref "API_Directory/_index.md" >}})
