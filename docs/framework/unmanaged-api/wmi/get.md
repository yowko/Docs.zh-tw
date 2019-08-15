---
title: Get 函式 (非受控 API 參考)
description: Get 函式會抓取指定的屬性值。
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 265d3edbd3175eebcf6fd35be24f5b66144c960f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69037958"
---
# <a name="get-function"></a>Get 函式

抓取指定的屬性值 (如果有的話)。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Get (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
); 
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`wszName`\
在屬性的名稱。

`lFlags`\
[in] 保留。 這個參數必須是0。

`pVal`\
脫銷如果函數傳回成功, 則包含`wszName`屬性的值。 已針對限定詞指派正確的類型和值給引數。`pval`

`pvtType`\
脫銷如果函式傳回成功, 則包含表示屬性類型的[CIM 類型常數](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration)。 其值也可以是`null`。 

`plFlavor`\
脫銷如果函式傳回成功, 會接收屬性來源的相關資訊。 其值可以是`null`, 或是*WbemCli*標頭檔中所定義的下列其中一個 WBEM_FLAVOR_TYPE 常數: 

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 若為類別:屬性繼承自父類別。 <br> 針對實例:繼承自父類別的屬性尚未由實例修改。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 若為類別:屬性屬於衍生類別。 <br> 針對實例:屬性會由實例修改;也就是, 已提供值, 或已新增或修改限定詞。 |

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中, 您也可以在程式碼中將它們定義為常數:

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法的呼叫。

`Get`函數也可以傳回系統屬性。

已針對限定詞和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函數指派正確的類型和值給引數`pVal`

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **標頭：** WMINet_Utils.idl

 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 (非受控 API 參考)](index.md)
