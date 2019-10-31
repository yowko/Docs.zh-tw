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
ms.openlocfilehash: 51ee8b3631bffe9fd7fef4351e0aa67d1cbbe2c9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125391"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="6c4b3-102">ICorDebugController::HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="6c4b3-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="6c4b3-103">取得值，指出目前是否已針對指定的執行緒將任何 managed 回呼排入佇列。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="6c4b3-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c4b3-105">參數</span><span class="sxs-lookup"><span data-stu-id="6c4b3-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="6c4b3-106">在代表執行緒之 "ICorDebugThread" 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="6c4b3-107">脫銷如果目前已針對指定的執行緒將任何 managed 回呼排入佇列，則為 `true` 的值指標。否則，`false`。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="6c4b3-108">如果指定了 `pThread` 參數的 null，`HasQueuedCallbacks` 會傳回 `true` （如果有任何執行緒目前已排入佇列的受控回呼）。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c4b3-109">備註</span><span class="sxs-lookup"><span data-stu-id="6c4b3-109">Remarks</span></span>  
 <span data-ttu-id="6c4b3-110">回呼會一次分派一個，每次呼叫[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)時。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="6c4b3-111">如果偵錯工具想要報告同時發生的多個偵測事件，可以檢查此旗標。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="6c4b3-112">當偵測事件排入佇列時，它們已經發生，因此偵錯工具必須清空整個佇列，以確保偵錯工具的狀態。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="6c4b3-113">（呼叫 `ICorDebugController::Continue` 以清空佇列）。例如，如果佇列包含執行緒*x*上的兩個偵測事件，而且偵錯工具在第一個偵錯工具事件之後暫停執行緒*x* ，然後呼叫 `ICorDebugController::Continue`，則會分派執行緒*x*的第二個偵錯工具事件，但執行緒已暫止。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c4b3-114">需求</span><span class="sxs-lookup"><span data-stu-id="6c4b3-114">Requirements</span></span>  
 <span data-ttu-id="6c4b3-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6c4b3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c4b3-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6c4b3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6c4b3-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c4b3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c4b3-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c4b3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c4b3-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="6c4b3-119">See also</span></span>
