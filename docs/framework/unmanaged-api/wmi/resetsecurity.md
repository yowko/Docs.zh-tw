---
title: "ResetSecurity 函式 （Unmanaged API 參考）"
description: "ResetSecurity 函式會模擬語彙基元指派給目前的執行緒。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: ResetSecurity
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: ResetSecurity
helpviewer_keywords: ResetSecurity function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bacee65633d25e705d978d3902a6804516a88bf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="resetsecurity-function"></a>ResetSecurity 函式
將提供的模擬語彙基元指派給目前的執行緒。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>參數

`token`  
[in]與目前執行緒相關聯的模擬權杖。 其值可以是 `null`。 

## <a name="return-value"></a>傳回值

如果函式成功，傳回值是`S_OK`(0)。

如果函式失敗，傳回的值就會為非零的錯誤碼。 若要取得延伸錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
