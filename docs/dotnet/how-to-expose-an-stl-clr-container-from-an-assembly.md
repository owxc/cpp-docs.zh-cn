---
title: 如何：公开从程序集中的 STL/CLR 容器
ms.date: 11/04/2016
helpviewer_keywords:
- STL/CLR Containers [STL/CLR]
- STL/CLR, cross-assembly issues
ms.assetid: 87efb41b-3db3-4498-a2e7-f3ef8a99f04d
ms.openlocfilehash: 206a95cbaa808f54d7ae0e500b5a2bea272d974b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387326"
---
# <a name="how-to-expose-an-stlclr-container-from-an-assembly"></a>如何：公开从程序集中的 STL/CLR 容器

STL/CLR 容器，如`list`和`map`作为模板 ref 类实现。 因为C++在编译时实例化模板，具有相同的签名，但位于不同的程序集的两个模板类是实际不同的类型。 这意味着不能跨程序集边界使用模板类。

若要使跨程序集共享成为可能，STL/CLR 容器实现泛型接口<xref:System.Collections.Generic.ICollection%601>。 通过使用此泛型接口，所有语言的都支持泛型，包括C++， C#，和 Visual Basic 中，可以访问 STL/CLR 容器。

本主题演示如何显示几个 STL/CLR 容器写入的元素C++程序集名为`StlClrClassLibrary`。 我们显示两个程序集访问`StlClrClassLibrary`。 第一个程序集用C++，并在第二个C#。

如果两个程序集用C++，可以使用访问容器的泛型接口及其`generic_container`typedef。 例如，如果你有一个类型的容器`cliext::vector<int>`，则其泛型接口是： `cliext::vector<int>::generic_container`。 同样，您可以获取一个迭代器，通过泛型接口使用`generic_iterator`typedef，如下所示： `cliext::vector<int>::generic_iterator`。

由于这些 typedef 声明中C++标头文件，用其他语言编写的程序集不能使用它们。 因此，若要访问的泛型接口`cliext::vector<int>`在 C# 或任何其他.NET 语言中，使用`System.Collections.Generic.ICollection<int>`。 若要循环访问此集合，使用`foreach`循环。

下表列出了每个 STL/CLR 容器实现的泛型接口：

|STL/CLR 容器|泛型接口|
|------------------------|-----------------------|
|`deque<T>`|`ICollection<T>`|
|`hash_map<K, V>`|`IDictionary<K, V>`|
|`hash_multimap<K, V>`|`IDictionary<K, V>`|
|`hash_multiset<T>`|`ICollection<T>`|
|`hash_set<T>`|`ICollection<T>`|
|`list<T>`|`ICollection<T>`|
|`map<K, V>`|`IDictionary<K, V>`|
|`multimap<K, V>`|`IDictionary<K, V>`|
|`multiset<T>`|`ICollection<T>`|
|`set<T>`|`ICollection<T>`|
|`vector<T>`|`ICollection<T>`|

> [!NOTE]
> 因为`queue`， `priority_queue`，和`stack`容器不支持迭代器，它们未实现泛型接口，不能访问的跨程序集。

## <a name="example-1"></a>示例 1

### <a name="description"></a>描述

在此示例中，我们声明C++类，该类包含专用的 STL/CLR 成员数据。 然后，我们声明用于授予访问权限的专用集合类的公共方法。 我们在两种不同方法，一个用于C++客户端，另一个用于其他.NET 客户端。

### <a name="code"></a>代码

```cpp
// StlClrClassLibrary.h
#pragma once

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/stack>
#include <cliext/vector>

using namespace System;
using namespace System::Collections::Generic;
using namespace cliext;

namespace StlClrClassLibrary {

    public ref class StlClrClass
    {
    public:
        StlClrClass();

        // These methods can be called by a C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        deque<wchar_t>::generic_container ^GetDequeCpp();
        list<float>::generic_container ^GetListCpp();
        map<int, String ^>::generic_container ^GetMapCpp();
        set<double>::generic_container ^GetSetCpp();
        vector<int>::generic_container ^GetVectorCpp();

        // These methods can be called by a non-C++ class
        // in another assembly to get access to the
        // private STL/CLR types defined below.
        ICollection<wchar_t> ^GetDequeCs();
        ICollection<float> ^GetListCs();
        IDictionary<int, String ^> ^GetMapCs();
        ICollection<double> ^GetSetCs();
        ICollection<int> ^GetVectorCs();

    private:
        deque<wchar_t> ^aDeque;
        list<float> ^aList;
        map<int, String ^> ^aMap;
        set<double> ^aSet;
        vector<int> ^aVector;
    };
}
```

## <a name="example-2"></a>示例 2

### <a name="description"></a>描述

在此示例中，我们实现在示例 1 中声明的类。 为了使客户端使用此类库，我们使用该清单工具**mt.exe**将嵌入到该 DLL 的清单文件。 有关详细信息，请参阅代码注释。

清单工具和通过并行程序集的详细信息，请参阅[生成 C /C++独立应用程序和通过并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)。

### <a name="code"></a>代码

```cpp
// StlClrClassLibrary.cpp
// compile with: /clr /LD /link /manifest
// post-build command: (attrib -r StlClrClassLibrary.dll & mt /manifest StlClrClassLibrary.dll.manifest /outputresource:StlClrClassLibrary.dll;#2 & attrib +r StlClrClassLibrary.dll)

#include "StlClrClassLibrary.h"

namespace StlClrClassLibrary
{
    StlClrClass::StlClrClass()
    {
        aDeque = gcnew deque<wchar_t>();
        aDeque->push_back(L'a');
        aDeque->push_back(L'b');

        aList = gcnew list<float>();
        aList->push_back(3.14159f);
        aList->push_back(2.71828f);

        aMap = gcnew map<int, String ^>();
        aMap[0] = "Hello";
        aMap[1] = "World";

        aSet = gcnew set<double>();
        aSet->insert(3.14159);
        aSet->insert(2.71828);

        aVector = gcnew vector<int>();
        aVector->push_back(10);
        aVector->push_back(20);
    }

    deque<wchar_t>::generic_container ^StlClrClass::GetDequeCpp()
    {
        return aDeque;
    }

    list<float>::generic_container ^StlClrClass::GetListCpp()
    {
        return aList;
    }

    map<int, String ^>::generic_container ^StlClrClass::GetMapCpp()
    {
        return aMap;
    }

    set<double>::generic_container ^StlClrClass::GetSetCpp()
    {
        return aSet;
    }

    vector<int>::generic_container ^StlClrClass::GetVectorCpp()
    {
        return aVector;
    }

    ICollection<wchar_t> ^StlClrClass::GetDequeCs()
    {
        return aDeque;
    }

    ICollection<float> ^StlClrClass::GetListCs()
    {
        return aList;
    }

    IDictionary<int, String ^> ^StlClrClass::GetMapCs()
    {
        return aMap;
    }

    ICollection<double> ^StlClrClass::GetSetCs()
    {
        return aSet;
    }

    ICollection<int> ^StlClrClass::GetVectorCs()
    {
        return aVector;
    }
}
```

## <a name="example-3"></a>示例 3

### <a name="description"></a>描述

在此示例中，我们将创建C++使用示例 1 和 2 中创建的类库的客户端。 此客户端使用`generic_container`来循环访问容器，并显示其内容的 STL/CLR 容器的 typedef。

### <a name="code"></a>代码

```cpp
// CppConsoleApp.cpp
// compile with: /clr /FUStlClrClassLibrary.dll

#include <cliext/deque>
#include <cliext/list>
#include <cliext/map>
#include <cliext/set>
#include <cliext/vector>

using namespace System;
using namespace StlClrClassLibrary;
using namespace cliext;

int main(array<System::String ^> ^args)
{
    StlClrClass theClass;

    Console::WriteLine("cliext::deque contents:");
    deque<wchar_t>::generic_container ^aDeque = theClass.GetDequeCpp();
    for each (wchar_t wc in aDeque)
    {
        Console::WriteLine(wc);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::list contents:");
    list<float>::generic_container ^aList = theClass.GetListCpp();
    for each (float f in aList)
    {
        Console::WriteLine(f);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::map contents:");
    map<int, String ^>::generic_container ^aMap = theClass.GetMapCpp();
    for each (map<int, String ^>::value_type rp in aMap)
    {
        Console::WriteLine("{0} {1}", rp->first, rp->second);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::set contents:");
    set<double>::generic_container ^aSet = theClass.GetSetCpp();
    for each (double d in aSet)
    {
        Console::WriteLine(d);
    }
    Console::WriteLine();

    Console::WriteLine("cliext::vector contents:");
    vector<int>::generic_container ^aVector = theClass.GetVectorCpp();
    for each (int i in aVector)
    {
        Console::WriteLine(i);
    }
    Console::WriteLine();

    return 0;
}
```

### <a name="output"></a>Output

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="example-4"></a>示例 4

### <a name="description"></a>描述

在此示例中，我们创建一个 C# 客户端使用在示例 1 和 2 中创建的类库。 此客户端使用<xref:System.Collections.Generic.ICollection%601>STL/CLR 容器来循环访问容器，并显示其内容的方法。

### <a name="code"></a>代码

```csharp
// CsConsoleApp.cs
// compile with: /r:Microsoft.VisualC.STLCLR.dll /r:StlClrClassLibrary.dll /r:System.dll

using System;
using System.Collections.Generic;
using StlClrClassLibrary;
using cliext;

namespace CsConsoleApp
{
    class Program
    {
        static int Main(string[] args)
        {
            StlClrClass theClass = new StlClrClass();

            Console.WriteLine("cliext::deque contents:");
            ICollection<char> iCollChar = theClass.GetDequeCs();
            foreach (char c in iCollChar)
            {
                Console.WriteLine(c);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::list contents:");
            ICollection<float> iCollFloat = theClass.GetListCs();
            foreach (float f in iCollFloat)
            {
                Console.WriteLine(f);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::map contents:");
            IDictionary<int, string> iDict = theClass.GetMapCs();
            foreach (KeyValuePair<int, string> kvp in iDict)
            {
                Console.WriteLine("{0} {1}", kvp.Key, kvp.Value);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::set contents:");
            ICollection<double> iCollDouble = theClass.GetSetCs();
            foreach (double d in iCollDouble)
            {
                Console.WriteLine(d);
            }
            Console.WriteLine();

            Console.WriteLine("cliext::vector contents:");
            ICollection<int> iCollInt = theClass.GetVectorCs();
            foreach (int i in iCollInt)
            {
                Console.WriteLine(i);
            }
            Console.WriteLine();

            return 0;
        }
    }
}
```

### <a name="output"></a>Output

```Output
cliext::deque contents:
a
b

cliext::list contents:
3.14159
2.71828

cliext::map contents:
0 Hello
1 World

cliext::set contents:
2.71828
3.14159

cliext::vector contents:
10
20
```

## <a name="see-also"></a>请参阅

[STL/CLR 库参考](../dotnet/stl-clr-library-reference.md)
