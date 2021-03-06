---
title: 受限 (C++ COM 特性)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 01dabcd15eb1a14734c16b9e54c0ab2e030d0479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514058"
---
# <a name="restricted"></a>restricted

指定不能任意调用模块、接口或调度接口的成员。

## <a name="syntax"></a>语法

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>参数

*interfaces*<br/>
不能对 COM 对象任意调用的一个或多个接口。 仅当应用于类时, 此参数才有效。

## <a name="remarks"></a>备注

**受限** C++特性具有与[受限制](/windows/win32/Midl/restricted)的 MIDL 特性相同的功能。

## <a name="example"></a>示例

下面的代码演示如何使用**受限**特性:

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>要求

### <a name="attribute-context"></a>特性上下文

|||
|-|-|
|**适用于**|接口方法、**接口**、**类**、**结构**|
|**可重复**|No|
|**必需的特性**|**coclass**(应用于**类**或**结构**时)|
|**无效的特性**|无|

有关特性上下文的详细信息，请参见 [特性上下文](cpp-attributes-com-net.md#contexts)。

## <a name="see-also"></a>请参阅

[IDL 特性](idl-attributes.md)<br/>
[接口特性](interface-attributes.md)<br/>
[方法特性](method-attributes.md)