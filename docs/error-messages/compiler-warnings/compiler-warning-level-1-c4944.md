---
title: 编译器警告（等级 1）C4944
ms.date: 11/04/2016
f1_keywords:
- C4944
helpviewer_keywords:
- C4944
ms.assetid: e2905eb1-2e3b-4fab-a48b-c0cae0fd997f
ms.openlocfilehash: 339a136824f050391c23e268992a656714d1dabb
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050222"
---
# <a name="compiler-warning-level-1-c4944"></a>编译器警告（等级 1）C4944

“symbol”：无法从“assembly1”导入符号，因为当前范围内已存在“symbol”

在源代码文件中定义了符号，然后 #using 语句引用了也已定义该符号的程序集。 程序集中的符号将被忽略。

## <a name="example"></a>示例

下面的示例使用一个名为 ClassA 类型创建了一个组件。

```csharp
// C4944.cs
// compile with: /target:library
// C# source code to create a dll
public class ClassA {
   public int i;
}
```

## <a name="example"></a>示例

以下示例生成 C4944。

```cpp
// C4944b.cpp
// compile with: /clr /W1
class ClassA {
public:
   int u;
};

#using "C4944.dll"   // C4944 ClassA also defined C4944.dll

int main() {
   ClassA * x = new ClassA();
   x->u = 9;
   System::Console::WriteLine(x->u);
}
```