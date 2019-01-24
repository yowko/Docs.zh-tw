---
title: BeginEnumeration 函式 （Unmanaged API 參考）
description: BeginEnumeration 函式會查看的列舉值重設為列舉的開頭
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
ms.openlocfilehash: 65e1ed604084fa61c8e47f0bb468b6a6d100778c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695721"
---
# <a name="beginenumeration-function"></a>BeginEnumeration 函式
將列舉值重設回列舉的開頭。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BeginEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用此參數。

`ptr` [in]指標[IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)執行個體。

`lEnumFlags`  
[in]中所述的旗標的位元組合[備註](#remarks)控制包含在列舉中的屬性的區段。

## <a name="return-value"></a>傳回值

此函式所傳回的下列值中定義*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 中的旗標的組合`lEnumFlags`無效，或是無效的引數所指定。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二次呼叫`BeginEnumeration`而不需要的介入呼叫進行[ `EndEnumeration` ](endenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可供開始新的列舉型別。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝在呼叫[IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)方法。

可以做為傳遞的旗標`lEnumFlags`中所定義的引數*WbemCli.h*標頭檔，或者您可以將其定義為常數中程式碼。  您可以結合任何其他群組的任何旗標的每個群組中的一個旗標。 不過，從相同的群組的旗標是互斥的。 

**群組 1**

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 包含構成只在索引鍵的屬性。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 包含僅限物件參考的屬性。 |

**群組 2**

常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 限制僅限系統屬性的列舉型別。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 包含本機和傳播屬性，但排除列舉中的系統屬性。 |

針對類別：

常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | 限制覆寫在類別定義中的屬性的列舉型別。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 限制覆寫目前的類別定義中的屬性並在類別中定義的新屬性的列舉型別。 |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | 遮罩 （而不是一個旗標），若要針對套用`lEnumFlags`值來檢查是否有任一`WBEM_FLAG_CLASS_OVERRIDES_ONLY`或`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`設定。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 限制屬性所定義或修改在類別本身的列舉型別。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 限制列舉型別繼承自基底類別的屬性。 |

執行個體：

常數  |值  |描述  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 限制屬性所定義或修改在類別本身的列舉型別。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 限制列舉型別繼承自基底類別的屬性。 |


## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱
- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
