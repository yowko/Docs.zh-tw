---
title: ICorDebug 介面
ms.date: 03/30/2017
api_name:
- ICorDebug
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug
helpviewer_keywords:
- ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type:
- apiref
ms.openlocfilehash: 21838bdd8ff45f8f74524dc4da52364fb032b396
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723398"
---
# <a name="icordebug-interface"></a><span data-ttu-id="0ce8b-102">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="0ce8b-102">ICorDebug Interface</span></span>

<span data-ttu-id="0ce8b-103">提供的方法可讓開發人員在 common language runtime (CLR) 環境中，進行應用程式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ce8b-104">在 Windows 95、Windows 98 或 Windows ME 或非 x86 平臺 (（例如 IA64 和 AMD64) ）上，不支援混合模式 (managed 和機器碼) 的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ce8b-105">方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-105">Methods</span></span>  
  
|<span data-ttu-id="0ce8b-106">方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-106">Method</span></span>|<span data-ttu-id="0ce8b-107">描述</span><span class="sxs-lookup"><span data-stu-id="0ce8b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ce8b-108">CanLaunchOrAttach 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-108">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="0ce8b-109">判斷在目前電腦和執行時間設定的內容中，是否可以啟動新的進程或附加至指定的進程。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="0ce8b-110">CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-110">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="0ce8b-111">在偵錯工具的控制下啟動進程和其主要執行緒。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="0ce8b-112">DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-112">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="0ce8b-113">將偵錯工具附加至現有的進程。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="0ce8b-114">EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-114">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="0ce8b-115">取得正在進行調試之進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="0ce8b-116">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-116">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="0ce8b-117">傳回具有指定處理序識別碼的 "ICorDebugProcess" 物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="0ce8b-118">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-118">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="0ce8b-119">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="0ce8b-120">SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-120">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="0ce8b-121">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="0ce8b-122">SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-122">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="0ce8b-123">指定非受控事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="0ce8b-124">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="0ce8b-124">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="0ce8b-125">終止 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ce8b-126">備註</span><span class="sxs-lookup"><span data-stu-id="0ce8b-126">Remarks</span></span>  

 <span data-ttu-id="0ce8b-127">`ICorDebug` 代表偵錯工具進程的事件處理迴圈。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="0ce8b-128">偵錯工具必須等待所有正在進行的進程的 [ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md) 回呼，再釋放這個介面。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="0ce8b-129">`ICorDebug`物件是用來控制所有進一步 managed 偵錯工具的初始物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="0ce8b-130">在 .NET Framework 1.0 和1.1 版中，此物件是 `CoClass` 從 COM 建立的物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="0ce8b-131">在 .NET Framework 2.0 版中，此物件不再是 `CoClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="0ce8b-132">它必須由 [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) 函式所建立，此函式可感知版本。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="0ce8b-133">這個新的建立函式可讓用戶端取得的特定執行 `ICorDebug` ，這也會模擬特定版本的偵錯工具 API。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ce8b-134">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ce8b-135">需求</span><span class="sxs-lookup"><span data-stu-id="0ce8b-135">Requirements</span></span>  

 <span data-ttu-id="0ce8b-136">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ce8b-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ce8b-137">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ce8b-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ce8b-138">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ce8b-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ce8b-139">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ce8b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce8b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ce8b-140">See also</span></span>

- [<span data-ttu-id="0ce8b-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="0ce8b-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
