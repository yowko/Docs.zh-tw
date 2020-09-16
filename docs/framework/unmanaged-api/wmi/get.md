---
title: '取得函式 (非受控 API 參考) '
description: Get 函數會抓取指定的屬性值。
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
ms.openlocfilehash: 7cc0c285f79b2791863fce251e4683aa7b55341b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553684"
---
# <a name="get-function"></a>Get 函式

如果存在，則抓取指定的屬性值。

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
在此參數未使用。

`ptr`\
在 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) 實例的指標。

`wszName`\
在屬性的名稱。

`lFlags`\
[in] 保留。 此參數必須為0。

`pVal`\
擴展如果函數傳回成功，則包含屬性的值 `wszName` 。 `pval`引數會被指派正確的辨識符號類型和值。

`pvtType`\
擴展如果函數傳回成功，則包含表示屬性類型的 [CIM 類型常數](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) 。 其值也可以是 `null` 。

`plFlavor`\
擴展如果函式傳回成功，則會接收有關屬性來源的資訊。 其值可以是 `null` 或 *WbemCli* 中定義的下列其中一項 WBEM_FLAVOR_TYPE 常數：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 針對類別：屬性繼承自父類別。 <br> 針對實例：實例尚未修改屬性（繼承自父類別）。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 若為類別：屬性屬於衍生類別。 <br> 針對實例：此屬性是由實例修改;亦即，已提供值，或新增或修改了限定詞。 |

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效。 |
|`WBEM_E_NOT_FOUND` | 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 可用的記憶體不足，無法完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) 方法的呼叫。

`Get`函數也可以傳回系統屬性。

`pVal`引數已指派限定詞和 COM [VariantInit](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit)函式的正確類型和值

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** WMINet_Utils .idl

 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
