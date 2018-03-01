---
title: "GetMethod 函式 （Unmanaged API 參考）"
description: "GetMethod 函式會擷取方法的相關資訊。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: reference
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f22a2dfa7aae411cac960cbad2017718df8057e1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="getmethod-function"></a>GetMethod 函式
擷取指定之方法的相關資訊。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>語法  
  
```  
HRESULT GetMethod (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
); 
```  

## <a name="parameters"></a>參數

`vFunc`  
[in]未使用這個參數。

`ptr`  
[in]指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)執行個體。

`wszName`  
[in]方法名稱。 此參數不得為`null`且必須指向有效`LPCWSTR`。

`lFlags`  
[in]保留。 這個參數必須是 0。

`ppInSignature`   
[out]位址指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)描述中的 paramteers 方法的執行個體。 這個參數已忽略，如果設定為`null`。 

`ppOutSignature`  
[out]位址指標[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)描述方法的 out 參數的執行個體。 這個參數已忽略，如果設定為`null`。 

## <a name="return-value"></a>傳回值

這個函式傳回下列值會定義在*WbemCli.h*標頭檔，或者您可以定義它們以常數的形式在程式碼中：

|常數  |值  |描述  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | 而會收到 0x80041002 | 找不到指定的屬性。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 沒有足夠的記憶體可完成作業。 |
|`WBEM_S_NO_ERROR` | 0 | 函式呼叫成功。  |
  
## <a name="remarks"></a>備註

此函式會包裝呼叫[IWbemClassObject::GetMethod](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)方法。

可以設定 Windows 管理[IWbemClassObject](https://msdn.microsoft.com/library/aa391433%28v=vs.85%29.aspx)指標`null`如果方法沒有任何 in 參數。

在`ppInSignature`和`ppOutSignature`分別中的屬性描述輸入和輸出參數，`IWbemClassObject`系統類別的執行個體[_Parameters](https://msdn.microsoft.com/library/aa394667(v=vs.85).aspx)。 中的屬性`ppInsignature`命名**Param***n*，其中 *n* 時 （例如方法簽章中參數的位置做為`Param1`，`Param2`等。)。 中的屬性`ppOutSignature`也稱為**Param***n*，傳回的值稱為**ReturnValue**。 如需詳細資訊和範例，請參閱[IWbemClassObject::GetMethod 方法](https://msdn.microsoft.com/library/aa391443(v=vs.85).aspx)。

## <a name="requirements"></a>需求  
**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
