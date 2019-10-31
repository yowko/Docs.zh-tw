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
ms.openlocfilehash: 2d865f837d38894e8449af671e2d12e7676dd040
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129128"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="fffcc-102">ICorDebugUnmanagedCallback::DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="fffcc-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>
<span data-ttu-id="fffcc-103">通知偵錯工具已引發原生事件。</span><span class="sxs-lookup"><span data-stu-id="fffcc-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fffcc-104">語法</span><span class="sxs-lookup"><span data-stu-id="fffcc-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fffcc-105">參數</span><span class="sxs-lookup"><span data-stu-id="fffcc-105">Parameters</span></span>  
 `pDebugEvent`  
 <span data-ttu-id="fffcc-106">在原生事件的指標。</span><span class="sxs-lookup"><span data-stu-id="fffcc-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="fffcc-107">[in] `true`，如果未受管理的事件發生，就無法與 managed 進程狀態互動，直到偵錯工具呼叫[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md);否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="fffcc-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fffcc-108">備註</span><span class="sxs-lookup"><span data-stu-id="fffcc-108">Remarks</span></span>  
 <span data-ttu-id="fffcc-109">如果正在進行調試的執行緒是 Win32 執行緒，請勿使用 Win32 調試介面的任何成員。</span><span class="sxs-lookup"><span data-stu-id="fffcc-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="fffcc-110">您只能在 Win32 執行緒上呼叫 `ICorDebugController::Continue`，而且只有在繼續超過頻外事件時才可以。</span><span class="sxs-lookup"><span data-stu-id="fffcc-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="fffcc-111">`DebugEvent` 回呼不會遵循回呼的標準規則。</span><span class="sxs-lookup"><span data-stu-id="fffcc-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="fffcc-112">當您呼叫 `DebugEvent`時，進程將會處於 [原始]、[OS-debug 已停止] 狀態。</span><span class="sxs-lookup"><span data-stu-id="fffcc-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="fffcc-113">此程式將不會同步處理。</span><span class="sxs-lookup"><span data-stu-id="fffcc-113">The process will not be synchronized.</span></span> <span data-ttu-id="fffcc-114">它會在必要時自動進入已同步處理的狀態，以滿足 managed 程式碼相關資訊的要求，而這可能會導致其他的嵌套 `DebugEvent` 回呼。</span><span class="sxs-lookup"><span data-stu-id="fffcc-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="fffcc-115">在進程上呼叫[ICorDebugProcess：： ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) ，以忽略例外狀況事件，然後再繼續處理常式。</span><span class="sxs-lookup"><span data-stu-id="fffcc-115">Call [ICorDebugProcess::ClearCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="fffcc-116">呼叫這個方法會在 CONTINUE 要求上傳送 DBG_CONTINUE 而不是 DBG_EXCEPTION_NOT_HANDLED，並自動清除頻外中斷點和單步驟例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fffcc-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="fffcc-117">即使正在進行調試的應用程式顯示為已停止，以及已有未處理的內建事件，也可能隨時都有頻外事件。</span><span class="sxs-lookup"><span data-stu-id="fffcc-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="fffcc-118">在 .NET Framework 版本2.0 中，偵錯工具應該立即繼續執行超出範圍外的中斷點事件。</span><span class="sxs-lookup"><span data-stu-id="fffcc-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="fffcc-119">偵錯工具應該使用[ICorDebugProcess2：： SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)和[ICorDebugProcess2：： ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md)方法來新增和移除中斷點。</span><span class="sxs-lookup"><span data-stu-id="fffcc-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="fffcc-120">這些方法會自動略過任何頻外中斷點。</span><span class="sxs-lookup"><span data-stu-id="fffcc-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="fffcc-121">因此，唯一分派的頻外中斷點應該是已在指令資料流程中的原始中斷點，例如 Win32 `DebugBreak` 函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="fffcc-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="fffcc-122">請勿嘗試使用 `ICorDebugProcess::ClearCurrentException`、 [ICorDebugProcess：： GetThreadCoNtext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)、 [ICorDebugProcess：： SetThreadCoNtext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)，或[調試 API](../../../../docs/framework/unmanaged-api/debugging/index.md)的任何其他成員。</span><span class="sxs-lookup"><span data-stu-id="fffcc-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](../../../../docs/framework/unmanaged-api/debugging/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fffcc-123">需求</span><span class="sxs-lookup"><span data-stu-id="fffcc-123">Requirements</span></span>  
 <span data-ttu-id="fffcc-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fffcc-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fffcc-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fffcc-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fffcc-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fffcc-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fffcc-127">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fffcc-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fffcc-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="fffcc-128">See also</span></span>

- [<span data-ttu-id="fffcc-129">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="fffcc-129">ICorDebugUnmanagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)
