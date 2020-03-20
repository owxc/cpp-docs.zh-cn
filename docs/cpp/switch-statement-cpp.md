---
title: switch 语句 (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 8136b03d9e54b4d49bcb1417238066bd86bc6b89
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221935"
---
# <a name="switch-statement-c"></a>switch 语句 (C++)

允许根据整型表达式的值在多个代码段中进行选择。

## <a name="syntax"></a>语法

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>备注

*expression* 必须是一种整型类型或明确转换为整型类型的类类型。 整型提升的情况见[标准转换](standard-conversions.md)中的描述。

**switch** 语句体由一系列 **case** 标签和一个可选的 **default** 标签组成。在 **case**语句任何两个常量表达式的值都不能相同。**default** 标签仅可以出现一次。标签语句不是语法要求，但如果没有它们 **switch** 语句是无意义的。default 语句不必须在末尾；它可以放在 switch 语句体的任何位置。 case 或 default 标签只能出现在 switch 语句内。

在每个 **case** 标签中的 *constant-expression* 会被转换为 *expression* 的类型并与 *expression* 比较是否相等。 控制将传递给 *constant-expression* 的值与之匹配的 *expression* 的**case** 。 下表中显示了生成的行为。

### <a name="switch-statement-behavior"></a>switch 语句行为

|条件|操作|
|---------------|------------|
|转换后的值与提升的控制表达式的值匹配。|控制将转移到跟在该标签后面的语句。|
|没有匹配任何**case**标签；**default**标签存在。|控制权转至**default**标签。|
|没有匹配任何**case**标签；**default**标签不存在。|控制权转交给**switch**语句之后的语句。|

如果找到匹配的表达式，控制不会被后续的 **case** 或 **default** 标签阻断。 [break](../cpp/break-statement-cpp.md) 语句用于停止执行并将控制转移到 **switch** 语句之后的语句。 如果没有 **break** 语句，从匹配的 **case** 标签到 **switch** 的末尾，包括 **default**，都会执行。 例如：

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

在上面的示例中，如果 `c` 是大写 `A` ，则 `capa` 将递增。 **break** 之后的语句 `capa++`终止执行 **switch** 语句体并将控制转移到 **while** 循环。 如果没有 **break** 语句中，执行将"贯穿"到下一个标记语句，这样 `lettera` 和 `nota` 也将递增。 相同的功能也由 `case 'a'` 的 **break** 语句实现。 如果 `c` 是一个小写 `a` ，`lettera` 会递增并且 **break**语句将终止 **switch** 语句体。 如果 `c` 不是 `a` 或 `A` ，则执行 **default** 语句。

**2017 及更高版本的 visual Studio:** (适用于[/std:C++ 17](../build/reference/std-specify-language-standard-version.md)) `[[fallthrough]]` 属性已在 C++ 17 标准中指定。 可在 **switch** 语句中使用以作为对编译器 （或任何读代码的人）的提醒：这里fall-through行为是故意为之。 Microsoft C++ 编译器当前不会警告 fallthrough 行为，因此，此属性对编译器行为没有影响。 请注意，该属性应用于标记语句中的一个空语句；换而言之，分号是必需的。

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 版本 15.3 及更高版本**(适用于[/std: c + + 17](../build/reference/std-specify-language-standard-version.md)):Switch 语句可能会引入并初始化一个变量，其作用域被限制在 switch 语句的块：

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

**switch** 语句中的内部块可以包含带有初始化的定义，只要它们是可访问 — 即，不会被所有可能的执行路径绕过。 使用这些声明引入的名称具有局部范围。 例如：

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

**switch** 语句可以嵌套。 在这种情况下，**case** 或 **default** 标签关联到包含它们的最近 **switch** 语句。

**Microsoft 专用**

Microsoft C 未限制 **switch** 语句中的 case 值的数量。 该数量仅受可用内存的限制。 ANSI C 要求 **switch** 语句允许至少 257 个 case 标签。

Microsoft C 的默认设置是启用 Microsoft 扩展。 使用[/Za](../build/reference/za-ze-disable-language-extensions.md)编译器选项来禁用这些扩展。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[选择语句](../cpp/selection-statements-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
