---
title: _ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l
ms.date: 11/04/2016
api_name:
- _ismbclegal_l
- _ismbclegal
- _ismbcsymbol
- _ismbcsymbol_l
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-multibyte-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- ismbcsymbol_l
- _ismbcsymbol_l
- _ismbcsymbol
- _ismbclegal_l
- _ismbclegal
- ismbclegal_l
- ismbcsymbol
- ismbclegal
helpviewer_keywords:
- ismbcsymbol function
- ismbclegal_l function
- _istlegal_l function
- istlegal function
- _istlegal function
- _ismbcsymbol function
- _ismbclegal_l function
- ismbclegal function
- ismbcsymbol_l function
- _ismbclegal function
- _ismbcsymbol_l function
- istlegal_l function
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
ms.openlocfilehash: 4e040db584725322e98d0a82b28912eea100aff7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953801"
---
# <a name="_ismbclegal-_ismbclegal_l-_ismbcsymbol-_ismbcsymbol_l"></a>_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l

检查多字节字符是合法字符还是符号字符。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
int _ismbclegal(
   unsigned int c
);
int _ismbclegal_l(
   unsigned int c,
   _locale_t locale
);
int _ismbcsymbol(
   unsigned int c
);
int _ismbcsymbol_l(
   unsigned int c,
   _locale_t locale
);
```

### <a name="parameters"></a>参数

*c*<br/>
要测试的字符。

*locale*<br/>
要使用的区域设置。

## <a name="return-value"></a>返回值

其中每个例程在字符满足测试条件时返回一个非零值，在不满足测试条件时回 0。 如果*c*< = 255 且存在相应的 **_ismbb**例程（例如， **_ismbcalnum**对应于 **_ismbbalnum**），则结果为相应 **_ismbb**例程的返回值。

## <a name="remarks"></a>备注

其中每个函数都针对给定的条件测试给定的多字节字符。

这些带有 **_l**后缀的函数的版本相同，只不过它们使用传入的区域设置，而不是其与区域设置相关的行为的当前区域设置。 有关详细信息，请参阅 [Locale](../../c-runtime-library/locale.md)。

|例程所返回的值|测试条件|代码页 932 示例|
|-------------|--------------------|---------------------------|
|**_ismbclegal**|有效多字节|当且仅当*c*的第一个字节在 0X81-0X9F 或 0XE0-0xFC 范围内，而第二个字节在 0X40-0x7E 或 0X80-FC 范围内时返回非零值。|
|**_ismbcsymbol**|多字节字符|当且仅当 0x8141 < =*c*< = 0x81AC 时返回非零值。|

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_istlegal**|始终返回 false|**_ismbclegal**|始终返回 false。|
|**_istlegal_l**|始终返回 false|**_ismbclegal_l**|始终返回 false。|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_ismbclegal**、 **_ismbclegal_l**|\<mbstring.h>|
|**_ismbcsymbol**、 **_ismbcsymbol_l**|\<mbstring.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[字符分类](../../c-runtime-library/character-classification.md)<br/>
[_ismbc 例程](../../c-runtime-library/ismbc-routines.md)<br/>
[is、isw 例程](../../c-runtime-library/is-isw-routines.md)<br/>
[_ismbb 例程](../../c-runtime-library/ismbb-routines.md)<br/>
