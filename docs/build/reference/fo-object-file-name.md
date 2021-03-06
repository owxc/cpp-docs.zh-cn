---
title: /Fo（对象文件名）
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: a8f2c1a196f18e6d310fd41d4dbed751440a4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293038"
---
# <a name="fo-object-file-name"></a>/Fo（对象文件名）

指定对象 (.obj) 文件的名称或要使用的目录，而不是默认目录。

## <a name="syntax"></a>语法

```
/Fopathname
```

## <a name="remarks"></a>备注

如果不使用此选项，该对象文件将使用的源文件和.obj 扩展的基名称。 可以使用任何名称和扩展插件，但推荐的约定是使用。 目标

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页”  对话框。 有关详细信息，请参阅[设置C++Visual Studio 中的编译器和生成属性](../working-with-project-properties.md)。

1. 单击 **“C/C++”** 文件夹。

1. 单击“输出文件”  属性页。

1. 修改**对象文件名**属性。  在开发环境中，对象文件必须具有的扩展。 目标

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>。

## <a name="example"></a>示例

下面的命令行创建对象文件中的现有目录，\OBJECT，驱动器 B.命名 THIS.obj

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>请参阅

[输出文件 (/F) 选项](output-file-f-options.md)<br/>
[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)<br/>
[指定路径名](specifying-the-pathname.md)
