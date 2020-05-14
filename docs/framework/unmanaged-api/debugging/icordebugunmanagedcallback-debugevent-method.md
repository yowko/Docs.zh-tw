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
ms.openlocfilehash: 24c316ea6bab11fb55e8e0fc1dc9832a312dbc6a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397186"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a>ICorDebugUnmanagedCallback::DebugEvent 方法
通知偵錯工具已引發原生事件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a>參數  
 `pDebugEvent`  
 在原生事件的指標。  
  
 `fOutOfBand`  
 [in] `true` ，如果未受管理的事件發生，就無法與 managed 進程狀態互動，直到偵錯工具呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)為止; 否則為 `false` 。  
  
## <a name="remarks"></a>備註  
 如果正在進行調試的執行緒是 Win32 執行緒，請勿使用 Win32 調試介面的任何成員。 您只能 `ICorDebugController::Continue` 在 Win32 執行緒上呼叫，而且只有在繼續執行超出範圍外事件時。  
  
 `DebugEvent`回呼不會遵循回呼的標準規則。 當您呼叫時 `DebugEvent` ，進程將會處於原始的 OS-debug 停止狀態。 此程式將不會同步處理。 它會在必要時自動進入已同步處理的狀態，以滿足 managed 程式碼之資訊的要求，而這可能會導致其他的嵌套 `DebugEvent` 回呼。  
  
 在進程上呼叫[ICorDebugProcess：： ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) ，以忽略例外狀況事件，然後再繼續處理常式。 呼叫這個方法會傳送 DBG_CONTINUE，而不是在 CONTINUE 要求上 DBG_EXCEPTION_NOT_HANDLED，並會自動清除頻外中斷點和單步驟例外狀況。 即使正在進行調試的應用程式顯示為已停止，以及已有未處理的內建事件，也可能隨時都有頻外事件。  
  
 在 .NET Framework 版本2.0 中，偵錯工具應該立即繼續執行超出範圍外的中斷點事件。 偵錯工具應該使用[ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)和[ICorDebugProcess2：： ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md)方法來新增和移除中斷點。 這些方法會自動略過任何頻外中斷點。 因此，唯一分派的頻外中斷點應該是已在指令資料流程中的原始中斷點，例如對 Win32 函數的呼叫 `DebugBreak` 。 請勿嘗試使用 `ICorDebugProcess::ClearCurrentException` 、 [ICorDebugProcess：： GetThreadCoNtext](icordebugprocess-getthreadcontext-method.md)、 [ICorDebugProcess：： SetThreadCoNtext](icordebugprocess-setthreadcontext-method.md)，或任何其他的[調試 API](index.md)成員。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugUnmanagedCallback 介面](icordebugunmanagedcallback-interface.md)
