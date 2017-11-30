---
title: "GetDemultiplexedStub 函式 （Unmanaged API 參考）"
description: "GetDemultiplexedStub 函式會建立物件轉寄站接收可協助用戶端從 Windows 管理接收非同步呼叫。"
ms.date: 11/06/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: reference
api_name: GetDemultiplexedStub
api_location: WMINet_Utils.dll
api_type: DLLExport
f1_keywords: GetDemultiplexedStub
helpviewer_keywords: GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type: Reference
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a81101acbf65546ea068e6b5a0e8d9045aaadc71
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/15/2017
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 函式
建立物件轉寄站接收可協助用戶端從 Windows 管理接收非同步呼叫。
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a>參數

`pObject`  
[in]用戶端的程序中實作的指標[IWbemObjectSink](https://msdn.microsoft.com/en-us/library/aa391787(v=vs.85).aspx)。

`isLocal`  
[in]指出事件是否位於本機的旗標 (`true`)，否則`false`。

`ppObject`  
[out]若要協助用戶端從 Windows 管理接收非同步呼叫物件轉寄站接收。

## <a name="return-value"></a>傳回值

如果函式成功，傳回值是`S_OK`(0)。

如果函式失敗，傳回的值就會為非零的錯誤碼。 若要取得延伸錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。
    
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
