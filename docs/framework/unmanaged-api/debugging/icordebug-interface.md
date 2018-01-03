---
title: "ICorDebug 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug
helpviewer_keywords: ICorDebug interface [.NET Framework debugging]
ms.assetid: 33f431d7-ab1a-494d-8af2-20ab15aba194
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ed0b3a8b42157f6a4fcbc6b4a05a416da736147
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebug-interface"></a><span data-ttu-id="b0384-102">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="b0384-102">ICorDebug Interface</span></span>
<span data-ttu-id="b0384-103">提供方法，可讓開發人員偵錯在 common language runtime (CLR) 環境中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0384-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0384-104">不支援偵錯混合模式 （managed 與原生程式碼），在 Windows 95、 Windows 98 或 Windows ME 或非 x86 的平台 （例如 IA64 和 AMD64）。</span><span class="sxs-lookup"><span data-stu-id="b0384-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0384-105">方法</span><span class="sxs-lookup"><span data-stu-id="b0384-105">Methods</span></span>  
  
|<span data-ttu-id="b0384-106">方法</span><span class="sxs-lookup"><span data-stu-id="b0384-106">Method</span></span>|<span data-ttu-id="b0384-107">描述</span><span class="sxs-lookup"><span data-stu-id="b0384-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0384-108">CanLaunchOrAttach 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="b0384-109">判斷是否可能在目前的電腦以及執行階段組態的內容中啟動新的處理序或附加至指定的處理序。</span><span class="sxs-lookup"><span data-stu-id="b0384-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="b0384-110">CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="b0384-111">啟動處理序與它所控制的偵錯工具的主要執行緒。</span><span class="sxs-lookup"><span data-stu-id="b0384-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="b0384-112">DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="b0384-113">將偵錯工具附加至現有的處理序。</span><span class="sxs-lookup"><span data-stu-id="b0384-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="b0384-114">EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="b0384-115">取得正在進行偵錯的處理程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="b0384-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="b0384-116">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="b0384-117">傳回"ICorDebugProcess 」 物件，並提供指定的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="b0384-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="b0384-118">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="b0384-119">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="b0384-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="b0384-120">SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="b0384-121">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="b0384-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="b0384-122">SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="b0384-123">指定 unmanaged 事件的事件處理常式的物件。</span><span class="sxs-lookup"><span data-stu-id="b0384-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="b0384-124">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="b0384-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="b0384-125">終止`ICorDebug`物件。</span><span class="sxs-lookup"><span data-stu-id="b0384-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0384-126">備註</span><span class="sxs-lookup"><span data-stu-id="b0384-126">Remarks</span></span>  
 <span data-ttu-id="b0384-127">`ICorDebug`表示在偵錯工具處理序的事件處理迴圈。</span><span class="sxs-lookup"><span data-stu-id="b0384-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="b0384-128">偵錯工具必須等候[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)從所有處理序進行偵錯之前釋出此介面的回呼。</span><span class="sxs-lookup"><span data-stu-id="b0384-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="b0384-129">`ICorDebug`物件是要控制所有進一步 managed 偵錯的初始物件。</span><span class="sxs-lookup"><span data-stu-id="b0384-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="b0384-130">在.NET framework 1.0 和 1.1 版中，這個物件是`CoClass`所建立的 COM 物件</span><span class="sxs-lookup"><span data-stu-id="b0384-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="b0384-131">在.NET Framework 2.0 版中，此物件已不再`CoClass`物件。</span><span class="sxs-lookup"><span data-stu-id="b0384-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="b0384-132">它必須先建立[CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)函式，也就是多版本感知。</span><span class="sxs-lookup"><span data-stu-id="b0384-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="b0384-133">這個新的建立函式可讓用戶端取得的特定實作`ICorDebug`，也是模擬偵錯 API 的特定版本。</span><span class="sxs-lookup"><span data-stu-id="b0384-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0384-134">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b0384-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0384-135">需求</span><span class="sxs-lookup"><span data-stu-id="b0384-135">Requirements</span></span>  
 <span data-ttu-id="b0384-136">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b0384-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0384-137">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0384-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0384-138">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0384-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0384-139">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0384-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0384-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="b0384-140">See Also</span></span>  
 [<span data-ttu-id="b0384-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b0384-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
