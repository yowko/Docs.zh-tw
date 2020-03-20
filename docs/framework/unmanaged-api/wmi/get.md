---
title: 獲取功能（非託管 API 引用）
description: Get 函數檢索指定的屬性值。
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
ms.openlocfilehash: 67fcfb301eebfcf4ed4fdcaa5c9ddf85c47a6073
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174975"
---
# <a name="get-function"></a>Get 函式

如果指定的屬性值存在，則檢索該值。

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
[在]此參數未使用。

`ptr`\
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`wszName`\
[在]屬性的名稱。

`lFlags`\
[in] 保留。 此參數必須為 0。

`pVal`\
[出]如果函數成功返回，則包含`wszName`屬性的值。 為`pval`限定詞分配了正確的類型和值。

`pvtType`\
[出]如果函數成功返回，則包含指示屬性類型的[CIM 類型常量](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration)。 其值也可以`null`是 。

`plFlavor`\
[出]如果函數成功返回，則接收有關屬性源的資訊。 其值可以是`null`，或者*WbemCli.h*標標頭檔中定義的以下WBEM_FLAVOR_TYPE常量之一：

|持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 對於類：屬性是從父類繼承的。 <br> 對於實例：屬性雖然從父類繼承，但實例尚未修改。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 對於類：屬性屬於派生類。 <br> 對於實例：屬性由實例修改;但是，該屬性由 實例修改。即，提供了值，或者添加或修改了限定詞。 |

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 出現了一個普遍的失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一個或多個參數無效。 |
|`WBEM_E_NOT_FOUND` | 0 x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函數包裝對[IWbem ClassObject 的調用：：get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get)方法。

該`Get`函數還可以返回系統屬性。

為`pVal`限定詞和 COM [VariantInit](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函數分配了正確的類型和值

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標題：** WMINet_Utils.idl

 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
