---
title: GetDemultiplexedStub 函式 （Unmanaged API 參考）
description: GetDemultiplexedStub 函式會建立物件轉寄站接收器，以協助用戶端接收 Windows 管理中的非同步呼叫。
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
ms.openlocfilehash: 4311a77c9159428bf7beacc99d4479acb28b91b6
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135805"
---
# <a name="getdemultiplexedstub-function"></a>GetDemultiplexedStub 函式
建立物件轉寄站接收以協助用戶端從 Windows Management 接收非同步呼叫。
  
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
[in]用戶端的程序中實作的指標[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)。

`isLocal`  
[in]指出事件是否位於本機的旗標 (`true`)，否則`false`。

`ppObject`  
[out]若要協助用戶端接收非同步呼叫，從 Windows 管理物件轉寄站接收。

## <a name="return-value"></a>傳回值

如果此函數成功，傳回的值是`S_OK`(0)。

如果函式失敗，傳回的值就會為非零的錯誤碼。 若要取得延伸錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。
    
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** WMINet_Utils.idl  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>另請參閱  
[WMI 和效能計數器 （Unmanaged API 參考）](index.md)
