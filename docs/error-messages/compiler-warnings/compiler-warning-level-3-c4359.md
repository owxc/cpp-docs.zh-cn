---
title: 编译器警告（等级3） C4359
ms.date: 11/04/2016
f1_keywords:
- C4359
helpviewer_keywords:
- C4359
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
ms.openlocfilehash: 7da4d231a341f8d4d4e8c1e82fc1fc8b9893778a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051611"
---
# <a name="compiler-warning-level-3-c4359"></a>编译器警告（等级3） C4359

"type"：实际对齐（8）大于在 __declspec 中指定的值（align （））

为某个类型指定的对齐方式小于其某个数据成员的类型的对齐方式。  有关详细信息，请参阅[align](../../cpp/align-cpp.md)。

## <a name="example"></a>示例

下面的示例生成 C4359。

```cpp
// C4359.cpp
// compile with: /W3 /c
struct __declspec(align(8)) C8 { __int64 i; };
struct __declspec(align(4)) C4  { C8 m8; };   // C4359
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK
struct __declspec(align(16)) C16  { C8 m8; };   // OK
```