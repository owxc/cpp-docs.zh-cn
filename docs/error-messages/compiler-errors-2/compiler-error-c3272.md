---
title: 编译器错误 C3272
ms.date: 11/04/2016
f1_keywords:
- C3272
helpviewer_keywords:
- C3272
ms.assetid: 7cdf254d-f207-4116-a1bf-7386f3b82a6f
ms.openlocfilehash: 14eefa303a8148b79ca7bc0d1777688ffce176f1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2019
ms.locfileid: "74753843"
---
# <a name="compiler-error-c3272"></a>编译器错误 C3272

“symbol”：符号需要 FieldOffset，因为它是用 StructLayout(LayoutKind::Explicit) 定义的 typename 类型的成员

当 `StructLayout(LayoutKind::Explicit)` 有效时，必须用 `FieldOffset`来标记字段。

下面的示例生成 C3272：

```cpp
// C3272_2.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Explicit)]
ref struct X
{
   int data_;   // C3272
   // try the following line instead
   // [FieldOffset(0)] int data_;
};
```
