---
title: BeginEnumeration 函式（非受控 API 參考）
description: BeginEnumeration 函數會將枚舉器重設為列舉的開頭
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de36650aa2b206b5e9734b38c6067a3a79de610c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798788"
---
# <a name="beginenumeration-function"></a>BeginEnumeration 函式
將列舉值重設回列舉的開頭。  

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
在未使用此參數。

`ptr`\
在[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)實例的指標。

`lEnumFlags`\
在在 [[備註](#remarks)] 區段中所描述的旗標或值的位元組合，可控制列舉中包含的屬性。

## <a name="return-value"></a>傳回值

這個函式所傳回的下列值會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 中`lEnumFlags`的旗標組合無效，或指定了不正確引數。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`BeginEnumeration`時，不需要介入的[`EndEnumeration`](endenumeration.md)呼叫。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可以開始新的列舉。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝對[IWbemClassObject：： BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法的呼叫。

可當做`lEnumFlags`引數傳遞的旗標會定義在*WbemCli*標頭檔中，您也可以在程式碼中將它們定義為常數。  您可以將每個群組中的一個旗標與任何其他群組中的任何旗標結合。 不過，來自相同群組的旗標是互斥的。 

**群組1**

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 包含僅構成金鑰的屬性。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 包含僅為物件參考的屬性。 |

**群組2**

常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 僅將列舉限制為系統屬性。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 包含本機和傳播的屬性，但從列舉中排除系統屬性。 |

針對類別：

常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | 將列舉限制為在類別定義中覆寫的屬性。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 將列舉限制為在目前類別定義中覆寫的屬性，以及加入至類別中定義的新屬性。 |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | 要對`lEnumFlags`值套用的遮罩（而不是旗標），以檢查`WBEM_FLAG_CLASS_OVERRIDES_ONLY`是否已`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`設定或。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 將列舉限制為在類別本身中定義或修改的屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 將列舉限制為繼承自基類的屬性。 |

針對實例：

常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 將列舉限制為在類別本身中定義或修改的屬性。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 將列舉限制為繼承自基類的屬性。 |

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
