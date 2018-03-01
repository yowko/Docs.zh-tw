---
title: "ICorDebugManagedCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fd864cbb5a95143f6dd7f55fc1b1fc57f9f42e98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback-interface"></a><span data-ttu-id="0cf97-102">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0cf97-102">ICorDebugManagedCallback Interface</span></span>
<span data-ttu-id="0cf97-103">提供方法來處理偵錯工具回呼。</span><span class="sxs-lookup"><span data-stu-id="0cf97-103">Provides methods to process debugger callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0cf97-104">方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-104">Methods</span></span>  
  
|<span data-ttu-id="0cf97-105">方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-105">Method</span></span>|<span data-ttu-id="0cf97-106">描述</span><span class="sxs-lookup"><span data-stu-id="0cf97-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0cf97-107">Break 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-107">Break Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-break-method.md)|<span data-ttu-id="0cf97-108">告知偵錯工具時<xref:System.Reflection.Emit.OpCodes.Break>執行指令碼資料流中的。</span><span class="sxs-lookup"><span data-stu-id="0cf97-108">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>|  
|[<span data-ttu-id="0cf97-109">Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-109">Breakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpoint-method.md)|<span data-ttu-id="0cf97-110">遇到中斷點時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-110">Notifies the debugger when a breakpoint is encountered.</span></span>|  
|[<span data-ttu-id="0cf97-111">BreakpointSetError 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-111">BreakpointSetError Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-breakpointseterror-method.md)|<span data-ttu-id="0cf97-112">Common language runtime (CLR) 無法正確地繫結在 just-in-time (JIT) 編譯函式之前已設定的中斷點會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-112">Notifies the debugger that the common language runtime (CLR) was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>|  
|[<span data-ttu-id="0cf97-113">ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-113">ControlCTrap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-controlctrap-method.md)|<span data-ttu-id="0cf97-114">CTRL + C 陷入正在偵錯的程序會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-114">Notifies the debugger that a CTRL+C is trapped in the process being debugged.</span></span>|  
|[<span data-ttu-id="0cf97-115">CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-115">CreateAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createappdomain-method.md)|<span data-ttu-id="0cf97-116">告知偵錯工具已建立應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="0cf97-116">Notifies the debugger that an application domain has been created.</span></span>|  
|[<span data-ttu-id="0cf97-117">CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-117">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createprocess-method.md)|<span data-ttu-id="0cf97-118">當處理程序已附加或第一次啟動時，請告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-118">Notifies the debugger when a process has been attached or started for the first time.</span></span>|  
|[<span data-ttu-id="0cf97-119">CreateThread 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-119">CreateThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md)|<span data-ttu-id="0cf97-120">執行緒已開始執行 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-120">Notifies the debugger that a thread has started executing managed code.</span></span>|  
|[<span data-ttu-id="0cf97-121">DebuggerError 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-121">DebuggerError Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-debuggererror-method.md)|<span data-ttu-id="0cf97-122">告知偵錯工具，在嘗試處理從 CLR 事件已發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cf97-122">Notifies the debugger that an error has occurred while attempting to handle an event from the CLR.</span></span>|  
|[<span data-ttu-id="0cf97-123">EditAndContinueRemap 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-123">EditAndContinueRemap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)|<span data-ttu-id="0cf97-124">已取代。</span><span class="sxs-lookup"><span data-stu-id="0cf97-124">Deprecated.</span></span> <span data-ttu-id="0cf97-125">重新對應事件已傳送至 IDE 會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-125">Notifies the debugger that a remap event has been sent to the IDE.</span></span>|  
|[<span data-ttu-id="0cf97-126">EvalComplete 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-126">EvalComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)|<span data-ttu-id="0cf97-127">告知偵錯工具評估已完成。</span><span class="sxs-lookup"><span data-stu-id="0cf97-127">Notifies the debugger that an evaluation has been completed.</span></span>|  
|[<span data-ttu-id="0cf97-128">EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-128">EvalException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalexception-method.md)|<span data-ttu-id="0cf97-129">告知偵錯工具，並發生未處理的例外狀況結束評估。</span><span class="sxs-lookup"><span data-stu-id="0cf97-129">Notifies the debugger that an evaluation has been terminated with an unhandled exception.</span></span>|  
|[<span data-ttu-id="0cf97-130">Exception 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-130">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exception-method.md)|<span data-ttu-id="0cf97-131">例外狀況已擲回從 managed 程式碼會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-131">Notifies the debugger that an exception has been thrown from managed code.</span></span>|  
|[<span data-ttu-id="0cf97-132">ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-132">ExitAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitappdomain-method.md)|<span data-ttu-id="0cf97-133">告知偵錯工具應用程式定義域已結束。</span><span class="sxs-lookup"><span data-stu-id="0cf97-133">Notifies the debugger that an application domain has exited.</span></span>|  
|[<span data-ttu-id="0cf97-134">ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-134">ExitProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)|<span data-ttu-id="0cf97-135">告知偵錯工具的處理序已經結束。</span><span class="sxs-lookup"><span data-stu-id="0cf97-135">Notifies the debugger that a process has exited.</span></span>|  
|[<span data-ttu-id="0cf97-136">ExitThread 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-136">ExitThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitthread-method.md)|<span data-ttu-id="0cf97-137">告知偵錯工具正在執行 managed 程式碼的執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="0cf97-137">Notifies the debugger that a thread that was executing managed code has exited.</span></span>|  
|[<span data-ttu-id="0cf97-138">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-138">LoadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadassembly-method.md)|<span data-ttu-id="0cf97-139">已成功載入 CLR 組件會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-139">Notifies the debugger that a CLR assembly has been successfully loaded.</span></span>|  
|[<span data-ttu-id="0cf97-140">LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-140">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)|<span data-ttu-id="0cf97-141">告知偵錯工具已載入類別。</span><span class="sxs-lookup"><span data-stu-id="0cf97-141">Notifies the debugger that a class has been loaded.</span></span>|  
|[<span data-ttu-id="0cf97-142">LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-142">LoadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)|<span data-ttu-id="0cf97-143">已成功載入 CLR 模組會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-143">Notifies the debugger that a CLR module has been successfully loaded.</span></span>|  
|[<span data-ttu-id="0cf97-144">LogMessage 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-144">LogMessage Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md)|<span data-ttu-id="0cf97-145">CLR managed 執行緒已呼叫方法，偵錯工具會通知<xref:System.Diagnostics.EventLog>記錄事件的類別。</span><span class="sxs-lookup"><span data-stu-id="0cf97-145">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>|  
|[<span data-ttu-id="0cf97-146">LogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-146">LogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logswitch-method.md)|<span data-ttu-id="0cf97-147">CLR managed 執行緒已呼叫方法，偵錯工具會通知<xref:System.Diagnostics.Switch>類別來建立、 修改或刪除偵錯/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="0cf97-147">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>|  
|[<span data-ttu-id="0cf97-148">NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-148">NameChange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-namechange-method.md)|<span data-ttu-id="0cf97-149">告知偵錯工具應用程式定義域或執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="0cf97-149">Notifies the debugger that the name of either an application domain or thread has changed.</span></span>|  
|[<span data-ttu-id="0cf97-150">StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-150">StepComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)|<span data-ttu-id="0cf97-151">告知偵錯工具已完成步驟。</span><span class="sxs-lookup"><span data-stu-id="0cf97-151">Notifies the debugger that a step has completed.</span></span>|  
|[<span data-ttu-id="0cf97-152">UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-152">UnloadAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadassembly-method.md)|<span data-ttu-id="0cf97-153">告知偵錯工具的 CLR 組件已卸載。</span><span class="sxs-lookup"><span data-stu-id="0cf97-153">Notifies the debugger that a CLR assembly has been unloaded.</span></span>|  
|[<span data-ttu-id="0cf97-154">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-154">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)|<span data-ttu-id="0cf97-155">表示正在卸載的類別會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0cf97-155">Notifies the debugger that a class is being unloaded.</span></span>|  
|[<span data-ttu-id="0cf97-156">UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-156">UnloadModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)|<span data-ttu-id="0cf97-157">告知偵錯工具為 CLR 模組 (DLL)，已卸載。</span><span class="sxs-lookup"><span data-stu-id="0cf97-157">Notifies the debugger that a CLR module (DLL) has been unloaded.</span></span>|  
|[<span data-ttu-id="0cf97-158">UpdateModuleSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="0cf97-158">UpdateModuleSymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-updatemodulesymbols-method.md)|<span data-ttu-id="0cf97-159">告知偵錯工具，已變更為 CLR 模組的符號。</span><span class="sxs-lookup"><span data-stu-id="0cf97-159">Notifies the debugger that the symbols for a CLR module have changed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cf97-160">備註</span><span class="sxs-lookup"><span data-stu-id="0cf97-160">Remarks</span></span>  
 <span data-ttu-id="0cf97-161">序列化，相同的執行緒中呼叫和以同步處理的狀態中的程序呼叫所有的回呼。</span><span class="sxs-lookup"><span data-stu-id="0cf97-161">All callbacks are serialized, called in the same thread, and called with the process in the synchronized state.</span></span>  
  
 <span data-ttu-id="0cf97-162">每個回呼實作必須呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0cf97-162">Each callback implementation must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution.</span></span> <span data-ttu-id="0cf97-163">如果`ICorDebugController::Continue`不之前呼叫在回呼傳回、 處理程序將保持停止並沒有更多的事件回呼將會發生，直到`ICorDebugController::Continue`呼叫。</span><span class="sxs-lookup"><span data-stu-id="0cf97-163">If `ICorDebugController::Continue` is not called before the callback returns, the process will remain stopped and no more event callbacks will occur until `ICorDebugController::Continue` is called.</span></span>  
  
 <span data-ttu-id="0cf97-164">偵錯工具必須實作[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)如果它.NET Framework 2.0 版的應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="0cf97-164">A debugger must implement [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) if it is debugging .NET Framework version 2.0 applications.</span></span> <span data-ttu-id="0cf97-165">執行個體`ICorDebugManagedCallback`或`ICorDebugManagedCallback2`為回呼物件，以傳遞[icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0cf97-165">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cf97-166">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0cf97-166">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cf97-167">需求</span><span class="sxs-lookup"><span data-stu-id="0cf97-167">Requirements</span></span>  
 <span data-ttu-id="0cf97-168">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0cf97-168">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cf97-169">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cf97-169">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cf97-170">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cf97-170">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cf97-171">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cf97-171">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cf97-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="0cf97-172">See Also</span></span>  
 [<span data-ttu-id="0cf97-173">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="0cf97-173">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="0cf97-174">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="0cf97-174">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="0cf97-175">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0cf97-175">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
