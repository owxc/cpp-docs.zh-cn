---
title: atomic_flag 结构
ms.date: 11/04/2016
f1_keywords:
- atomic/std::atomic_flag
- atomic/std::atomic_flag::clear
- atomic/std::atomic_flag::test_and_set
ms.assetid: 17f0c2f5-fd39-4a44-873a-b569720a670e
ms.openlocfilehash: 36944c3c3bdc58272d87bbcdfb119d1c52c43995
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447406"
---
# <a name="atomicflag-structure"></a>atomic_flag 结构

描述一个对象, 该对象以原子方式设置并清除**布尔**型标志。 对原子标志执行的操作始终是无锁的。

## <a name="syntax"></a>语法

```cpp
struct atomic_flag;
```

## <a name="members"></a>成员

### <a name="public-methods"></a>公共方法

|名称|描述|
|----------|-----------------|
|[clear](#clear)|将存储的标志设置为**false**。|
|[test_and_set](#test_and_set)|将存储的标志设置为**true** , 并返回初始标志值。|

## <a name="remarks"></a>备注

`atomic_flag` 对象可传递给非成员函数 [atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)、[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)、[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set) 和 [atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)。 可使用值 `ATOMIC_FLAG_INIT` 对其进行初始化。

## <a name="requirements"></a>要求

**标头:** \<原子 >

**命名空间：** std

## <a name="clear"></a>  atomic_flag::clear

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束内, 将`*this`存储的**bool**标志设置为**false**。

```cpp
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) volatile noexcept;
void atomic_flag::clear(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>参数

*为了*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

## <a name="test_and_set"></a>  atomic_flag::test_and_set

在指定的[memory_order](../standard-library/atomic-enums.md#memory_order_enum)约束内, 将`*this`存储在中的**bool**标志设置为**true**。

```cpp
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) volatile noexcept;
bool atomic_flag::test_and_set(memory_order Order = memory_order_seq_cst) noexcept;
```

### <a name="parameters"></a>参数

*为了*\
[memory_order](../standard-library/atomic-enums.md#memory_order_enum)。

### <a name="return-value"></a>返回值

存储在 `*this` 中的标志的初始值。

## <a name="see-also"></a>请参阅

[\<atomic>](../standard-library/atomic.md)
