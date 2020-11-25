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
ms.openlocfilehash: bd623f8bee2feafebe80c0c7513bcfb33d6ad367
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707889"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="19503-102">ICorDebugController::HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="19503-102">ICorDebugController::HasQueuedCallbacks Method</span></span>

<span data-ttu-id="19503-103">取得值，這個值表示是否目前已針對指定的執行緒將任何受控回呼排入佇列。</span><span class="sxs-lookup"><span data-stu-id="19503-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19503-104">語法</span><span class="sxs-lookup"><span data-stu-id="19503-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19503-105">參數</span><span class="sxs-lookup"><span data-stu-id="19503-105">Parameters</span></span>  

 `pThread`  
 <span data-ttu-id="19503-106">在代表執行緒之 "ICorDebugThread" 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="19503-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="19503-107">擴展值的指標， `true` 如果有任何受控回呼目前排入指定執行緒的佇列，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="19503-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="19503-108">如果為參數指定了 null `pThread` ，則 `HasQueuedCallbacks` `true` 如果目前有任何執行緒的受控回呼已排入佇列，則會傳回。</span><span class="sxs-lookup"><span data-stu-id="19503-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19503-109">備註</span><span class="sxs-lookup"><span data-stu-id="19503-109">Remarks</span></span>  

 <span data-ttu-id="19503-110">回呼會一次分派一個，每次呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 。</span><span class="sxs-lookup"><span data-stu-id="19503-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="19503-111">如果偵錯工具想要報告多個同時發生的偵錯工具事件，則可以檢查此旗標。</span><span class="sxs-lookup"><span data-stu-id="19503-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="19503-112">當偵測到事件已排入佇列時，偵錯工具必須清空整個佇列，以確定偵錯工具的狀態。</span><span class="sxs-lookup"><span data-stu-id="19503-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="19503-113"> (呼叫 `ICorDebugController::Continue` 以清空佇列 ) 。例如，如果佇列包含執行緒 *x* 上的兩個偵錯工具事件，而且偵錯工具在第一個偵測事件之後暫停執行緒 *x* ，然後呼叫，則會 `ICorDebugController::Continue` 分派執行緒 *x* 的第二個偵測事件，雖然執行緒已暫止。</span><span class="sxs-lookup"><span data-stu-id="19503-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19503-114">需求</span><span class="sxs-lookup"><span data-stu-id="19503-114">Requirements</span></span>  

 <span data-ttu-id="19503-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19503-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19503-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19503-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19503-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19503-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19503-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19503-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19503-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19503-119">See also</span></span>
