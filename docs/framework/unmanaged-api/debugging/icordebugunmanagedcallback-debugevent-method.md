---
title: "ICorDebugUnmanagedCallback::DebugEvent 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugUnmanagedCallback.DebugEvent
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49c3386fcda0bc731935ec9db7d029d0e619ef14
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent 方法
原生事件已引發會通知偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pDebugEvent`  
 [in]原生事件指標。  
  
 `fOutOfBand`  
 [in]`true`，如果不可能與受管理的處理序狀態的互動是直到偵錯工具呼叫 unmanaged 的事件發生後[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)，否則`false`。  
  
## <a name="remarks"></a>備註  
 如果正在偵錯執行緒的 Win32 執行緒，請勿使用任何成員 Win32 偵錯介面。 您可以呼叫`ICorDebugController::Continue`只有 Win32 執行緒和過去的頻外事件繼續時，才。  
  
 `DebugEvent`回呼未遵循標準的規則，以便回呼。 當您呼叫`DebugEvent`、 處理程序會在未經處理、 OS 偵錯已停止 」 狀態。 將不會同步處理程序。 它會自動進入已同步處理的狀態時所需滿足之 managed 程式碼，可能會導致巢狀其他資訊的要求`DebugEvent`回呼。  
  
 呼叫[icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)忽略例外狀況事件，然後再繼續此程序的程序。 呼叫這個方法會傳送繼續要求，而不是 DBG_EXCEPTION_NOT_HANDLED DBG_CONTINUE，並會自動清除 超出訊號範圍中斷點和逐步執行例外狀況。 超出訊號範圍事件都在任何時候，，和進行偵錯應用程式會出現停止時，即使當未處理的頻外事件已經存在。  
  
 在.NET Framework 2.0 版中，偵錯工具立即應該的頻外中斷點事件之後繼續執行。 應該使用偵錯工具[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)和[icordebugprocess2:: Clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)新增和移除中斷點的方法。 這些方法會自動略過任何超出訊號範圍的中斷點。 因此，分派只 out-of-band 中斷點應該是未經處理已經存在於指令資料流，例如 Win32 呼叫中的中斷點`DebugBreak`函式。 請勿嘗試使用`ICorDebugProcess::ClearCurrentException`， [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)， [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)，或任何其他成員的[偵錯 API](../../../../docs/framework/unmanaged-api/debugging/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebugUnmanagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
