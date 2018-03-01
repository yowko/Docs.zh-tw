---
title: "QualifierSet_Delete 函式 （Unmanaged API 參考）"
description: "QualifierSet_Delete 函式會依名稱刪除限定詞。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4e7b5650a0b47fd8d9b64bb9d0fff3511afe2d43
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="qualifiersetdelete-function"></a>QualifierSet_Delete 函式
依名稱刪除指定的限定詞。  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`   
[in]指標[IWbemQualifierSet](https://msdn.microsoft.com/library/aa391860(v=vs.85).aspx)執行個體。

`wszName`   
[in]若要刪除限定詞的名稱。

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | `wszName`參數無效。 |
|`WBEM_E_INVALID_OPERATION` | 0x80041016 | 刪除這個限定詞是不合法的。 |
|`WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 找不到指定的限定詞。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
| `WBEM_S_RESET_TO_DEFAULT` | 0x40002 | 本機覆寫已刪除，並從父物件的原始限定詞已恢復範圍。 |

## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemQualifierSet::Delete](https://msdn.microsoft.com/library/aa391864(v=vs.85).aspx)方法。

限定詞傳播規則，因為特定的辨識符號可能已從另一個物件繼承和只是覆寫目前的類別或執行個體中。 在此情況下，`QualifierSet_Delete`方法重設這個限定詞繼承其原始值。 函式在此情況下會傳回狀態碼`WBEM_S_RESET_TO_DEFAULT`。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
