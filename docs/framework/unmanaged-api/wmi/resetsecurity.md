---
title: 重置安全功能（非託管 API 引用）
description: 重置安全功能將類比權杖分配給當前執行緒。
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
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174858"
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
[在]要與當前執行緒關聯的類比權杖。 其值可以是 `null`。

## <a name="return-value"></a>傳回值

如果函數成功，則傳回值為`S_OK`（0）。

如果函數失敗，傳回值是非零錯誤代碼。 要獲取擴展的錯誤資訊，請致電[GetErrorInfo](geterrorinfo.md)函數。
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標題：** WMINet_Utils.idl  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
