---
title: Put 函數（非受控 API 參考）
description: Put 函式會將新值指派給已命名的屬性。
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798393"
---
# <a name="put-function"></a>Put 函式

將具名屬性設定為新值。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`wszName`\
在屬性的名稱。 這個參數不可以是 `null`。

`lFlags`\
[in] 保留。 這個參數必須是0。

`pVal`\
在有效`VARIANT`的指標，它會成為新的屬性值。 如果`pVal` `VARIANT`為`null` ，或指向`null`類型`VT_NULL`的，則屬性會設定為。

`vtType`\
在所`VARIANT` 指向`pVal`的類型。 如需詳細資訊，請參閱[備註](#remarks)一節。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 發生一般失敗。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 一或多個參數無效。 |
|`WBEM_E_INVALID_PROPERTY_TYPE` | 0x8004102a | 無法辨識屬性類型。 建立類別實例時，如果類別已經存在，就會傳回這個值。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
| `WBEM_E_TYPE_MISMATCH` | 0x80041005 | 針對實例：`pVal`表示指向`VARIANT`屬性的不正確類型的。 <br/> 針對類別定義：屬性已經存在於父類別中，而新的 COM 類型與舊的 COM 類型不同。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。 |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：:P](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)的工作方法的呼叫。

此函式一律會以新的屬性值覆寫。 如果[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向類別定義， `Put`則會建立或更新屬性值。 當[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)指向 CIM 實例時， `Put`只會更新屬性值。`Put`無法建立屬性值。

只有在類別建立期間，系統屬性可能不會保留空白時，才可寫入。`__CLASS` 所有其他的系統屬性都是唯讀的。

使用者無法以底線（"_"）來建立名稱開頭或結尾的屬性。 這會保留給系統類別和屬性。

如果函式所設定`Put`的屬性存在於父類別中，除非屬性類型與父類別類型不相符，否則屬性的預設值會變更。 如果屬性不存在，而且不是類型不符，則會建立屬性。

`VARIANT` `pVal` `null`只有在 CIM 類別定義中建立新屬性，且為或指向類型`VT_NULL`的時，才使用參數。`vtType` 在此情況下， `vType`參數會指定屬性的 CIM 類型。 在其他所有情況下`vtType` ，必須是0。 `vtType`如果基礎物件是實例（即使`Val`是`null`），則也必須是0，因為屬性的類型是固定的，而且無法變更。

## <a name="example"></a>範例

如需範例，請參閱[IWbemClassObject：:P](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put)的工作方法。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
