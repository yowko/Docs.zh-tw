---
title: ICorDebugUnmanagedCallback::DebugEvent 方法
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ec45004f5dd87983187690a0a4feefb35b05e85
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183608"
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
  
## <a name="parameters"></a>參數  
 `pDebugEvent`  
 [in]原生的事件指標。  
  
 `fOutOfBand`  
 [in]`true`，如果 managed 處理序狀態的互動是不可能在未受管理的事件發生，直到偵錯工具呼叫後[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); 否則`false`。  
  
## <a name="remarks"></a>備註  
 如果正在偵錯的執行緒是 Win32 執行緒，請勿使用任何成員的 Win32 偵錯介面。 您可以呼叫`ICorDebugController::Continue`只有在 Win32 執行緒和過去的頻外事件繼續時，才。  
  
 `DebugEvent`回呼不會遵循標準的規則，以便回呼。 當您呼叫`DebugEvent`、 程序會在未經處理、 OS 偵錯已停止 」 狀態。 將不會同步處理程序。 它會自動進入已同步處理的狀態時所需滿足的 managed 程式碼，可能會導致其他巢狀的相關資訊要求`DebugEvent`回呼。  
  
 呼叫[icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)上忽略例外狀況事件，然後再繼續此程序的程序。 呼叫這個方法將繼續要求，而不是 DBG_EXCEPTION_NOT_HANDLED DBG_CONTINUE，並會自動清除 頻外中斷點和逐步執行例外狀況。 頻外事件都在任何時間，，和正在偵錯應用程式會顯示已停止時，即使當未處理的頻內事件已經存在。  
  
 在.NET Framework 2.0 版中，偵錯工具立即應超出的中斷點事件之後繼續執行。 應該使用偵錯工具[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)並[ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)新增及移除中斷點的方法。 這些方法會自動略過任何超出的中斷點。 因此，分派只頻中斷點應已處於指令資料流，例如呼叫 Win32 的未經處理中斷點`DebugBreak`函式。 請勿嘗試使用`ICorDebugProcess::ClearCurrentException`， [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)， [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)，或任何其他成員[偵錯 API](../../../../docs/framework/unmanaged-api/debugging/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugUnmanagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
