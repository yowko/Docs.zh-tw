---
title: ICorDebugController 介面
ms.date: 03/30/2017
api_name:
- ICorDebugController
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController
helpviewer_keywords:
- ICorDebugController interface [.NET Framework debugging]
ms.assetid: dbb1c4dc-269a-459b-ab1d-6c70788782ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7628aa0ad10398f92d475c4c776810e13fac22b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749497"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="5338c-102">ICorDebugController 介面</span><span class="sxs-lookup"><span data-stu-id="5338c-102">ICorDebugController Interface</span></span>

<span data-ttu-id="5338c-103">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="5338c-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5338c-104">方法</span><span class="sxs-lookup"><span data-stu-id="5338c-104">Methods</span></span>  
  
|<span data-ttu-id="5338c-105">方法</span><span class="sxs-lookup"><span data-stu-id="5338c-105">Method</span></span>|<span data-ttu-id="5338c-106">描述</span><span class="sxs-lookup"><span data-stu-id="5338c-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="5338c-107">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="5338c-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="5338c-108">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="5338c-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="5338c-109">Continue 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="5338c-110">之後繼續執行的受管理的執行緒呼叫[icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5338c-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="5338c-111">Detach 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="5338c-112">中斷連結處理序或應用程式定義域與偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5338c-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="5338c-113">EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="5338c-114">取得作用中的 managed 執行緒處理序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5338c-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="5338c-115">HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="5338c-116">取得值，指出是否任何受管理的回呼目前在佇列中等待指定的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5338c-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="5338c-117">IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="5338c-118">取得值，指出是否在程序中的執行緒目前正在自由。</span><span class="sxs-lookup"><span data-stu-id="5338c-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="5338c-119">SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="5338c-120">設定程序中的所有 managed 執行緒的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="5338c-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="5338c-121">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="5338c-122">在此程序中執行 managed 程式碼的所有執行緒上執行合作式的停駐點。</span><span class="sxs-lookup"><span data-stu-id="5338c-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="5338c-123">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="5338c-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="5338c-124">終止與指定的結束代碼的程序。</span><span class="sxs-lookup"><span data-stu-id="5338c-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5338c-125">備註</span><span class="sxs-lookup"><span data-stu-id="5338c-125">Remarks</span></span>  
 <span data-ttu-id="5338c-126">如果`ICorDebugController`是控制處理程序，其範圍包括所有執行緒的處理程序。</span><span class="sxs-lookup"><span data-stu-id="5338c-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="5338c-127">如果`ICorDebugController`會控制應用程式定義域，範圍包括該特定應用程式定義域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5338c-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5338c-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5338c-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5338c-129">需求</span><span class="sxs-lookup"><span data-stu-id="5338c-129">Requirements</span></span>  
 <span data-ttu-id="5338c-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5338c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5338c-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5338c-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5338c-132">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5338c-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5338c-133">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5338c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5338c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5338c-134">See also</span></span>

- [<span data-ttu-id="5338c-135">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5338c-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
