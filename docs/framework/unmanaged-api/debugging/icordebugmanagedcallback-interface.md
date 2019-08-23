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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25e40103a2925cbd2a181b8e39c3873e4d7c842c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940051"
---
# <a name="icordebugmanagedcallback-interface"></a>ICorDebugManagedCallback 介面
提供方法來處理偵錯工具回呼。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[Break 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|執行程式碼資料流程中<xref:System.Reflection.Emit.OpCodes.Break>的指令時, 通知偵錯工具。|  
|[Breakpoint 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|遇到中斷點時, 通知偵錯工具。|  
|[BreakpointSetError 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|通知偵錯工具, common language runtime (CLR) 無法正確地系結在函式為即時 (JIT) 編譯之前所設定的中斷點。|  
|[ControlCTrap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|通知偵錯工具在正在進行調試的進程中, 已攔截 CTRL + C。|  
|[CreateAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|通知偵錯工具已建立應用程式域。|  
|[CreateProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|第一次附加或啟動進程時, 會通知偵錯工具。|  
|[CreateThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|通知偵錯工具執行緒已開始執行 managed 程式碼。|  
|[DebuggerError 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|通知偵錯工具, 在嘗試處理來自 CLR 的事件時發生錯誤。|  
|[EditAndContinueRemap 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|已取代。 通知偵錯工具已將重新對應事件傳送至 IDE。|  
|[EvalComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|通知偵錯工具已完成評估。|  
|[EvalException 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|通知偵錯工具已因未處理的例外狀況而終止評估。|  
|[Exception 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|通知偵錯工具, 已從 managed 程式碼擲回例外狀況。|  
|[ExitAppDomain 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|通知偵錯工具, 應用程式域已結束。|  
|[ExitProcess 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|通知偵錯工具已結束進程。|  
|[ExitThread 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|通知偵錯工具, 執行 managed 程式碼的執行緒已結束。|  
|[LoadAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|通知偵錯工具已成功載入 CLR 元件。|  
|[LoadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|通知偵錯工具已載入類別。|  
|[LoadModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|通知偵錯工具已成功載入 CLR 模組。|  
|[LogMessage 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|通知偵錯工具 CLR managed 執行緒已呼叫<xref:System.Diagnostics.EventLog>類別中的方法來記錄事件。|  
|[LogSwitch 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|通知偵錯工具 CLR managed 執行緒已呼叫<xref:System.Diagnostics.Switch>類別中的方法, 以建立、修改或刪除偵錯工具/追蹤參數。|  
|[NameChange 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|通知偵錯工具, 應用程式域或執行緒的名稱已變更。|  
|[StepComplete 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|通知偵錯工具已完成步驟。|  
|[UnloadAssembly 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|通知偵錯工具已卸載 CLR 元件。|  
|[UnloadClass 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|通知偵錯工具正在卸載類別。|  
|[UnloadModule 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|通知偵錯工具已卸載 CLR 模組 (DLL)。|  
|[UpdateModuleSymbols 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|通知偵錯工具, CLR 模組的符號已經變更。|  
  
## <a name="remarks"></a>備註  
 所有回呼都會序列化, 並在相同的執行緒中呼叫, 並在進程處於已同步處理狀態時呼叫。  
  
 每個回呼的執行都必須呼叫[ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , 才能繼續執行。 如果`ICorDebugController::Continue`在回呼傳回之前未呼叫, 進程將會維持停止, 而且在呼叫之前`ICorDebugController::Continue` , 不會再發生事件回呼。  
  
 偵錯工具必須在 .NET Framework 版本2.0 應用程式中進行[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)時, 才會執行。 `ICorDebugManagedCallback` 或`ICorDebugManagedCallback2`的實例會當做回呼物件傳遞至[ICorDebug:: SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。  
  
> [!NOTE]
> 這個介面不支援跨電腦或跨處理序的遠端呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebug 介面](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [偵錯介面](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
