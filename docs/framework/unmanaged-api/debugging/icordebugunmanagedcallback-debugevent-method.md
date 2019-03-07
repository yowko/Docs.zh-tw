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
ms.openlocfilehash: beb2b9f17696e293d14cf997ef69deb7557ed0bb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479238"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="d4c1e-102">ICorDebugUnmanagedCallback::DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="d4c1e-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="d4c1e-103">原生事件已引發會通知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c1e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4c1e-104">Syntax</span></span>  
  
```  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4c1e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4c1e-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="d4c1e-106">[in]原生的事件指標。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="d4c1e-107">[in]`true`，如果 managed 處理序狀態的互動是不可能在未受管理的事件發生，直到偵錯工具呼叫後[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); 否則`false`。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4c1e-108">備註</span><span class="sxs-lookup"><span data-stu-id="d4c1e-108">Remarks</span></span>  
 <span data-ttu-id="d4c1e-109">如果正在偵錯的執行緒是 Win32 執行緒，請勿使用任何成員的 Win32 偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="d4c1e-110">您可以呼叫`ICorDebugController::Continue`只有在 Win32 執行緒和過去的頻外事件繼續時，才。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="d4c1e-111">`DebugEvent`回呼不會遵循標準的規則，以便回呼。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="d4c1e-112">當您呼叫`DebugEvent`、 程序會在未經處理、 OS 偵錯已停止 」 狀態。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="d4c1e-113">將不會同步處理程序。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-113">The process will not be synchronized.</span></span> <span data-ttu-id="d4c1e-114">它會自動進入已同步處理的狀態時所需滿足的 managed 程式碼，可能會導致其他巢狀的相關資訊要求`DebugEvent`回呼。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="d4c1e-115">呼叫[icordebugprocess:: Clearcurrentexception](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)上忽略例外狀況事件，然後再繼續此程序的程序。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="d4c1e-116">呼叫這個方法將繼續要求，而不是 DBG_EXCEPTION_NOT_HANDLED DBG_CONTINUE，並會自動清除 頻外中斷點和逐步執行例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="d4c1e-117">頻外事件都在任何時間，，和正在偵錯應用程式會顯示已停止時，即使當未處理的頻內事件已經存在。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="d4c1e-118">在.NET Framework 2.0 版中，偵錯工具立即應超出的中斷點事件之後繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="d4c1e-119">應該使用偵錯工具[ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)並[ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)新增及移除中斷點的方法。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="d4c1e-120">這些方法會自動略過任何超出的中斷點。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="d4c1e-121">因此，分派只頻中斷點應已處於指令資料流，例如呼叫 Win32 的未經處理中斷點`DebugBreak`函式。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="d4c1e-122">請勿嘗試使用`ICorDebugProcess::ClearCurrentException`， [icordebugprocess:: Getthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)， [icordebugprocess:: Setthreadcontext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)，或任何其他成員[偵錯 API](../../../../docs/framework/unmanaged-api/debugging/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4c1e-123">需求</span><span class="sxs-lookup"><span data-stu-id="d4c1e-123">Requirements</span></span>  
 <span data-ttu-id="d4c1e-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4c1e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4c1e-125">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4c1e-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4c1e-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4c1e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4c1e-127">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4c1e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c1e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4c1e-128">See also</span></span>
- [<span data-ttu-id="d4c1e-129">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d4c1e-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
