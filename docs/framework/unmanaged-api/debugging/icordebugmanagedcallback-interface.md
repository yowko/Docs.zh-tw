---
title: "ICorDebugManagedCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback
helpviewer_keywords: ICorDebugManagedCallback interface [.NET Framework debugging]
ms.assetid: b47f1d61-c7dc-4196-b926-0b08c94f7041
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fd864cbb5a95143f6dd7f55fc1b1fc57f9f42e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback 介面
提供方法來處理偵錯工具回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Break 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|告知偵錯工具時<xref:System.Reflection.Emit.OpCodes.Break>執行指令碼資料流中的。|  
|[Breakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|遇到中斷點時，請告知偵錯工具。|  
|[BreakpointSetError 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|Common language runtime (CLR) 無法正確地繫結在 just-in-time (JIT) 編譯函式之前已設定的中斷點會告知偵錯工具。|  
|[ControlCTrap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|CTRL + C 陷入正在偵錯的程序會告知偵錯工具。|  
|[CreateAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|告知偵錯工具已建立應用程式定義域。|  
|[CreateProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|當處理程序已附加或第一次啟動時，請告知偵錯工具。|  
|[CreateThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|執行緒已開始執行 managed 程式碼會告知偵錯工具。|  
|[DebuggerError 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|告知偵錯工具，在嘗試處理從 CLR 事件已發生錯誤。|  
|[EditAndContinueRemap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|已取代。 重新對應事件已傳送至 IDE 會告知偵錯工具。|  
|[EvalComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|告知偵錯工具評估已完成。|  
|[EvalException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|告知偵錯工具，並發生未處理的例外狀況結束評估。|  
|[Exception 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|例外狀況已擲回從 managed 程式碼會告知偵錯工具。|  
|[ExitAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|告知偵錯工具應用程式定義域已結束。|  
|[ExitProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|告知偵錯工具的處理序已經結束。|  
|[ExitThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|告知偵錯工具正在執行 managed 程式碼的執行緒已結束。|  
|[LoadAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|已成功載入 CLR 組件會告知偵錯工具。|  
|[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|告知偵錯工具已載入類別。|  
|[LoadModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|已成功載入 CLR 模組會告知偵錯工具。|  
|[LogMessage 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|CLR managed 執行緒已呼叫方法，偵錯工具會通知<xref:System.Diagnostics.EventLog>記錄事件的類別。|  
|[LogSwitch 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|CLR managed 執行緒已呼叫方法，偵錯工具會通知<xref:System.Diagnostics.Switch>類別來建立、 修改或刪除偵錯/追蹤參數。|  
|[NameChange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|告知偵錯工具應用程式定義域或執行緒的名稱已變更。|  
|[StepComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|告知偵錯工具已完成步驟。|  
|[UnloadAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|告知偵錯工具的 CLR 組件已卸載。|  
|[UnloadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|表示正在卸載的類別會告知偵錯工具。|  
|[UnloadModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|告知偵錯工具為 CLR 模組 (DLL)，已卸載。|  
|[UpdateModuleSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|告知偵錯工具，已變更為 CLR 模組的符號。|  
  
## <a name="remarks"></a>備註  
 序列化，相同的執行緒中呼叫和以同步處理的狀態中的程序呼叫所有的回呼。  
  
 每個回呼實作必須呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)繼續執行。 如果`ICorDebugController::Continue`不之前呼叫在回呼傳回、 處理程序將保持停止並沒有更多的事件回呼將會發生，直到`ICorDebugController::Continue`呼叫。  
  
 偵錯工具必須實作[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)如果它.NET Framework 2.0 版的應用程式進行偵錯。 執行個體`ICorDebugManagedCallback`或`ICorDebugManagedCallback2`為回呼物件，以傳遞[icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
>  這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
