---
title: 下一個函式 （Unmanaged API 參考）
description: 下一個函式擷取列舉中的下一個屬性。
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
ms.openlocfilehash: 240544330fa352cbfdc01944e4be6bcad28dc96f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373190"
---
# <a name="next-function"></a>下一個函式
擷取開頭呼叫列舉中的下一個屬性[BeginEnumeration](beginenumeration.md)。

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
[in]未使用此參數。

`ptr`\
[in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`lFlags`\
[in] 保留。 這個參數必須是 0。

`pstrName`\
[out]新`BSTR`含有屬性名稱。 您可以將此參數設定為`null`如果名稱不需要。

`pVal`\
[out]A`VARIANT`填滿屬性的值。 您可以將此參數設定為`null`如果不需要值。 如果函數傳回的錯誤碼`VARIANT`傳遞至`pVal`左未經修改。

`pvtType`\
[out]指標`CIMTYPE`變數 (`LONG`到置於屬性的型別)。 這個屬性的值可以是`VT_NULL_VARIANT`，在此情況下就必須判斷屬性的實際型別。 這個參數也可以是`null`。

`plFlavor`\
[out]`null`，或接收的原始伺服器上的資訊屬性的值。 請參閱 [備註] 區段，如需可能值。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | 已有一般失敗。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_UNEXPECTED` | 0x8004101d | 沒有不需要呼叫[ `BeginEnumeration` ](beginenumeration.md)函式。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可供開始新的列舉型別。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 遠端程序之間的呼叫失敗的 Windows 管理與目前的處理序。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_NO_MORE_DATA` | 0x40005 | 列舉中沒有更多的屬性。 |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next)方法。

這個方法也會傳回系統屬性。

如果屬性的基礎類型的物件路徑、 日期或時間或另一種特殊類型，傳回的型別並不會包含足夠的資訊。 呼叫端必須檢查`CIMTYPE`来判斷屬性是否有物件參考、 日期或時間或另一種特殊類型的指定屬性。

如果`plFlavor`不是`null`，則`LONG`值接收屬性的原始伺服器的相關資訊，如下所示：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | 0x40 | 屬性是標準的系統屬性。 |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | 0x20 | 類別：屬性被繼承自父類別。 <br> 執行個體：屬性，而繼承自父類別中，有尚未修改的執行個體。  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | 0 | 類別：屬性屬於衍生的類別。 <br> 執行個體：執行個體; 所修改的屬性也就是所提供的值，或加入或修改限定詞。 |

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)