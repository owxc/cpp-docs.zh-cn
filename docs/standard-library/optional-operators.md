---
title: '&lt;可选&gt;运算符'
ms.date: 11/04/2016
f1_keywords:
- optional/std::operator!=
- optional/std::operator==
- optional/std::operatoroperator&gt;
- optional/std::operatoroperator&gt=;
- optional/std::operatoroperator&lt;
- optional/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (optional)
- std::operator== (optional)
- std::operatoroperator&gt; (optional)
- std::operatoroperator&gt=; (optional)
- std::operatoroperator&lt; (optional)
- std::operatoroperator&lt;= (optional)
ms.openlocfilehash: c5d0de435180054b186400384fc0583df5b03246
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268919"
---
# <a name="ltoptionalgt-operators"></a>&lt;可选&gt;运算符

## <a name="op_eq_eq"></a> 运算符 = =

测试运算符左侧的 `optional` 对象是否等于右侧的 `optional` 对象。

```cpp
template <class T, class U> constexpr bool operator==(const optional<T>& left, const optional<U>& right);
template <class T> constexpr bool operator==(const optional<T>& left, nullopt_t right) noexcept;
template <class T> constexpr bool operator==(nullopt_t left, const optional<T>& right) noexcept;
template <class T, class U> constexpr bool operator==(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator==(const U&, const optional<T>&);
```

### <a name="parameters"></a>参数

*左侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

*右侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

## <a name="op_neq"></a> 运算符 ！ =

测试运算符左侧的 `optional` 对象是否不等于右侧的 `optional` 对象。

```cpp
template <class T, class U> constexpr bool operator!=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator!=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator!=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator!=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator!=(const U&, const optional<T>&);
```

### <a name="parameters"></a>参数

*左侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

*右侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

### <a name="remarks"></a>备注

此模板函数返回 `!(left == right)`。

## <a name="op_lt"></a> 运算符&lt;

测试运算符左侧的 `optional` 对象是否小于右侧的 `optional` 对象。

```cpp
template <class T, class U> constexpr bool operator<(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<(const U&, const optional<T>&);
```

### <a name="parameters"></a>参数

*左侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

*右侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

### <a name="return-value"></a>返回值

如果运算符左侧的列表小于但不等于运算符右侧的列表，则为 **true**，否则为 **false**。

## <a name="op_lt_eq"></a>  operator&lt;=

测试运算符左侧的 `optional` 对象是否小于或等于右侧的 `optional` 对象。

```cpp
template <class T, class U> constexpr bool operator<=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator<=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator<=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator<=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator<=(const U&, const optional<T>&);
```

### <a name="parameters"></a>参数

*左侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

*右侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

### <a name="return-value"></a>返回值

如果运算符左侧的列表小于或等于运算符右侧的列表，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此模板函数返回 `!(right < left)`。

## <a name="op_gt"></a> 运算符&gt;

测试运算符左侧的 `optional` 对象是否大于右侧的 `optional` 对象。

```cpp
template <class T, class U> constexpr bool operator>(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>(const U&, const optional<T>&);
```

### <a name="parameters"></a>参数

*左侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

*右侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

### <a name="return-value"></a>返回值

如果运算符左侧的列表大于右侧的列表，则为 **true**，否则为 **false**。

### <a name="remarks"></a>备注

此模板函数返回 `right < left`。

## <a name="op_gt_eq"></a> 运算符&gt;=

测试运算符左侧的 `optional` 对象是否大于或等于右侧的 `optional` 对象。

```cpp
template <class T, class U> constexpr bool operator>=(const optional<T>&, const optional<U>&);
template <class T> constexpr bool operator>=(const optional<T>&, nullopt_t) noexcept;
template <class T> constexpr bool operator>=(nullopt_t, const optional<T>&) noexcept;
template <class T, class U> constexpr bool operator>=(const optional<T>&, const U&);
template <class T, class U> constexpr bool operator>=(const U&, const optional<T>&);
```

### <a name="parameters"></a>参数

*左侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

*右侧*\
类型的对象`optional`， `nullopt_t`，或`T`。

### <a name="return-value"></a>返回值

如果运算符左侧的 `optional` 大于或等于右侧的 `optional`，则为 **true**；否则为 **false**。

### <a name="remarks"></a>备注

此模板函数返回 `!(left < right)`。
