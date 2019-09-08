---
title: QualifierSet_BeginEnumeration 函式（非受控 API 參考）
description: QualifierSet_BeginEnumeration 函數會重設物件的限定詞枚舉器。
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b75c51ebddd78e447fed57b22a96c2d5c35004e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798342"
---
# <a name="qualifierset_beginenumeration-function"></a>QualifierSet_BeginEnumeration 函式

將物件限定詞的列舉程式重設為列舉開始時的狀態。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。

`lFlags`\
在在 [[備註](#remarks)] 區段中所描述的旗標或值的位元組合，指定要包含在列舉中的限定詞。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `lFlags` 參數無效。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`QualifierSet_BeginEnumeration`時，不需要介入的[`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md)呼叫。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可以開始新的列舉。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemQualifierSet：： BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration)方法的呼叫。

若要列舉物件上的所有限定詞，必須在第一次呼叫[QualifierSet_Next](qualifierset-next.md)之前，呼叫這個方法。 辨識限定詞的順序，保證對指定的列舉而言是不變的。

可當做`lEnumFlags`引數傳遞的旗標會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。

|常數  |值  |描述  |
|---------|---------|---------|
|  | 0 | 傳回所有限定詞的名稱。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 只傳回目前屬性或物件的特定限定詞名稱。 <br/> 若為屬性：只傳回屬性的特定限定詞（包括覆寫），而不是從類別定義傳播的限定詞。 <br/> 針對實例：只傳回實例特有的限定詞名稱。 <br/> 若為類別：只傳回衍生的類別特定的限定詞。
|`WBEM_FLAG_PROPAGATED_ONLY` | 0x20 | 只傳回從另一個物件傳播的限定詞名稱。 <br/> 若為屬性：只傳回從類別定義傳播到這個屬性的限定詞，而不是屬性本身的辨識符號。 <br/> 針對實例：只傳回從類別定義傳播的限定詞。 <br/> 若為類別：只傳回繼承自父類別的限定詞名稱。 |

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
