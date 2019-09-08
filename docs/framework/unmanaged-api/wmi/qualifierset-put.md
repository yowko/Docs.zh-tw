---
title: QualifierSet_Put 函式（非受控 API 參考）
description: QualifierSet_Put 函數會寫入已命名的限定詞和其值。
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798266"
---
# <a name="qualifierset_put-function"></a>QualifierSet_Put 函式

寫入具名限定詞與值。 新的限定詞會覆寫相同名稱的先前值。 如果辨識符號不存在，則會加以建立。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a>參數

`vFunc`\
在未使用此參數。

`ptr`\
在[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)實例的指標。

`wszName`\
在要寫入的限定詞名稱。

`pVal`\
在有效`VARIANT`的指標，其中包含要寫入的限定詞。 這個參數不可以是 `null`。

`lFlavor`\
在下列其中一個常數，定義此辨識符號的所需限定詞類別。 預設值為`WBEM_FLAVOR_OVERRIDABLE` （0）。

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | 限定詞可以在衍生類別或實例中覆寫。 **這是預設值。** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | 限定詞會傳播到執行個體。 |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | 限定詞會傳播到衍生類別。 |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | 無法在衍生類別或執行個體中覆寫限定詞。 |
| `WBEM_FLAVOR_AMENDED` | 0x80 | 辨識符號已當地語系化。 |

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | 在無法做為索引鍵的屬性上，指定索引**鍵**辨識符號的嘗試不合法。 索引鍵是在物件的類別定義中指定，而且無法針對每個實例進行變更。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數無效。 |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal`參數不是合法的限定詞類型。 |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | 因為主控物件不允許覆寫`QualifierSet_Put` ，所以無法在辨識符號上呼叫方法。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝對[IWbemQualifierSet：:P](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put)的工作方法的呼叫。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
