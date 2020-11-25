---
title: 'Next function (非受控 API 參考) '
description: 下一個函數會捕獲列舉中的下一個屬性。
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: c2a7fae32e82caae40a95bfdad10fa78082988ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726778"
---
# <a name="next-function"></a>Next 函式

抓取列舉中的下一個屬性，其開頭為 [BeginEnumeration](beginenumeration.md)的呼叫。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
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

`lFlags`\
[in] 保留。 此參數必須為0。

`pstrName`\
擴展 `BSTR` 包含屬性名稱的新。 `null`如果名稱不是必要的，您可以將此參數設定為。

`pVal`\
擴展 `VARIANT` 填滿屬性值的。 如果不需要此值，您可以將此參數設定為 `null` 。 如果函式傳回錯誤碼，則 `VARIANT` 傳遞至的 `pVal` 會保持未修改狀態。

`pvtType`\
擴展變數的指標， `CIMTYPE` (將 `LONG` 屬性的型別放置) 。 這個屬性的值可以是 `VT_NULL_VARIANT` ，在這種情況下，必須判斷屬性的實際類型。 此參數也可以是 `null` 。

`plFlavor`\
[out] `null` ，或在屬性的原點接收資訊的值。 如需可能的值，請參閱 [備註] 區段。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值是在 *WbemCli .h* 標頭檔中定義，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有函數的呼叫 [`BeginEnumeration`](beginenumeration.md) 。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可用來開始新的列舉。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程與 Windows 管理之間的遠端程序呼叫失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有其他屬性。 |

## <a name="remarks"></a>備註

此函數會包裝對 [IWbemClassObject：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) 方法的呼叫。

這個方法也會傳回系統屬性。

如果屬性的基礎類型是物件路徑、日期或時間或其他特殊類型，則傳回的型別不會包含足夠的資訊。 呼叫端必須檢查 `CIMTYPE` 是否有指定的屬性，以判斷屬性是否為物件參考、日期或時間，或另一種特殊類型。

如果 `plFlavor` 不是 `null` ，此 `LONG` 值會接收有關屬性來源的資訊，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 針對類別：屬性繼承自父類別。 <br> 針對實例：實例尚未修改屬性（繼承自父類別）。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 若為類別：屬性屬於衍生類別。 <br> 針對實例：此屬性是由實例修改;亦即，已提供值，或新增或修改了限定詞。 |

## <a name="requirements"></a>需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils .idl

**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
