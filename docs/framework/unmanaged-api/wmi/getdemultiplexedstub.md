---
title: GetDemultiplexedStub 函式（非受控 API 參考）
description: GetDemultiplexedStub 函式會建立物件轉寄站接收，以協助用戶端接收來自 Windows 管理的非同步呼叫。
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2d3885a4a9e54950909053ba18de5b1891e7edf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798605"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 函式
建立物件轉寄站接收以協助用戶端從 Windows Management 接收非同步呼叫。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>參數

`pObject`  
在[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)的用戶端同進程執行的指標。

`isLocal`  
在指出事件是否為本機（`true`）的旗標， `false`否則為。

`ppObject`  
脫銷物件轉寄站接收，可協助用戶端接收來自 Windows 管理的非同步呼叫。

## <a name="return-value"></a>傳回值

如果函式成功，則傳回值為`S_OK` （0）。

如果函式失敗，則傳回值為非零的錯誤碼。 若要取得擴充的錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。
    
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱

- [WMI 和效能計數器（非受控 API 參考）](index.md)
