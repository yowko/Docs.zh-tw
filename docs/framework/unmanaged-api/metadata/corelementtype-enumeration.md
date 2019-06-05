---
title: CorElementType 列舉 1
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48650a85a88f36cd51adb1bbec0436fb5d75ecfb
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690376"
---
# <a name="corelementtype-enumeration1"></a>CorElementType 列舉 1

指定 common language runtime <xref:System.Type>、 型別修飾詞或在 中繼資料型別簽章類型的相關資訊。

## <a name="syntax"></a>語法

```
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a>成員

|成員|描述|
|------------|-----------------|
|`ELEMENT_TYPE_END`|在內部使用。|
|`ELEMENT_TYPE_VOID`|無效的型別。|
|`ELEMENT_TYPE_BOOLEAN`|布林型別|
|`ELEMENT_TYPE_CHAR`|字元類型。|
|`ELEMENT_TYPE_I1`|帶正負號的 1 位元整數。|
|`ELEMENT_TYPE_U1`|不帶正負號的 1 位元整數。|
|`ELEMENT_TYPE_I2`|2 位元組帶正負號的整數。|
|`ELEMENT_TYPE_U2`|2 位元組不帶正負號的整數。|
|`ELEMENT_TYPE_I4`|4 位元組帶正負號的整數。|
|`ELEMENT_TYPE_U4`|4 位元組不帶正負號的整數。|
|`ELEMENT_TYPE_I8`|8 位元組帶正負號的整數。|
|`ELEMENT_TYPE_U8`|8 位元組不帶正負號的整數。|
|`ELEMENT_TYPE_R4`|4 位元組浮點數。|
|`ELEMENT_TYPE_R8`|8 位元組浮點數。|
|`ELEMENT_TYPE_STRING`|System.String 類型。|
|`ELEMENT_TYPE_PTR`|指標型別修飾詞。|
|`ELEMENT_TYPE_BYREF`|參考型別修飾詞。|
|`ELEMENT_TYPE_VALUETYPE`|值型別修飾詞。|
|`ELEMENT_TYPE_CLASS`|類別型別修飾詞。|
|`ELEMENT_TYPE_VAR`|類別變數的類型修飾詞。|
|`ELEMENT_TYPE_ARRAY`|多維度陣列型別修飾詞。|
|`ELEMENT_TYPE_GENERICINST`|泛型類型的類型修飾詞。|
|`ELEMENT_TYPE_TYPEDBYREF`|具型別參考。|
|`ELEMENT_TYPE_I`|原生的整數的大小。|
|`ELEMENT_TYPE_U`|帶正負號的原生整數的大小。|
|`ELEMENT_TYPE_FNPTR`|函式的指標。|
|`ELEMENT_TYPE_OBJECT`|System.Object 類型。|
|`ELEMENT_TYPE_SZARRAY`|一維、 零下限陣列型別修飾詞。|
|`ELEMENT_TYPE_MVAR`|方法的變數型別修飾詞。|
|`ELEMENT_TYPE_CMOD_REQD`|C 語言所需的修飾詞。|
|`ELEMENT_TYPE_CMOD_OPT`|C 語言選擇性修飾詞。|
|`ELEMENT_TYPE_INTERNAL`|在內部使用。|
|`ELEMENT_TYPE_MAX`|類型無效。|
|`ELEMENT_TYPE_MODIFIER`|在內部使用。|
|`ELEMENT_TYPE_SENTINEL`|是一份參數數目可變的 sentinel 為類型修飾詞。|
|`ELEMENT_TYPE_PINNED`|在內部使用。|

## <a name="remarks"></a>備註

類型修飾詞會促使表示更複雜的類型。 A`CorElementType`類型修飾詞值套用至緊接在型別簽章中的值。 值，會遵循`CorElementType`型別修飾詞值可以是`CorElementType`簡單型別值、 中繼資料語彙基元或其他值，指定下表中。

> [!NOTE]
> 所有數字 (*數字*，*引數計數*，*中繼資料語彙基元*，*陣序規範*，*計數*，與*繫結*) 會儲存為壓縮的整數。 請參閱[標準 ECMA-335-通用語言基礎結構 (CLI)](https://go.microsoft.com/fwlink/?LinkID=116487)上 ECMA 造訪網站以取得詳細資料。

|類型修飾詞|格式|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|ELEMENT_TYPE_PTR \<`CorElementType`值 >|
|`ELEMENT_TYPE_BYREF`|ELEMENT_TYPE_BYREF \<`CorElementType`值 >|
|`ELEMENT_TYPE_VALUETYPE`|ELEMENT_TYPE_VALUETYPE \<`mdTypeDef`中繼資料語彙基元 >|
|`ELEMENT_TYPE_CLASS`|ELEMENT_TYPE_CLASS \<`mdTypeDef`中繼資料語彙基元 >|
|`ELEMENT_TYPE_VAR`|ELEMENT_TYPE_VAR\<數字 >|
|`ELEMENT_TYPE_ARRAY`|ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN>|
|`ELEMENT_TYPE_GENERICINST`|ELEMENT_TYPE_GENERICINST \<`mdTypeDef`中繼資料語彙基元 >\<引數計數 > \<arg1 >...\<argN >|
|`ELEMENT_TYPE_FNPTR`|Typ ELEMENT_TYPE_FNPTR\<函式，包括呼叫慣例的完整簽章 >|
|`ELEMENT_TYPE_SZARRAY`|ELEMENT_TYPE_SZARRAY \<`CorElementType`值 >|
|`ELEMENT_TYPE_MVAR`|ELEMENT_TYPE_MVAR\<數字 >|
|`ELEMENT_TYPE_CMOD_REQD`|ELEMENT_TYPE_\<`mdTypeRef`或`mdTypeDef`中繼資料語彙基元 >|
|`ELEMENT_TYPE_CMOD_OPT`|E_T_CMOD_OPT \<`mdTypeRef`或`mdTypeDef`中繼資料語彙基元 >|

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorHdr.h

**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>另請參閱

- [中繼資料列舉](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
