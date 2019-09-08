---
title: Next 函式（非受控 API 參考）
description: 下一個函數會抓取列舉中的下一個屬性。
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95cea4cb3e7e7df2b6b52256a440b9a8d544f2db
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798406"
---
# <a name="next-function"></a>Next 函式
從呼叫[BeginEnumeration](beginenumeration.md)開始，抓取列舉中的下一個屬性。

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
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`lFlags`\
[in] 保留。 這個參數必須是0。

`pstrName`\
脫銷新`BSTR`的，其中包含屬性名稱。 如果名稱不是必要的`null` ，您可以將此參數設定為。

`pVal`\
脫銷`VARIANT`填入屬性值的。 如果不需要此值， `null`您可以將此參數設定為。 如果函式傳回錯誤碼，則不修改`VARIANT`傳遞給`pVal`的。

`pvtType`\
脫銷`CIMTYPE`變數的指標`LONG` （屬性的類型會放在其中）。 這個屬性的值可以`VT_NULL_VARIANT`是，在此情況下，必須判斷屬性的實際類型。 這個參數也可以是`null`。

`plFlavor`\
脫銷`null`，或接收屬性之來源資訊的值。 如需可能的值，請參閱 [備註] 區段。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有函數的[`BeginEnumeration`](beginenumeration.md)呼叫。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可以開始新的列舉。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 目前進程與 Windows 管理之間的遠端程序呼叫失敗。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有其他屬性。 |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next)方法的呼叫。

這個方法也會傳回系統屬性。

如果屬性的基礎類型是物件路徑、日期或時間或另一個特殊類型，則傳回的類型不會包含足夠的資訊。 呼叫端必須檢查`CIMTYPE`指定之屬性的，以判斷屬性是否為物件參考、日期或時間，或其他特殊類型。

如果`plFlavor` `LONG`不`null`是，此值會接收屬性來源的相關資訊，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 若為類別：屬性繼承自父類別。 <br> 針對實例：繼承自父類別的屬性尚未由實例修改。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 若為類別：屬性屬於衍生類別。 <br> 針對實例：屬性會由實例修改;也就是，已提供值，或已新增或修改限定詞。 |

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
