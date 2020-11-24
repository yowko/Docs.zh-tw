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
ms.openlocfilehash: 1ca9e55a2183ca4293d30607496b588cbf21d6dd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679943"
---
# <a name="icordebugcontroller-interface"></a><span data-ttu-id="59adb-102">ICorDebugController 介面</span><span class="sxs-lookup"><span data-stu-id="59adb-102">ICorDebugController Interface</span></span>

<span data-ttu-id="59adb-103">表示可以控制程式碼執行內容的範圍 (<xref:System.Diagnostics.Process> 或 <xref:System.AppDomain> 其中一項)。</span><span class="sxs-lookup"><span data-stu-id="59adb-103">Represents a scope, either a <xref:System.Diagnostics.Process> or an <xref:System.AppDomain>, in which code execution context can be controlled.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="59adb-104">方法</span><span class="sxs-lookup"><span data-stu-id="59adb-104">Methods</span></span>  
  
|<span data-ttu-id="59adb-105">方法</span><span class="sxs-lookup"><span data-stu-id="59adb-105">Method</span></span>|<span data-ttu-id="59adb-106">描述</span><span class="sxs-lookup"><span data-stu-id="59adb-106">Description</span></span>|  
|------------|-----------------|  
|`ICorDebugController::CanCommitChanges`|<span data-ttu-id="59adb-107">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="59adb-107">This method is obsolete.</span></span>|  
|`ICorDebugController::CommitChanges`|<span data-ttu-id="59adb-108">這個方法已過時。</span><span class="sxs-lookup"><span data-stu-id="59adb-108">This method is obsolete.</span></span>|  
|[<span data-ttu-id="59adb-109">Continue 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-109">Continue Method</span></span>](icordebugcontroller-continue-method.md)|<span data-ttu-id="59adb-110">在呼叫 [ICorDebugController：： Stop](icordebugcontroller-stop-method.md)之後，繼續執行 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="59adb-110">Resumes execution of managed threads after a call to [ICorDebugController::Stop](icordebugcontroller-stop-method.md).</span></span>|  
|[<span data-ttu-id="59adb-111">Detach 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-111">Detach Method</span></span>](icordebugcontroller-detach-method.md)|<span data-ttu-id="59adb-112">卸離進程或應用程式域中的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="59adb-112">Detaches the debugger from the process or application domain.</span></span>|  
|[<span data-ttu-id="59adb-113">EnumerateThreads 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-113">EnumerateThreads Method</span></span>](icordebugcontroller-enumeratethreads-method.md)|<span data-ttu-id="59adb-114">取得進程中使用中 managed 執行緒的列舉值。</span><span class="sxs-lookup"><span data-stu-id="59adb-114">Gets an enumerator for the active managed threads in the process.</span></span>|  
|[<span data-ttu-id="59adb-115">HasQueuedCallbacks 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-115">HasQueuedCallbacks Method</span></span>](icordebugcontroller-hasqueuedcallbacks-method.md)|<span data-ttu-id="59adb-116">取得值，這個值表示是否目前已針對指定的執行緒將任何受控回呼排入佇列。</span><span class="sxs-lookup"><span data-stu-id="59adb-116">Gets a value that indicates whether any managed callbacks are currently queued for the specified thread.</span></span>|  
|[<span data-ttu-id="59adb-117">IsRunning 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-117">IsRunning Method</span></span>](icordebugcontroller-isrunning-method.md)|<span data-ttu-id="59adb-118">取得值，這個值表示進程中的執行緒目前是否可自由執行。</span><span class="sxs-lookup"><span data-stu-id="59adb-118">Gets a value that indicates whether the threads in the process are currently running freely.</span></span>|  
|[<span data-ttu-id="59adb-119">SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-119">SetAllThreadsDebugState Method</span></span>](icordebugcontroller-setallthreadsdebugstate-method.md)|<span data-ttu-id="59adb-120">設定進程中所有 managed 執行緒的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="59adb-120">Sets the debug state of all managed threads in the process.</span></span>|  
|[<span data-ttu-id="59adb-121">Stop 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-121">Stop Method</span></span>](icordebugcontroller-stop-method.md)|<span data-ttu-id="59adb-122">在進程中執行 managed 程式碼的所有線程上執行合作式停止。</span><span class="sxs-lookup"><span data-stu-id="59adb-122">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>|  
|[<span data-ttu-id="59adb-123">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="59adb-123">Terminate Method</span></span>](icordebugcontroller-terminate-method.md)|<span data-ttu-id="59adb-124">使用指定的結束代碼終止進程。</span><span class="sxs-lookup"><span data-stu-id="59adb-124">Terminates the process with the specified exit code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59adb-125">備註</span><span class="sxs-lookup"><span data-stu-id="59adb-125">Remarks</span></span>  

 <span data-ttu-id="59adb-126">如果 `ICorDebugController` 控制進程，則範圍會包含進程的所有線程。</span><span class="sxs-lookup"><span data-stu-id="59adb-126">If `ICorDebugController` is controlling a process, the scope includes all threads of the process.</span></span> <span data-ttu-id="59adb-127">如果 `ICorDebugController` 是控制應用程式域，則範圍僅包含該特定應用程式域的執行緒。</span><span class="sxs-lookup"><span data-stu-id="59adb-127">If `ICorDebugController` is controlling an application domain, the scope includes only the threads of that particular application domain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="59adb-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="59adb-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59adb-129">需求</span><span class="sxs-lookup"><span data-stu-id="59adb-129">Requirements</span></span>  

 <span data-ttu-id="59adb-130">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="59adb-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59adb-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59adb-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59adb-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59adb-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59adb-133">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59adb-133">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59adb-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59adb-134">See also</span></span>

- [<span data-ttu-id="59adb-135">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="59adb-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
