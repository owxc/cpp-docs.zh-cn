---
title: 编译器警告（等级1） C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: db7f0425c3752c20ca8c5d4b6c95845ff64475c5
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627039"
---
# <a name="compiler-warning-level-1-c4042"></a>编译器警告（等级1） C4042

"identifier"：有坏的存储类

在此上下文中，不能将指定的存储类与此标识符一起使用。 编译器改为使用默认存储类：

- `extern`，如果*标识符*是一个函数。

- 如果*标识符*是形参或局部变量，则为**auto**。

- 没有存储类，如果*标识符*是全局变量。

如果在参数声明中指定了除**register**之外的存储类，则可能导致此警告。

下面的示例生成 C4042

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```