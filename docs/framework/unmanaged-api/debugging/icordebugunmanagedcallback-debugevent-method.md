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
ms.openlocfilehash: 75341b1af034972c861b75f29a06eaa2c4e33c3a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703027"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="4774a-102">ICorDebugUnmanagedCallback::DebugEvent 方法</span><span class="sxs-lookup"><span data-stu-id="4774a-102">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>

<span data-ttu-id="4774a-103">通知偵錯工具已引發原生事件。</span><span class="sxs-lookup"><span data-stu-id="4774a-103">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4774a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4774a-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4774a-105">參數</span><span class="sxs-lookup"><span data-stu-id="4774a-105">Parameters</span></span>  

 `pDebugEvent`  
 <span data-ttu-id="4774a-106">在原生事件的指標。</span><span class="sxs-lookup"><span data-stu-id="4774a-106">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="4774a-107">[in] 如果未受管理的 `true` 事件發生之後，不可能發生與 managed 進程狀態的互動，直到偵錯工具呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md)，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="4774a-107">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4774a-108">備註</span><span class="sxs-lookup"><span data-stu-id="4774a-108">Remarks</span></span>  

 <span data-ttu-id="4774a-109">如果正在進行調試的執行緒是 Win32 執行緒，請不要使用 Win32 偵錯工具的任何成員。</span><span class="sxs-lookup"><span data-stu-id="4774a-109">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="4774a-110">您只能 `ICorDebugController::Continue` 在 Win32 執行緒上呼叫，而且只有在繼續超過頻外事件時才會呼叫。</span><span class="sxs-lookup"><span data-stu-id="4774a-110">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="4774a-111">`DebugEvent`回呼未遵循回呼的標準規則。</span><span class="sxs-lookup"><span data-stu-id="4774a-111">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="4774a-112">當您呼叫時 `DebugEvent` ，進程將會處於原始的 OS-debug 已停止狀態。</span><span class="sxs-lookup"><span data-stu-id="4774a-112">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="4774a-113">此程式將不會同步處理。</span><span class="sxs-lookup"><span data-stu-id="4774a-113">The process will not be synchronized.</span></span> <span data-ttu-id="4774a-114">它會在需要時自動輸入已同步處理的狀態，以滿足 managed 程式碼的相關資訊要求，這可能會導致其他的嵌套 `DebugEvent` 回呼。</span><span class="sxs-lookup"><span data-stu-id="4774a-114">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="4774a-115">在處理常式上呼叫 [ICorDebugProcess：： ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) ，以忽略例外狀況事件，然後再繼續處理。</span><span class="sxs-lookup"><span data-stu-id="4774a-115">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="4774a-116">呼叫這個方法會傳送 DBG_CONTINUE 而不是 DBG_EXCEPTION_NOT_HANDLED 繼續要求，並自動清除頻外中斷點和單一步驟例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4774a-116">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="4774a-117">即使正在進行調試的應用程式顯示為已停止，且已有未完成的內建事件，仍可能隨時都有頻外事件。</span><span class="sxs-lookup"><span data-stu-id="4774a-117">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="4774a-118">在 .NET Framework 2.0 版中，偵錯工具應該立即繼續超過頻外中斷點事件。</span><span class="sxs-lookup"><span data-stu-id="4774a-118">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="4774a-119">偵錯工具應該使用 [ICorDebugProcess2：： SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 和 [ICorDebugProcess2：： ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) 方法來加入和移除中斷點。</span><span class="sxs-lookup"><span data-stu-id="4774a-119">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="4774a-120">這些方法會自動略過任何頻外中斷點。</span><span class="sxs-lookup"><span data-stu-id="4774a-120">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="4774a-121">因此，唯一發送的頻外中斷點應該是已在指令資料流程中的原始中斷點，例如對 Win32 函數的呼叫 `DebugBreak` 。</span><span class="sxs-lookup"><span data-stu-id="4774a-121">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="4774a-122">請勿嘗試使用 `ICorDebugProcess::ClearCurrentException` 、 [ICorDebugProcess：： GetThreadCoNtext](icordebugprocess-getthreadcontext-method.md)、 [ICorDebugProcess：： SetThreadCoNtext](icordebugprocess-setthreadcontext-method.md)或任何其他 [調試](index.md)程式的成員。</span><span class="sxs-lookup"><span data-stu-id="4774a-122">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4774a-123">需求</span><span class="sxs-lookup"><span data-stu-id="4774a-123">Requirements</span></span>  

 <span data-ttu-id="4774a-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4774a-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4774a-125">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4774a-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4774a-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4774a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4774a-127">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4774a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4774a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4774a-128">See also</span></span>

- [<span data-ttu-id="4774a-129">ICorDebugUnmanagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4774a-129">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
