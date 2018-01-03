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
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="defcf-102">ICorDebugUnmanagedCallback::DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="defcf-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="defcf-103">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="defcf-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="defcf-104">語法</span><span class="sxs-lookup"><span data-stu-id="defcf-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="defcf-105">參數</span><span class="sxs-lookup"><span data-stu-id="defcf-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="defcf-106">[in]原生事件指標。</span><span class="sxs-lookup"><span data-stu-id="defcf-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="defcf-107">[in]`true`，如果不可能與受管理的處理序狀態的互動是直到偵錯工具呼叫 unmanaged 的事件發生後[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="defcf-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="defcf-108">備註</span><span class="sxs-lookup"><span data-stu-id="defcf-108">Remarks</span></span>  
 <span data-ttu-id="defcf-109">如果正在偵錯執行緒的 Win32 執行緒，請勿使用任何成員 Win32 偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="defcf-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="defcf-110">您可以呼叫`ICorDebugController::Continue`只有 Win32 執行緒和過去的頻外事件繼續時，才。</span><span class="sxs-lookup"><span data-stu-id="defcf-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="defcf-111">`DebugEvent`回呼未遵循標準的規則，以便回呼。</span><span class="sxs-lookup"><span data-stu-id="defcf-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="defcf-112">當您呼叫`DebugEvent`、 處理程序會在未經處理、 OS 偵錯已停止 」 狀態。</span><span class="sxs-lookup"><span data-stu-id="defcf-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="defcf-113">將不會同步處理程序。</span><span class="sxs-lookup"><span data-stu-id="defcf-113">The process will not be synchronized.</span></span> <span data-ttu-id="defcf-114">它會自動進入已同步處理的狀態時所需滿足之 managed 程式碼，可能會導致巢狀其他資訊的要求`DebugEvent`回呼。</span><span class="sxs-lookup"><span data-stu-id="defcf-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="defcf-115">呼叫[icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)忽略例外狀況事件，然後再繼續此程序的程序。</span><span class="sxs-lookup"><span data-stu-id="defcf-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="defcf-116">呼叫這個方法會傳送繼續要求，而不是 DBG_EXCEPTION_NOT_HANDLED DBG_CONTINUE，並會自動清除 超出訊號範圍中斷點和逐步執行例外狀況。</span><span class="sxs-lookup"><span data-stu-id="defcf-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="defcf-117">超出訊號範圍事件都在任何時候，，和進行偵錯應用程式會出現停止時，即使當未處理的頻外事件已經存在。</span><span class="sxs-lookup"><span data-stu-id="defcf-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="defcf-118">在.NET Framework 2.0 版中，偵錯工具立即應該的頻外中斷點事件之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="defcf-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="defcf-119">應該使用偵錯工具[icordebugprocess2:: Setunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)和[icordebugprocess2:: Clearunmanagedbreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)新增和移除中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="defcf-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="defcf-120">這些方法會自動略過任何超出訊號範圍的中斷點。</span><span class="sxs-lookup"><span data-stu-id="defcf-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="defcf-121">因此，分派只 out-of-band 中斷點應該是未經處理已經存在於指令資料流，例如 Win32 呼叫中的中斷點`DebugBreak`函式。</span><span class="sxs-lookup"><span data-stu-id="defcf-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="defcf-122">請勿嘗試使用`ICorDebugProcess::ClearCurrentException`， [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)， [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)，或任何其他成員的[偵錯 API](../../../../docs/framework/unmanaged-api/debugging/index.md)。</span><span class="sxs-lookup"><span data-stu-id="defcf-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="defcf-123">需求</span><span class="sxs-lookup"><span data-stu-id="defcf-123">Requirements</span></span>  
 <span data-ttu-id="defcf-124">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="defcf-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="defcf-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="defcf-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="defcf-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="defcf-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="defcf-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="defcf-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="defcf-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="defcf-128">See Also</span></span>  
 [<span data-ttu-id="defcf-129">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="defcf-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
