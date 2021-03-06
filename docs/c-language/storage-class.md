---
title: 存储类
ms.date: 11/04/2016
helpviewer_keywords:
- linkage [C++], external
- function storage class
- function specifiers, storage class
- storage classes
- Microsoft-specific storage classes
- external linkage, storage-class specifiers
- static storage class specifiers
ms.assetid: 39a79ba6-edf5-42b6-8e45-f94227603dd6
ms.openlocfilehash: aa6e977b3aa03b5f08901cfa8b0abe1b4046e72d
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857003"
---
# <a name="storage-class"></a>存储类

函数定义中的存储类说明符为函数提供 `extern` 或 static 存储类。

## <a name="syntax"></a>语法

function-definition：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers*<sub>opt</sub> *attribute-seq*<sub>opt</sub> *declarator* *declaration-list*<sub>opt</sub> *compound-statement*

/\**属性-seq*是特定于 Microsoft 的 \*/

*declaration-specifiers*：<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*storage-class-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-specifier* *declaration-specifiers*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*type-qualifier* *declaration-specifiers*<sub>opt</sub>

storage-class-specifier: /\* 针对函数定义 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**extern**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**static**

如果函数定义不包括 storage-class-specifier，则存储类默认为 `extern`。 您可以将函数显式声明为 `extern`，但这不是必需的。

如果函数的声明包含 storage-class-specifier `extern`，则标识符拥有与带文件范围的标识符的任何可见声明相同的链接。 如果没有带文件范围的可见声明，则标识符具有外部链接。 如果标识符具有文件范围但没有 storage-class-specifier，则标识符具有外部链接。 外部链接意味着，标识符的每个实例表示相同的对象或函数。 有关链接和文件范围的详细信息，请参阅[生存期、范围、可见性和链接](../c-language/lifetime-scope-visibility-and-linkage.md)。

带 `extern` 之外的存储类说明符的块范围数声明将生成错误。

带 static 存储类的函数仅在定义它的源文件中可见。 所有其他函数（无论是显式还是隐式地为它们提供 `extern` 存储类）在程序中的所有源文件中都可见。 如果需要 static 存储类，则必须在函数声明（如果有）的第一个匹配项和函数定义中声明该存储类。

**Microsoft 专用**

在启用 Microsoft 扩展时，如果函数定义在同一源文件中且定义显式指定 static 存储类，则会为最初未使用存储类（或使用 `extern` 存储类）声明的函数提供 static 存储类。

当使用 /Ze 编译器选项进行编译时，使用 `extern` 关键字在块内声明的函数具有全局可见性。 在使用 /Za 编译时，并非如此。 如果需要考虑源代码的可移植性，则不应依赖此功能。

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[C 函数定义](../c-language/c-function-definitions.md)
