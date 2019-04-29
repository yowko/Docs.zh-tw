---
title: Get 函式 （Unmanaged API 參考）
description: Get 函式會擷取指定之的屬性的值。
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
ms.openlocfilehash: 7534d760f902f80d42c6c20c57a34d52012997a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608992"
---
# <a name="get-function"></a>Get 函式

若有的話，則擷取指定的屬性值。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```
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
[in]未使用此參數。

`ptr`\
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`wszName`\
[in]屬性的名稱。

`lFlags`\
[in] 保留。 這個參數必須是 0。

`pVal`\
[out]如果函式會傳回成功，則包含值的`wszName`屬性。 `pval`引數指派正確的型別和辨識符號值。

`pvtType`\
[out]如果函式會傳回成功，就會包含[CIM 類型常數](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration)表示的屬性型別。 其值也可以是`null`。 

`plFlavor`\
[out]如果函式會傳回成功，會收到之屬性的原點資訊。 其值可以是`null`，或其中一個定義中的下列 WBEM_FLAVOR_TYPE 常數*WbemCli.h*標頭檔： 

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 類別：屬性被繼承自父類別。 <br> 執行個體：屬性，而繼承自父類別中，有尚未修改的執行個體。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 類別：屬性屬於衍生的類別。 <br> 執行個體：執行個體; 所修改的屬性也就是所提供的值，或加入或修改限定詞。 |

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 找不到有效的一或多個參數。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成此作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法。

`Get`函式也可以傳回系統屬性。

`pVal`引數指派正確的型別和值限定詞和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函式

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **標頭：** WMINet_Utils.idl

 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)