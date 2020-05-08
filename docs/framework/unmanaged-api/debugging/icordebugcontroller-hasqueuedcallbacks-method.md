---
title: ICorDebugController::HasQueuedCallbacks 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.HasQueuedCallbacks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::HasQueuedCallbacks
helpviewer_keywords:
- HasQueuedCallbacks method [.NET Framework debugging]
- ICorDebugController::HasQueuedCallbacks method [.NET Framework debugging]
ms.assetid: 0d6a1cd9-370b-4462-adbf-e3980e897ea7
topic_type:
- apiref
ms.openlocfilehash: bd656445c2451d0583ddbc45e71c9e090bb80305
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892783"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="59fb8-102">ICorDebugController::HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="59fb8-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="59fb8-103">取得值，指出目前是否已針對指定的執行緒將任何 managed 回呼排入佇列。</span><span class="sxs-lookup"><span data-stu-id="59fb8-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59fb8-104">語法</span><span class="sxs-lookup"><span data-stu-id="59fb8-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59fb8-105">參數</span><span class="sxs-lookup"><span data-stu-id="59fb8-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="59fb8-106">在代表執行緒之 "ICorDebugThread" 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="59fb8-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="59fb8-107">脫銷值的指標，如果目前已`true`針對指定的執行緒將任何 managed 回呼排入佇列，則為;否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="59fb8-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="59fb8-108">如果為`pThread`參數指定 null， `HasQueuedCallbacks`將會`true`在目前有 managed 回呼排入佇列給任何執行緒時傳回。</span><span class="sxs-lookup"><span data-stu-id="59fb8-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59fb8-109">備註</span><span class="sxs-lookup"><span data-stu-id="59fb8-109">Remarks</span></span>  
 <span data-ttu-id="59fb8-110">回呼會一次分派一個，每次呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)時。</span><span class="sxs-lookup"><span data-stu-id="59fb8-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="59fb8-111">如果偵錯工具想要報告同時發生的多個偵測事件，可以檢查此旗標。</span><span class="sxs-lookup"><span data-stu-id="59fb8-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="59fb8-112">當偵測事件排入佇列時，它們已經發生，因此偵錯工具必須清空整個佇列，以確保偵錯工具的狀態。</span><span class="sxs-lookup"><span data-stu-id="59fb8-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="59fb8-113">（呼叫`ICorDebugController::Continue`以清空佇列）。例如，如果佇列包含執行緒*x*上的兩個偵測事件，而偵錯工具在第一次調試事件之後暫停執行緒*x* ， `ICorDebugController::Continue`然後再呼叫，則執行緒*x*的第二個偵錯工具事件將會分派，雖然執行緒已暫止。</span><span class="sxs-lookup"><span data-stu-id="59fb8-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59fb8-114">需求</span><span class="sxs-lookup"><span data-stu-id="59fb8-114">Requirements</span></span>  
 <span data-ttu-id="59fb8-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59fb8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59fb8-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59fb8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59fb8-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59fb8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59fb8-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59fb8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59fb8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59fb8-119">See also</span></span>
