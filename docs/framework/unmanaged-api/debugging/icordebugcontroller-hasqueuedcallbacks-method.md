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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d17f51867b64780fca9b21c5f48c88db36343af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748779"
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="e213e-102">ICorDebugController::HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="e213e-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="e213e-103">取得值，指出是否任何受管理的回呼目前在佇列中等待指定的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e213e-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e213e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e213e-104">Syntax</span></span>  
  
```cpp  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e213e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e213e-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="e213e-106">[in]表示執行緒 」 ICorDebugThread 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="e213e-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="e213e-107">[out]為值的指標`true`如果任何受管理的回呼目前針對指定的執行緒已排入佇列，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="e213e-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="e213e-108">如果指定 null`pThread`參數，`HasQueuedCallbacks`會傳回`true`如果目前沒有受管理的回呼排入佇列的任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="e213e-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e213e-109">備註</span><span class="sxs-lookup"><span data-stu-id="e213e-109">Remarks</span></span>  
 <span data-ttu-id="e213e-110">回呼會在時間內，每次分派的一個[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="e213e-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="e213e-111">偵錯工具可以檢查此旗標，如果想要報告多個同時進行的偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="e213e-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="e213e-112">當偵錯事件會排入佇列時，它們已經發生，因此偵錯工具必須清空的偵錯工具的狀態，確定整個佇列。</span><span class="sxs-lookup"><span data-stu-id="e213e-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="e213e-113">(呼叫`ICorDebugController::Continue`清空佇列。)比方說，如果佇列包含兩個執行緒上的偵錯事件*X*，以及偵錯工具暫止的執行緒*X*之後第一個偵錯事件，然後呼叫`ICorDebugController::Continue`，第二個偵錯事件執行緒*X*雖然已暫停的執行緒會分派。</span><span class="sxs-lookup"><span data-stu-id="e213e-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e213e-114">需求</span><span class="sxs-lookup"><span data-stu-id="e213e-114">Requirements</span></span>  
 <span data-ttu-id="e213e-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e213e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e213e-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e213e-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e213e-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e213e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e213e-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e213e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e213e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e213e-119">See also</span></span>
