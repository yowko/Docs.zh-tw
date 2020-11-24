---
title: ICorDebugManagedCallback 介面
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback
helpviewer_keywords:
- ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type:
- apiref
ms.openlocfilehash: 6eebabc3a08027eab4ac55c1e46dd75b1f75bd21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679698"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback 介面

提供方法來處理偵錯工具回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Break 方法](icordebugmanagedcallback-break-method.md)|當 <xref:System.Reflection.Emit.OpCodes.Break> 執行程式碼資料流程中的指令時，通知偵錯工具。|  
|[Breakpoint 方法](icordebugmanagedcallback-breakpoint-method.md)|在遇到中斷點時通知偵錯工具。|  
|[BreakpointSetError 方法](icordebugmanagedcallback-breakpointseterror-method.md)|通知偵錯工具，common language runtime (CLR) 無法精確地系結在函式 (JIT) 編譯之前所設定的中斷點。|  
|[ControlCTrap 方法](icordebugmanagedcallback-controlctrap-method.md)|通知偵錯工具，在要進行調試的進程中攔截 CTRL + C。|  
|[CreateAppDomain 方法](icordebugmanagedcallback-createappdomain-method.md)|通知偵錯工具已建立應用程式域。|  
|[CreateProcess 方法](icordebugmanagedcallback-createprocess-method.md)|第一次附加或啟動處理常式時，通知偵錯工具。|  
|[CreateThread 方法](icordebugmanagedcallback-createthread-method.md)|通知偵錯工具執行緒已開始執行 managed 程式碼。|  
|[DebuggerError 方法](icordebugmanagedcallback-debuggererror-method.md)|通知偵錯工具在嘗試處理來自 CLR 的事件時發生錯誤。|  
|[EditAndContinueRemap 方法](icordebugmanagedcallback-editandcontinueremap-method.md)|已取代。 通知偵錯工具，重新對應事件已傳送至 IDE。|  
|[EvalComplete 方法](icordebugmanagedcallback-evalcomplete-method.md)|通知偵錯工具已完成評估。|  
|[EvalException 方法](icordebugmanagedcallback-evalexception-method.md)|通知偵錯工具已終止評估，但有未處理的例外狀況。|  
|[Exception 方法](icordebugmanagedcallback-exception-method.md)|通知偵錯工具已從 managed 程式碼擲回例外狀況。|  
|[ExitAppDomain 方法](icordebugmanagedcallback-exitappdomain-method.md)|通知偵錯工具，應用程式域已結束。|  
|[ExitProcess 方法](icordebugmanagedcallback-exitprocess-method.md)|通知偵錯工具已結束。|  
|[ExitThread 方法](icordebugmanagedcallback-exitthread-method.md)|通知偵錯工具，已結束執行 managed 程式碼的執行緒。|  
|[LoadAssembly 方法](icordebugmanagedcallback-loadassembly-method.md)|通知偵錯工具已順利載入 CLR 元件。|  
|[LoadClass 方法](icordebugmanagedcallback-loadclass-method.md)|通知偵錯工具已載入某個類別。|  
|[LoadModule 方法](icordebugmanagedcallback-loadmodule-method.md)|通知偵錯工具已順利載入 CLR 模組。|  
|[LogMessage 方法](icordebugmanagedcallback-logmessage-method.md)|通知偵錯工具，CLR managed 執行緒已在類別中呼叫方法 <xref:System.Diagnostics.EventLog> 來記錄事件。|  
|[LogSwitch 方法](icordebugmanagedcallback-logswitch-method.md)|通知偵錯工具，CLR managed 執行緒已呼叫類別中的方法， <xref:System.Diagnostics.Switch> 以建立、修改或刪除偵錯工具/追蹤參數。|  
|[NameChange 方法](icordebugmanagedcallback-namechange-method.md)|通知偵錯工具，應用程式域或執行緒的名稱已變更。|  
|[StepComplete 方法](icordebugmanagedcallback-stepcomplete-method.md)|通知偵錯工具已完成步驟。|  
|[UnloadAssembly 方法](icordebugmanagedcallback-unloadassembly-method.md)|通知偵錯工具已卸載 CLR 元件。|  
|[UnloadClass 方法](icordebugmanagedcallback-unloadclass-method.md)|通知偵錯工具正在卸載某個類別。|  
|[UnloadModule 方法](icordebugmanagedcallback-unloadmodule-method.md)|通知偵錯工具，CLR 模組 (DLL) 已卸載。|  
|[UpdateModuleSymbols 方法](icordebugmanagedcallback-updatemodulesymbols-method.md)|通知偵錯工具，CLR 模組的符號已變更。|  
  
## <a name="remarks"></a>備註  

 所有回呼都會序列化，並在相同的執行緒中呼叫，並以已同步處理狀態的進程呼叫。  
  
 每個回呼執行都必須呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 以繼續執行。 如果在 `ICorDebugController::Continue` 回呼傳回之前未呼叫，進程將維持停止，而且在呼叫之前，不會再發生任何事件回呼 `ICorDebugController::Continue` 。  
  
 如果偵錯工具正在 .NET Framework 2.0 版應用程式進行偵錯工具，則必須執行 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 。 或的實例 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` 會以回呼物件的形式傳遞至 [ICorDebug：： SetManagedHandler](icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](icordebug-interface.md)
- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [偵錯介面](debugging-interfaces.md)
