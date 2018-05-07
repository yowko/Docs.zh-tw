---
title: VerifyClientKey 函式 （Unmanaged API 參考）
description: VerifyClientKey 函式可確保用戶端金鑰具有正確的安全性。
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea8a74633d3e950f6cf7ba87c00a9efa45206545
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="verifyclientkey-function"></a>VerifyClientKey 函式
可確保用戶端金鑰具有正確的安全性。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a>傳回值

如果函式成功，傳回值是`ERROR_SUCCESS`(0)。

如果函式失敗，傳回值是中定義的非零的錯誤代碼*WinError.h*。

## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.def  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
