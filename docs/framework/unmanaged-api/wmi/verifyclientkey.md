---
title: 'VerifyClientKey 函式 (非受控 API 參考) '
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
ms.openlocfilehash: 26cffe9936f2e01078b6f54e8499b58519f1018e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729417"
---
# <a name="verifyclientkey-function"></a>VerifyClientKey 函式

確定用戶端金鑰有正確的安全性。  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為 `ERROR_SUCCESS` (0) 。

如果函式失敗，則傳回值會在 *winerror.h* 中定義為非零的錯誤碼。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils .def  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 與效能計數器 (非受控 API 參考)](index.md)
