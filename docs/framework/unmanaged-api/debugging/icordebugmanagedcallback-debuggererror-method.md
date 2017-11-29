---
title: "ICorDebugManagedCallback::DebuggerError 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.DebuggerError
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::DebuggerError
helpviewer_keywords:
- DebuggerError method [.NET Framework debugging]
- ICorDebugManagedCallback::DebuggerError method [.NET Framework debugging]
ms.assetid: 9e983d11-eaf3-4741-b936-29ec456384a3
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c4eb16762d2a0db01c3cc921712a89995e0c87c0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmanagedcallbackdebuggererror-method"></a>ICorDebugManagedCallback::DebuggerError 方法
告知偵錯工具嘗試處理從 common language runtime (CLR) 事件時，已發生錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DebuggerError (  
    [in] ICorDebugProcess *pProcess,  
    [in] HRESULT           errorHR,  
    [in] DWORD             errorCode  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pProcess`  
 [in]代表發生事件的程序 」 ICorDebugProcess 」 物件的指標。  
  
 `errorHR`  
 [in]從事件處理常式傳回的 HRESULT 值。  
  
 `errorCode`  
 [in]指定 CLR 錯誤的整數。  
  
## <a name="remarks"></a>備註  
 處理程序可能會放置於傳遞模式，視錯誤的本質而定。  
  
 `DebugError`回呼表示，偵錯服務已停用由於發生錯誤，因此偵錯工具應該提供錯誤訊息給使用者。 [Icordebugprocess:: Getid](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)會安全地呼叫，但所有其他方法，包括[icordebug:: Terminate](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)，不應呼叫。 偵錯工具應該使用作業系統的功能，來結束處理序。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
