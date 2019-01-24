---
title: ICorDebugController 介面 1
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
ms.openlocfilehash: c0651f8cd63f2ebdc6b81e92c0b55d94fe51316b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54645297"
---
# <a name="icordebugcontroller-interface1"></a><span data-ttu-id="5346a-102">ICorDebugController 介面 1</span><span class="sxs-lookup"><span data-stu-id="5346a-102">ICorDebugController Interface1</span></span>
<span data-ttu-id="5346a-103">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="5346a-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5346a-104">方法</span><span class="sxs-lookup"><span data-stu-id="5346a-104">Methods</span></span>  
  
|<span data-ttu-id="5346a-105">方法</span><span class="sxs-lookup"><span data-stu-id="5346a-105">Method</span></span>|<span data-ttu-id="5346a-106">描述</span><span class="sxs-lookup"><span data-stu-id="5346a-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="5346a-107">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="5346a-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="5346a-108">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="5346a-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="5346a-109">Continue 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-109">Continue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)|<span data-ttu-id="5346a-110">之後繼續執行的受管理的執行緒呼叫[icordebugcontroller:: Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5346a-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="5346a-111">Detach 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-111">Detach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-detach-method.md)|<span data-ttu-id="5346a-112">中斷連結處理序或應用程式定義域與偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5346a-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="5346a-113">EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-113">EnumerateThreads Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="5346a-114">取得作用中的 managed 執行緒處理序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="5346a-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="5346a-115">HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-115">HasQueuedCallbacks Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="5346a-116">取得值，指出是否任何受管理的回呼目前在佇列中等待指定的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5346a-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="5346a-117">IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-117">IsRunning Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-isrunning-method.md)|<span data-ttu-id="5346a-118">取得值，指出是否在程序中的執行緒目前正在自由。</span><span class="sxs-lookup"><span data-stu-id="5346a-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="5346a-119">SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-119">SetAllThreadsDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="5346a-120">設定程序中的所有 managed 執行緒的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="5346a-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="5346a-121">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-121">Stop Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)|<span data-ttu-id="5346a-122">在此程序中執行 managed 程式碼的所有執行緒上執行合作式的停駐點。</span><span class="sxs-lookup"><span data-stu-id="5346a-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="5346a-123">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="5346a-123">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-terminate-method.md)|<span data-ttu-id="5346a-124">終止與指定的結束代碼的程序。</span><span class="sxs-lookup"><span data-stu-id="5346a-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5346a-125">備註</span><span class="sxs-lookup"><span data-stu-id="5346a-125">Remarks</span></span>  
 <span data-ttu-id="5346a-126">如果`ICorDebugController`是控制處理程序，其範圍包括所有執行緒的處理程序。</span><span class="sxs-lookup"><span data-stu-id="5346a-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="5346a-127">如果`ICorDebugController`會控制應用程式定義域，範圍包括該特定應用程式定義域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5346a-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5346a-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5346a-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5346a-129">需求</span><span class="sxs-lookup"><span data-stu-id="5346a-129">Requirements</span></span>  
 <span data-ttu-id="5346a-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5346a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5346a-131">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5346a-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5346a-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5346a-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5346a-133">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5346a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5346a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5346a-134">See also</span></span>
- [<span data-ttu-id="5346a-135">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5346a-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
