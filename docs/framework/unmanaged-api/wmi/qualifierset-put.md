---
title: QualifierSet_Put 函式 （Unmanaged API 參考）
description: QualifierSet_Put 函式會寫入具名的辨識符號和其值。
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
ms.openlocfilehash: 0e42cf3440bef030f5c7bec71ed1b4b875b79a61
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000268"
---
# <a name="qualifiersetput-function"></a>QualifierSet_Put 函式

寫入具名限定詞與值。 新限定詞會覆寫先前的相同名稱的值。 如果不存在的辨識符號，它會建立它。

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
[in]未使用此參數。

`ptr`\
[in]指標[IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)執行個體。

`wszName`\
[in]要寫入的限定詞名稱。

`pVal`\
[in]有效的指標`VARIANT`，其中包含要寫入的限定詞。 這個參數不可以是 `null`。

`lFlavor`\
[in]其中一個的所需的限定詞標註，這個辨識符號會定義下列常數。 預設值是`WBEM_FLAVOR_OVERRIDABLE`(0)。

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | 0 | 限定詞可以覆寫於衍生的類別或執行個體。 **這是預設值。** |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | 1 | 限定詞會傳播到執行個體。 |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | 2 | 限定詞會傳播到衍生類別中。 |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | 0x10 | 無法在衍生類別或執行個體中覆寫限定詞。 |
| `WBEM_FLAVOR_AMENDED` | 0x80 | 限定詞會進行當地語系化。 |

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | 0x8004101f | 發生不合法嘗試指定**金鑰**不得為索引鍵屬性上的限定詞。 指定索引鍵 om c; as 物件的定義，無法變更每個執行個體為基礎。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | 參數不是有效的。 |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | 0x80041029 | `pVal`參數不是合法的限定詞型別。 |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | 0x8004101a | 不可能呼叫`QualifierSet_Put`方法在限定詞上的因為主控物件不允許覆寫。 |
| `WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |

## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put)方法。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** WMINet_Utils.idl

**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)