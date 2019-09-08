---
title: ResetSecurity 函式（非受控 API 參考）
description: ResetSecurity 函數會將模擬 token 指派給目前的執行緒。
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
ms.openlocfilehash: 1636d7de8273389e785131dbc1145affd5d3b45f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798250"
---
# <a name="resetsecurity-function"></a>ResetSecurity 函式
將提供的模擬權杖指派給目前的執行緒。   
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
); 
```  

## <a name="parameters"></a>參數

`token`  
在要與目前線程產生關聯的模擬權杖。 其值可以是 `null`。 

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為`S_OK` （0）。

如果函式失敗，則傳回值為非零的錯誤碼。 若要取得擴充的錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
