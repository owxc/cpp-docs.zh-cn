---
title: Platform::Collections::BackInsertIterator 类
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: be5a905725c2ed0f056f1686d17d87c74b9cdc5e
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416062"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections::BackInsertIterator 类

表示一个迭代器，它插入而非重写元素到有序集合的后端。

## <a name="syntax"></a>语法

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>parameters

*T*<br/>
当前集合中项目的类型。

### <a name="remarks"></a>备注

BackInsertIterator 类实现 [back_insert_iterator Class](../standard-library/back-insert-iterator-class.md)所要求的规则。

### <a name="members"></a>成员

### <a name="public-constructors"></a>公共构造函数

|名称|说明|
|----------|-----------------|
|[BackInsertIterator：： BackInsertIterator](#ctor)|初始化 BackInsertIterator 类的新实例。|

### <a name="public-operators"></a>公用運算子

|名称|说明|
|----------|-----------------|
|[BackInsertIterator::operator* 运算符](#operator-dereference)|检索对当前 BackInsertIterator 的引用。|
|[BackInsertIterator::operator++ 运算符](#operator-increment)|返回对当前 BackInsertIterator 的引用。 迭代器未经修改。|
|[BackInsertIterator::operator= 运算符](#operator-assign)|将指定对象追加到当前有序集合的末尾。|

## <a name="inheritance-hierarchy"></a>继承层次结构

`BackInsertIterator`

### <a name="requirements"></a>要求

**标头：** collection.h

<a name="namespace-platformcollections"></a>**命名空间：** Platform::Collections
---
## <a name="ctor"></a>BackInsertIterator：： BackInsertIterator 构造函数

初始化 `BackInsertIterator` 类的新实例。

## <a name="syntax"></a>语法

```

explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>parameters

*v*<br/>
IVector\<T > 对象。

### <a name="remarks"></a>备注

`BackInsertIterator` 在参数 `v` 指定的对象的最后一个元素之后插入元素。

## <a name="operator-assign"></a>BackInsertIterator：： operator = 运算符

将指定对象追加到当前有序集合的末尾。

## <a name="syntax"></a>语法

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>parameters

*t*<br/>
要追加到当前集合的对象。

### <a name="return-value"></a>返回值

对当前 BackInsertIterator 的引用。

## <a name="operator-dereference"></a>BackInsertIterator：： operator * 运算符

检索对当前 BackInsertIterator 的引用。

## <a name="syntax"></a>语法

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>返回值

对当前 BackInsertIterator 的引用。

### <a name="remarks"></a>备注

此运算符返回对当前 BackInsertIterator 的引用；而不是对当前集合中任何元素的引用。

## <a name="operator-increment"></a>BackInsertIterator：： operator + + 运算符

返回对当前 BackInsertIterator 的引用。 迭代器未经修改。

## <a name="syntax"></a>语法

```

BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>返回值

对当前 BackInsertIterator 的引用。

### <a name="remarks"></a>备注

按照设计，第一个语法示例前递增当前 BackInsertIterator，第二个语法后递增当前 BackInsertIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。

但是，此运算符不会实际修改 BackInsertIterator， 而是返回对未经修改的当前迭代器的引用。 这与[operator *](#operator-dereference)的行为相同。

## <a name="see-also"></a>另请参阅

[平台命名空间](platform-namespace-c-cx.md)
