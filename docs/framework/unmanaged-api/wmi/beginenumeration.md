---
title: "BeginEnumeration 函式 （Unmanaged API 參考）"
description: "BeginEnumeration 函式會列舉值重設為開頭的列舉型別"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: BeginEnumeration
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: BeginEnumeration
helpviewer_keywords: BeginEnumeration function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12a742774bff22030bdfaaa34e431059e016a4bf
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
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
[in]未使用這個參數。

`ptr`[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`lEnumFlags`  
[in]旗標或描述中值的位元組合[備註](#remarks)控制屬性包含在列舉中的區段。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 中的旗標的組合`lEnumFlags`無效，或是無效的引數所指定。 |
|`WBEM_E_UNEXPECTED` | 0x8004101d | 第二個呼叫`BeginEnumeration`所沒有的中間呼叫[ `EndEnumeration` ](endenumeration.md)。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 使用開始新的列舉型別沒有足夠的記憶體。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::BeginEnumeration](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)方法。

可以做為傳遞的旗標`lEnumFlags`引數中所定義*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中。  您可以結合任何旗標，任何其他群組的每個群組從一個旗標。 不過，從相同群組的旗標互斥。 

**群組 1**

|常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | 包含構成只在索引鍵屬性。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 包含僅限物件參考的內容。 |

**群組 2**

常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | 限制只系統屬性的列舉型別。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 包含本機和傳播屬性，但排除在列舉中的系統屬性。 |

針對類別：

常數  |值  |說明  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | 0x100 | 限制覆寫類別定義中的屬性的列舉型別。 |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | 0x100 | 限制覆寫目前的類別定義中的屬性並定義於類別的新屬性的列舉型別。 |
| `WBEM_MASK_CLASS_CONDITION` | 0x300 | 遮罩 （而不是一個旗標），套用對`lEnumFlags`值來檢查是否有任一個`WBEM_FLAG_CLASS_OVERRIDES_ONLY`或`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES`設定。 |
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 限制屬性所定義或修改此類別本身中的列舉型別。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 限制的列舉型別都繼承自基底類別的屬性。 |

執行個體：

常數  |值  |說明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 限制屬性所定義或修改此類別本身中的列舉型別。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 限制的列舉型別都繼承自基底類別的屬性。 |


## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
