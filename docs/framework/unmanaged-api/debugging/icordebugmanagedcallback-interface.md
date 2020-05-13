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
ms.openlocfilehash: cb2b69c5e6dfed4e0cb4e4e324c4ec6ad664f3e7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212746"
---
# <a name="icordebugmanagedcallback-interface"></a><span data-ttu-id="1cc44-102">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1cc44-102">ICorDebugManagedCallback Interface</span></span>
<span data-ttu-id="1cc44-103">提供方法來處理偵錯工具回呼。</span><span class="sxs-lookup"><span data-stu-id="1cc44-103">Provides methods to process debugger callbacks.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1cc44-104">方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-104">Methods</span></span>  
  
|<span data-ttu-id="1cc44-105">方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-105">Method</span></span>|<span data-ttu-id="1cc44-106">描述</span><span class="sxs-lookup"><span data-stu-id="1cc44-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1cc44-107">Break 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-107">Break Method</span></span>](icordebugmanagedcallback-break-method.md)|<span data-ttu-id="1cc44-108">執行程式碼資料流程中的指令時，通知偵錯工具 <xref:System.Reflection.Emit.OpCodes.Break> 。</span><span class="sxs-lookup"><span data-stu-id="1cc44-108">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>|  
|[<span data-ttu-id="1cc44-109">Breakpoint 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-109">Breakpoint Method</span></span>](icordebugmanagedcallback-breakpoint-method.md)|<span data-ttu-id="1cc44-110">遇到中斷點時，通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1cc44-110">Notifies the debugger when a breakpoint is encountered.</span></span>|  
|[<span data-ttu-id="1cc44-111">BreakpointSetError 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-111">BreakpointSetError Method</span></span>](icordebugmanagedcallback-breakpointseterror-method.md)|<span data-ttu-id="1cc44-112">通知偵錯工具，common language runtime （CLR）無法正確地系結在函式為即時（JIT）編譯之前所設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="1cc44-112">Notifies the debugger that the common language runtime (CLR) was unable to accurately bind a breakpoint that was set before a function was just-in-time (JIT) compiled.</span></span>|  
|[<span data-ttu-id="1cc44-113">ControlCTrap 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-113">ControlCTrap Method</span></span>](icordebugmanagedcallback-controlctrap-method.md)|<span data-ttu-id="1cc44-114">通知偵錯工具在正在進行調試的進程中，已攔截 CTRL + C。</span><span class="sxs-lookup"><span data-stu-id="1cc44-114">Notifies the debugger that a CTRL+C is trapped in the process being debugged.</span></span>|  
|[<span data-ttu-id="1cc44-115">CreateAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-115">CreateAppDomain Method</span></span>](icordebugmanagedcallback-createappdomain-method.md)|<span data-ttu-id="1cc44-116">通知偵錯工具已建立應用程式域。</span><span class="sxs-lookup"><span data-stu-id="1cc44-116">Notifies the debugger that an application domain has been created.</span></span>|  
|[<span data-ttu-id="1cc44-117">CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-117">CreateProcess Method</span></span>](icordebugmanagedcallback-createprocess-method.md)|<span data-ttu-id="1cc44-118">第一次附加或啟動進程時，會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1cc44-118">Notifies the debugger when a process has been attached or started for the first time.</span></span>|  
|[<span data-ttu-id="1cc44-119">CreateThread 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-119">CreateThread Method</span></span>](icordebugmanagedcallback-createthread-method.md)|<span data-ttu-id="1cc44-120">通知偵錯工具執行緒已開始執行 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cc44-120">Notifies the debugger that a thread has started executing managed code.</span></span>|  
|[<span data-ttu-id="1cc44-121">DebuggerError 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-121">DebuggerError Method</span></span>](icordebugmanagedcallback-debuggererror-method.md)|<span data-ttu-id="1cc44-122">通知偵錯工具，在嘗試處理來自 CLR 的事件時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1cc44-122">Notifies the debugger that an error has occurred while attempting to handle an event from the CLR.</span></span>|  
|[<span data-ttu-id="1cc44-123">EditAndContinueRemap 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-123">EditAndContinueRemap Method</span></span>](icordebugmanagedcallback-editandcontinueremap-method.md)|<span data-ttu-id="1cc44-124">已被取代。</span><span class="sxs-lookup"><span data-stu-id="1cc44-124">Deprecated.</span></span> <span data-ttu-id="1cc44-125">通知偵錯工具已將重新對應事件傳送至 IDE。</span><span class="sxs-lookup"><span data-stu-id="1cc44-125">Notifies the debugger that a remap event has been sent to the IDE.</span></span>|  
|[<span data-ttu-id="1cc44-126">EvalComplete 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-126">EvalComplete Method</span></span>](icordebugmanagedcallback-evalcomplete-method.md)|<span data-ttu-id="1cc44-127">通知偵錯工具已完成評估。</span><span class="sxs-lookup"><span data-stu-id="1cc44-127">Notifies the debugger that an evaluation has been completed.</span></span>|  
|[<span data-ttu-id="1cc44-128">EvalException 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-128">EvalException Method</span></span>](icordebugmanagedcallback-evalexception-method.md)|<span data-ttu-id="1cc44-129">通知偵錯工具已因未處理的例外狀況而終止評估。</span><span class="sxs-lookup"><span data-stu-id="1cc44-129">Notifies the debugger that an evaluation has been terminated with an unhandled exception.</span></span>|  
|[<span data-ttu-id="1cc44-130">Exception 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-130">Exception Method</span></span>](icordebugmanagedcallback-exception-method.md)|<span data-ttu-id="1cc44-131">通知偵錯工具，已從 managed 程式碼擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cc44-131">Notifies the debugger that an exception has been thrown from managed code.</span></span>|  
|[<span data-ttu-id="1cc44-132">ExitAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-132">ExitAppDomain Method</span></span>](icordebugmanagedcallback-exitappdomain-method.md)|<span data-ttu-id="1cc44-133">通知偵錯工具，應用程式域已結束。</span><span class="sxs-lookup"><span data-stu-id="1cc44-133">Notifies the debugger that an application domain has exited.</span></span>|  
|[<span data-ttu-id="1cc44-134">ExitProcess 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-134">ExitProcess Method</span></span>](icordebugmanagedcallback-exitprocess-method.md)|<span data-ttu-id="1cc44-135">通知偵錯工具已結束進程。</span><span class="sxs-lookup"><span data-stu-id="1cc44-135">Notifies the debugger that a process has exited.</span></span>|  
|[<span data-ttu-id="1cc44-136">ExitThread 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-136">ExitThread Method</span></span>](icordebugmanagedcallback-exitthread-method.md)|<span data-ttu-id="1cc44-137">通知偵錯工具，執行 managed 程式碼的執行緒已結束。</span><span class="sxs-lookup"><span data-stu-id="1cc44-137">Notifies the debugger that a thread that was executing managed code has exited.</span></span>|  
|[<span data-ttu-id="1cc44-138">LoadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-138">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)|<span data-ttu-id="1cc44-139">通知偵錯工具已成功載入 CLR 元件。</span><span class="sxs-lookup"><span data-stu-id="1cc44-139">Notifies the debugger that a CLR assembly has been successfully loaded.</span></span>|  
|[<span data-ttu-id="1cc44-140">LoadClass 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-140">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)|<span data-ttu-id="1cc44-141">通知偵錯工具已載入類別。</span><span class="sxs-lookup"><span data-stu-id="1cc44-141">Notifies the debugger that a class has been loaded.</span></span>|  
|[<span data-ttu-id="1cc44-142">LoadModule 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-142">LoadModule Method</span></span>](icordebugmanagedcallback-loadmodule-method.md)|<span data-ttu-id="1cc44-143">通知偵錯工具已成功載入 CLR 模組。</span><span class="sxs-lookup"><span data-stu-id="1cc44-143">Notifies the debugger that a CLR module has been successfully loaded.</span></span>|  
|[<span data-ttu-id="1cc44-144">LogMessage 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-144">LogMessage Method</span></span>](icordebugmanagedcallback-logmessage-method.md)|<span data-ttu-id="1cc44-145">通知偵錯工具 CLR managed 執行緒已呼叫類別中的方法 <xref:System.Diagnostics.EventLog> 來記錄事件。</span><span class="sxs-lookup"><span data-stu-id="1cc44-145">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.EventLog> class to log an event.</span></span>|  
|[<span data-ttu-id="1cc44-146">LogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-146">LogSwitch Method</span></span>](icordebugmanagedcallback-logswitch-method.md)|<span data-ttu-id="1cc44-147">通知偵錯工具 CLR managed 執行緒已呼叫類別中的方法 <xref:System.Diagnostics.Switch> ，以建立、修改或刪除偵錯工具/追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="1cc44-147">Notifies the debugger that a CLR managed thread has called a method in the <xref:System.Diagnostics.Switch> class to create, modify, or delete a debugging/tracing switch.</span></span>|  
|[<span data-ttu-id="1cc44-148">NameChange 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-148">NameChange Method</span></span>](icordebugmanagedcallback-namechange-method.md)|<span data-ttu-id="1cc44-149">通知偵錯工具，應用程式域或執行緒的名稱已變更。</span><span class="sxs-lookup"><span data-stu-id="1cc44-149">Notifies the debugger that the name of either an application domain or thread has changed.</span></span>|  
|[<span data-ttu-id="1cc44-150">StepComplete 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-150">StepComplete Method</span></span>](icordebugmanagedcallback-stepcomplete-method.md)|<span data-ttu-id="1cc44-151">通知偵錯工具已完成步驟。</span><span class="sxs-lookup"><span data-stu-id="1cc44-151">Notifies the debugger that a step has completed.</span></span>|  
|[<span data-ttu-id="1cc44-152">UnloadAssembly 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-152">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)|<span data-ttu-id="1cc44-153">通知偵錯工具已卸載 CLR 元件。</span><span class="sxs-lookup"><span data-stu-id="1cc44-153">Notifies the debugger that a CLR assembly has been unloaded.</span></span>|  
|[<span data-ttu-id="1cc44-154">UnloadClass 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-154">UnloadClass Method</span></span>](icordebugmanagedcallback-unloadclass-method.md)|<span data-ttu-id="1cc44-155">通知偵錯工具正在卸載類別。</span><span class="sxs-lookup"><span data-stu-id="1cc44-155">Notifies the debugger that a class is being unloaded.</span></span>|  
|[<span data-ttu-id="1cc44-156">UnloadModule 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-156">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)|<span data-ttu-id="1cc44-157">通知偵錯工具已卸載 CLR 模組（DLL）。</span><span class="sxs-lookup"><span data-stu-id="1cc44-157">Notifies the debugger that a CLR module (DLL) has been unloaded.</span></span>|  
|[<span data-ttu-id="1cc44-158">UpdateModuleSymbols 方法</span><span class="sxs-lookup"><span data-stu-id="1cc44-158">UpdateModuleSymbols Method</span></span>](icordebugmanagedcallback-updatemodulesymbols-method.md)|<span data-ttu-id="1cc44-159">通知偵錯工具，CLR 模組的符號已經變更。</span><span class="sxs-lookup"><span data-stu-id="1cc44-159">Notifies the debugger that the symbols for a CLR module have changed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cc44-160">備註</span><span class="sxs-lookup"><span data-stu-id="1cc44-160">Remarks</span></span>  
 <span data-ttu-id="1cc44-161">所有回呼都會序列化，並在相同的執行緒中呼叫，並在進程處於已同步處理狀態時呼叫。</span><span class="sxs-lookup"><span data-stu-id="1cc44-161">All callbacks are serialized, called in the same thread, and called with the process in the synchronized state.</span></span>  
  
 <span data-ttu-id="1cc44-162">每個回呼的執行都必須呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md) ，才能繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1cc44-162">Each callback implementation must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution.</span></span> <span data-ttu-id="1cc44-163">如果在 `ICorDebugController::Continue` 回呼傳回之前未呼叫，進程將會維持停止，而且在呼叫之前，不會再發生事件回呼 `ICorDebugController::Continue` 。</span><span class="sxs-lookup"><span data-stu-id="1cc44-163">If `ICorDebugController::Continue` is not called before the callback returns, the process will remain stopped and no more event callbacks will occur until `ICorDebugController::Continue` is called.</span></span>  
  
 <span data-ttu-id="1cc44-164">偵錯工具必須在 .NET Framework 版本2.0 應用程式中進行[ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md)時，才會執行。</span><span class="sxs-lookup"><span data-stu-id="1cc44-164">A debugger must implement [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) if it is debugging .NET Framework version 2.0 applications.</span></span> <span data-ttu-id="1cc44-165">或的實例 `ICorDebugManagedCallback` `ICorDebugManagedCallback2` 會當做回呼物件傳遞至[ICorDebug：： SetManagedHandler](icordebug-setmanagedhandler-method.md)。</span><span class="sxs-lookup"><span data-stu-id="1cc44-165">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cc44-166">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1cc44-166">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cc44-167">需求</span><span class="sxs-lookup"><span data-stu-id="1cc44-167">Requirements</span></span>  
 <span data-ttu-id="1cc44-168">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1cc44-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc44-169">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cc44-169">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cc44-170">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cc44-170">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cc44-171">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc44-171">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc44-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="1cc44-172">See also</span></span>

- [<span data-ttu-id="1cc44-173">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="1cc44-173">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="1cc44-174">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="1cc44-174">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="1cc44-175">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1cc44-175">Debugging Interfaces</span></span>](debugging-interfaces.md)
