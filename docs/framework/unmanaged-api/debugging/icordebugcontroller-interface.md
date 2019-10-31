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
ms.openlocfilehash: 27f991c12ea7786d6146b5731848ca5ad3a37e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125363"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="a940c-102">ICorDebugController 介面</span><span class="sxs-lookup"><span data-stu-id="a940c-102">ICorDebugController Interface</span></span>

<span data-ttu-id="a940c-103">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="a940c-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a940c-104">方法</span><span class="sxs-lookup"><span data-stu-id="a940c-104">Methods</span></span>  
  
|<span data-ttu-id="a940c-105">方法</span><span class="sxs-lookup"><span data-stu-id="a940c-105">Method</span></span>|<span data-ttu-id="a940c-106">描述</span><span class="sxs-lookup"><span data-stu-id="a940c-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="a940c-107">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="a940c-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="a940c-108">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="a940c-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="a940c-109">Continue 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="a940c-110">呼叫[ICorDebugController：： Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)之後，繼續執行 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="a940c-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="a940c-111">Detach 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="a940c-112">從進程或應用程式域中卸離偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a940c-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="a940c-113">EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="a940c-114">取得進程中使用中 managed 執行緒的列舉值。</span><span class="sxs-lookup"><span data-stu-id="a940c-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="a940c-115">HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="a940c-116">取得值，指出目前是否已針對指定的執行緒將任何 managed 回呼排入佇列。</span><span class="sxs-lookup"><span data-stu-id="a940c-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="a940c-117">IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="a940c-118">取得值，指出進程中的執行緒目前是否可自由執行。</span><span class="sxs-lookup"><span data-stu-id="a940c-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="a940c-119">SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="a940c-120">設定進程中所有 managed 執行緒的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="a940c-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="a940c-121">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="a940c-122">在進程中執行 managed 程式碼的所有線程上執行合作性停止。</span><span class="sxs-lookup"><span data-stu-id="a940c-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="a940c-123">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="a940c-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="a940c-124">使用指定的結束代碼終止進程。</span><span class="sxs-lookup"><span data-stu-id="a940c-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a940c-125">備註</span><span class="sxs-lookup"><span data-stu-id="a940c-125">Remarks</span></span>  
 <span data-ttu-id="a940c-126">如果 `ICorDebugController` 正在控制進程，範圍會包含進程的所有線程。</span><span class="sxs-lookup"><span data-stu-id="a940c-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="a940c-127">如果 `ICorDebugController` 控制應用程式域，則範圍只會包含該特定應用程式域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a940c-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a940c-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a940c-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a940c-129">需求</span><span class="sxs-lookup"><span data-stu-id="a940c-129">Requirements</span></span>  
 <span data-ttu-id="a940c-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a940c-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a940c-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a940c-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a940c-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a940c-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a940c-133">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a940c-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a940c-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="a940c-134">See also</span></span>

- [<span data-ttu-id="a940c-135">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a940c-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
