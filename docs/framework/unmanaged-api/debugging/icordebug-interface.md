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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 193232ce1006a9cf209db9330343386404948440
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168281"
---
# <a name="icordebug-interface"></a><span data-ttu-id="35a79-102">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="35a79-102">ICorDebug Interface</span></span>
<span data-ttu-id="35a79-103">提供方法，可讓開發人員能夠偵錯在 common language runtime (CLR) 環境中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="35a79-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35a79-104">不支援偵錯混合 （managed 和原生程式碼），在 Windows 95、windows Windows 98 或 Windows ME，或在非 x86 平台 （例如 IA64 和 AMD64） 上。</span><span class="sxs-lookup"><span data-stu-id="35a79-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35a79-105">方法</span><span class="sxs-lookup"><span data-stu-id="35a79-105">Methods</span></span>  
  
|<span data-ttu-id="35a79-106">方法</span><span class="sxs-lookup"><span data-stu-id="35a79-106">Method</span></span>|<span data-ttu-id="35a79-107">描述</span><span class="sxs-lookup"><span data-stu-id="35a79-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35a79-108">CanLaunchOrAttach 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-108">CanLaunchOrAttach Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-canlaunchorattach-method.md)|<span data-ttu-id="35a79-109">判斷是否有可能在目前的電腦以及執行階段組態的內容中啟動新的處理序，或附加至指定的處理序。</span><span class="sxs-lookup"><span data-stu-id="35a79-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="35a79-110">CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-110">CreateProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)|<span data-ttu-id="35a79-111">啟動處理程序和它所控制的偵錯工具的主要執行緒。</span><span class="sxs-lookup"><span data-stu-id="35a79-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="35a79-112">DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-112">DebugActiveProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md)|<span data-ttu-id="35a79-113">將偵錯工具附加至現有的處理序。</span><span class="sxs-lookup"><span data-stu-id="35a79-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="35a79-114">EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-114">EnumerateProcesses Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-enumerateprocesses-method.md)|<span data-ttu-id="35a79-115">取得正在偵錯的處理程序中的列舉值。</span><span class="sxs-lookup"><span data-stu-id="35a79-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="35a79-116">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-116">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-getprocess-method.md)|<span data-ttu-id="35a79-117">傳回"ICorDebugProcess 」 物件與指定的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="35a79-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="35a79-118">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-118">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md)|<span data-ttu-id="35a79-119">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="35a79-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="35a79-120">SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-120">SetManagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)|<span data-ttu-id="35a79-121">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="35a79-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="35a79-122">SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-122">SetUnmanagedHandler Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="35a79-123">指定未受管理的事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="35a79-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="35a79-124">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="35a79-124">Terminate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-terminate-method.md)|<span data-ttu-id="35a79-125">終止`ICorDebug`物件。</span><span class="sxs-lookup"><span data-stu-id="35a79-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35a79-126">備註</span><span class="sxs-lookup"><span data-stu-id="35a79-126">Remarks</span></span>  
 `ICorDebug` <span data-ttu-id="35a79-127">代表偵錯工具處理序的事件處理迴圈。</span><span class="sxs-lookup"><span data-stu-id="35a79-127">represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="35a79-128">偵錯工具必須等到[icordebugmanagedcallback:: Exitprocess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md)從正在偵錯之前釋出此介面的所有處理序的回呼。</span><span class="sxs-lookup"><span data-stu-id="35a79-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="35a79-129">`ICorDebug`物件是初始的物件，以控制所有進一步 managed 偵錯。</span><span class="sxs-lookup"><span data-stu-id="35a79-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="35a79-130">在.NET framework 1.0 和 1.1 版中，這個物件是`CoClass`建立 COM 物件</span><span class="sxs-lookup"><span data-stu-id="35a79-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="35a79-131">在.NET Framework 2.0 版中，此物件已不再`CoClass`物件。</span><span class="sxs-lookup"><span data-stu-id="35a79-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="35a79-132">它必須先建立[CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)函式，也就是多版本感知。</span><span class="sxs-lookup"><span data-stu-id="35a79-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="35a79-133">這個新建立的函式可讓用戶端取得的特定實作`ICorDebug`，這也會模擬偵錯 API 的特定版本。</span><span class="sxs-lookup"><span data-stu-id="35a79-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35a79-134">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="35a79-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a79-135">需求</span><span class="sxs-lookup"><span data-stu-id="35a79-135">Requirements</span></span>  
 <span data-ttu-id="35a79-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35a79-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a79-137">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35a79-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35a79-138">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35a79-138">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="35a79-139">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="35a79-139">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="35a79-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35a79-140">See also</span></span>

- [<span data-ttu-id="35a79-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="35a79-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
