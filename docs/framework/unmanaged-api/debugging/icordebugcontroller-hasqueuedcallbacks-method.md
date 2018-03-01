---
title: "ICorDebugController::HasQueuedCallbacks 方法"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03d52bb31a81876a00e1af33494b14fb99fee0fa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerhasqueuedcallbacks-method"></a><span data-ttu-id="dd4ff-102">ICorDebugController::HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="dd4ff-102">ICorDebugController::HasQueuedCallbacks Method</span></span>
<span data-ttu-id="dd4ff-103">取得值，指出是否針對指定的執行緒目前佇列任何受管理的回呼。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-103">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd4ff-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd4ff-104">Syntax</span></span>  
  
```  
HRESULT HasQueuedCallbacks (  
    [in] ICorDebugThread *pThread,  
    [out] BOOL           *pbQueued  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd4ff-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd4ff-105">Parameters</span></span>  
 `pThread`  
 <span data-ttu-id="dd4ff-106">[in]表示執行緒 」 ICorDebugThread 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-106">[in] A pointer to an "ICorDebugThread" object that represents the thread.</span></span>  
  
 `pbQueued`  
 <span data-ttu-id="dd4ff-107">[out]值的指標`true`如果任何受管理的回呼目前佇列指定的執行緒，否則`false`。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-107">[out] A pointer to a value that is `true` if any managed callbacks are currently queued for the specified thread; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="dd4ff-108">如果指定 null`pThread`參數，`HasQueuedCallbacks`會傳回`true`如果目前沒有任何執行緒排入佇列 managed 回撥。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-108">If null is specified for the `pThread` parameter, `HasQueuedCallbacks` will return `true` if there are currently managed callbacks queued for any thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd4ff-109">備註</span><span class="sxs-lookup"><span data-stu-id="dd4ff-109">Remarks</span></span>  
 <span data-ttu-id="dd4ff-110">回呼會分派的一次，每次[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)呼叫。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-110">Callbacks will be dispatched one at a time, each time [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) is called.</span></span> <span data-ttu-id="dd4ff-111">偵錯工具可以檢查這個旗標，如果想要報告多個同時發生的偵錯事件。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-111">The debugger can check this flag if it wants to report multiple debugging events that occur simultaneously.</span></span>  
  
 <span data-ttu-id="dd4ff-112">當偵錯事件會排入佇列時，它們已經發生，因此偵錯工具必須清空整個佇列，以確定偵錯項目狀態。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-112">When debugging events are queued, they have already occurred, so the debugger must drain the entire queue to be sure of the state of the debuggee.</span></span> <span data-ttu-id="dd4ff-113">(呼叫`ICorDebugController::Continue`清空佇列。)例如，如果佇列包含兩個執行緒上的偵錯事件*X*，和偵錯工具暫止的執行緒*X*之後第一個偵錯事件，然後呼叫`ICorDebugController::Continue`，第二個偵錯事件執行緒*X*會分派，雖然執行緒已經暫止。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-113">(Call `ICorDebugController::Continue` to drain the queue.) For example, if the queue contains two debugging events on thread *X*, and the debugger suspends thread *X* after the first debugging event and then calls `ICorDebugController::Continue`, the second debugging event for thread *X* will be dispatched although the thread has been suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd4ff-114">需求</span><span class="sxs-lookup"><span data-stu-id="dd4ff-114">Requirements</span></span>  
 <span data-ttu-id="dd4ff-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd4ff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd4ff-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd4ff-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd4ff-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd4ff-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd4ff-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd4ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4ff-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="dd4ff-119">See Also</span></span>  
 
