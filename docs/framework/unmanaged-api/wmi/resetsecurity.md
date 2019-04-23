---
title: ResetSecurity 函式 （Unmanaged API 參考）
description: ResetSecurity 函式會指派給目前執行緒的模擬語彙基元。
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e937690c184d810549e8ab11ef1fc2273a45c5f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115124"
---
# <a name="resetsecurity-function"></a>ResetSecurity 函式
將提供的模擬權杖指派給目前的執行緒。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>參數

`token`  
[in]要與目前的執行緒產生關聯的模擬權杖。 其值可以是 `null`。 

## <a name="return-value"></a>傳回值

如果此函數成功，傳回的值是`S_OK`(0)。

如果函式失敗，傳回的值就會為非零的錯誤碼。 若要取得延伸錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器 （Unmanaged API 參考）](index.md)
