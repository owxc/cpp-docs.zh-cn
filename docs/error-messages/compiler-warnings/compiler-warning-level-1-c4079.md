---
title: 编译器警告（等级1） C4079
ms.date: 11/04/2016
f1_keywords:
- C4079
helpviewer_keywords:
- C4079
ms.assetid: 549759f0-e168-47e9-8c9a-de93ac843689
ms.openlocfilehash: 27304f8c31c195097c6adcdae1408ef7ad9698bc
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627044"
---
# <a name="compiler-warning-level-1-c4079"></a>编译器警告（等级1） C4079

意外的标记“token”

杂注参数列表中出现意外的分隔符标记。 已忽略杂注的其余部分。

下面的示例生成 C4079：

```cpp
// C4079.cpp
// compile with: /W1
#pragma warning(disable : 4081)
#pragma pack(c,16)   // C4079

int main() {
}
```