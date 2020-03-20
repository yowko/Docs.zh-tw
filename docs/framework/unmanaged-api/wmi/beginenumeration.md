---
title: 開始枚舉函數（非託管 API 引用）
description: BeginEe枚舉函數將枚舉器重置為枚舉的開頭
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176873"
---
# <a name="beginenumeration-function"></a>BeginEnumeration 函式
將枚舉器重置回枚舉的開頭。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a>參數

`vFunc`\
[在]此參數未使用。

`ptr`\
[在]指向[IWbem ClassObject 實例](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)的指標。

`lEnumFlags`\
[在]控制枚舉中包含的屬性的[備註](#remarks)部分中描述的標誌或值的位組合。

## <a name="return-value"></a>傳回值

此函數返回的以下值在*WbemCli.h*標標頭檔中定義，或者您可以在代碼中將它們定義為常量：

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 中`lEnumFlags`的標誌組合無效，或指定了不正確參數。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`BeginEnumeration`是在沒有干預調用[`EndEnumeration`](endenumeration.md)的情況下進行的。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可用於開始新的枚舉。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函數包裝對[IWbemClassObject 的調用：：開始枚舉](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法。

可在`lEnumFlags`*WbemCli.h*標標頭檔中定義作為參數傳遞的標誌，也可以將它們定義為代碼中的常量。  您可以將每個組中的一個標誌與任何其他組的任何標誌合併。 但是，來自同一組的標誌是互斥的。

**組 1**

|持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 僅包含構成金鑰的屬性。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 僅包含物件引用的屬性。 |

**組 2**

持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 僅將枚舉限制為系統屬性。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 包括本地和傳播屬性，但從枚舉中排除系統屬性。 |

對於類：

持續性  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | 將枚舉限制為類定義中重寫的屬性。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 將枚舉限制為當前類定義中重寫的屬性和類中定義的新屬性。 |
| `WBEM_MASK_CLASS_CONDITION` | 0 x 300 | 要針對`lEnumFlags`值應用的蒙版（而不是標誌），以檢查是否設置了。 `WBEM_FLAG_CLASS_OVERRIDES_ONLY` `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 將枚舉限制為在類本身中定義或修改的屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 將枚舉限制為從基類繼承的屬性。 |

例如：

持續性  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 將枚舉限制為在類本身中定義或修改的屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 將枚舉限制為從基類繼承的屬性。 |

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
