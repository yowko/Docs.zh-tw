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
ms.openlocfilehash: 0ca66f001d04bc86b64e0fe2d1cd37559e4fc633
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785109"
---
# <a name="icordebug-interface"></a><span data-ttu-id="90a8d-102">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="90a8d-102">ICorDebug Interface</span></span>
<span data-ttu-id="90a8d-103">提供可讓開發人員在 common language runtime （CLR）環境中，對應用程式進行 debug 的方法。</span><span class="sxs-lookup"><span data-stu-id="90a8d-103">Provides methods that allow developers to debug applications in the common language runtime (CLR) environment.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90a8d-104">Windows 95、Windows 98 或 Windows ME 或非 x86 平臺（例如 IA64 和 AMD64）不支援混合模式（managed 和機器碼）的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="90a8d-104">Mixed-mode (managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA64 and AMD64).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90a8d-105">方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-105">Methods</span></span>  
  
|<span data-ttu-id="90a8d-106">方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-106">Method</span></span>|<span data-ttu-id="90a8d-107">描述</span><span class="sxs-lookup"><span data-stu-id="90a8d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90a8d-108">CanLaunchOrAttach 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-108">CanLaunchOrAttach Method</span></span>](icordebug-canlaunchorattach-method.md)|<span data-ttu-id="90a8d-109">判斷是否可以在目前的電腦和執行時間設定的內容中，啟動新的進程或附加至指定的進程。</span><span class="sxs-lookup"><span data-stu-id="90a8d-109">Determines whether launching a new process or attaching to the given process is possible within the context of the current machine and runtime configuration.</span></span>|  
|[<span data-ttu-id="90a8d-110">CreateProcess 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-110">CreateProcess Method</span></span>](icordebug-createprocess-method.md)|<span data-ttu-id="90a8d-111">在偵錯工具的控制項底下啟動進程和其主要執行緒。</span><span class="sxs-lookup"><span data-stu-id="90a8d-111">Launches a process and its primary thread under the control of the debugger.</span></span>|  
|[<span data-ttu-id="90a8d-112">DebugActiveProcess 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-112">DebugActiveProcess Method</span></span>](icordebug-debugactiveprocess-method.md)|<span data-ttu-id="90a8d-113">將偵錯工具附加至現有的進程。</span><span class="sxs-lookup"><span data-stu-id="90a8d-113">Attaches the debugger to an existing process.</span></span>|  
|[<span data-ttu-id="90a8d-114">EnumerateProcesses 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-114">EnumerateProcesses Method</span></span>](icordebug-enumerateprocesses-method.md)|<span data-ttu-id="90a8d-115">取得正在進行調試之進程的列舉值。</span><span class="sxs-lookup"><span data-stu-id="90a8d-115">Gets an enumerator for the processes that are being debugged.</span></span>|  
|[<span data-ttu-id="90a8d-116">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-116">GetProcess Method</span></span>](icordebug-getprocess-method.md)|<span data-ttu-id="90a8d-117">傳回具有指定處理序識別碼的 "ICorDebugProcess" 物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-117">Returns the "ICorDebugProcess" object with the given process ID.</span></span>|  
|[<span data-ttu-id="90a8d-118">Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-118">Initialize Method</span></span>](icordebug-initialize-method.md)|<span data-ttu-id="90a8d-119">初始化 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-119">Initializes the `ICorDebug` object.</span></span>|  
|[<span data-ttu-id="90a8d-120">SetManagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-120">SetManagedHandler Method</span></span>](icordebug-setmanagedhandler-method.md)|<span data-ttu-id="90a8d-121">指定 managed 事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-121">Specifies the event handler object for managed events.</span></span>|  
|[<span data-ttu-id="90a8d-122">SetUnmanagedHandler 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-122">SetUnmanagedHandler Method</span></span>](icordebug-setunmanagedhandler-method.md)|<span data-ttu-id="90a8d-123">指定非受控事件的事件處理常式物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-123">Specifies the event handler object for unmanaged events.</span></span>|  
|[<span data-ttu-id="90a8d-124">Terminate 方法</span><span class="sxs-lookup"><span data-stu-id="90a8d-124">Terminate Method</span></span>](icordebug-terminate-method.md)|<span data-ttu-id="90a8d-125">終止 `ICorDebug` 物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-125">Terminates the `ICorDebug` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90a8d-126">備註</span><span class="sxs-lookup"><span data-stu-id="90a8d-126">Remarks</span></span>  
 <span data-ttu-id="90a8d-127">`ICorDebug` 代表偵錯工具進程的事件處理迴圈。</span><span class="sxs-lookup"><span data-stu-id="90a8d-127">`ICorDebug` represents an event processing loop for a debugger process.</span></span> <span data-ttu-id="90a8d-128">偵錯工具必須等到所有進程中的[ICorDebugManagedCallback：： ExitProcess](icordebugmanagedcallback-exitprocess-method.md)回呼，才會釋放此介面。</span><span class="sxs-lookup"><span data-stu-id="90a8d-128">The debugger must wait for the [ICorDebugManagedCallback::ExitProcess](icordebugmanagedcallback-exitprocess-method.md) callback from all processes being debugged before releasing this interface.</span></span>  
  
 <span data-ttu-id="90a8d-129">`ICorDebug` 物件是用來控制所有進一步 managed 調試的初始物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-129">The `ICorDebug` object is the initial object to control all further managed debugging.</span></span> <span data-ttu-id="90a8d-130">在 .NET Framework 版本1.0 和1.1 中，此物件是從 COM 建立的 `CoClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-130">In the .NET Framework versions 1.0 and 1.1, this object was a `CoClass` object created from COM.</span></span> <span data-ttu-id="90a8d-131">在 .NET Framework 版本2.0 中，此物件不再是 `CoClass` 物件。</span><span class="sxs-lookup"><span data-stu-id="90a8d-131">In the .NET Framework version 2.0, this object is no longer a `CoClass` object.</span></span> <span data-ttu-id="90a8d-132">它必須由[CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)函式所建立，這是更容易感知版本的功能。</span><span class="sxs-lookup"><span data-stu-id="90a8d-132">It must be created by the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function, which is more version-aware.</span></span> <span data-ttu-id="90a8d-133">這項新的建立功能可讓用戶端取得 `ICorDebug`的特定執行，這也會模擬特定版本的調試 API。</span><span class="sxs-lookup"><span data-stu-id="90a8d-133">This new creation function enables clients to get a specific implementation of `ICorDebug`, which also emulates a specific version of the debugging API.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90a8d-134">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="90a8d-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90a8d-135">需求</span><span class="sxs-lookup"><span data-stu-id="90a8d-135">Requirements</span></span>  
 <span data-ttu-id="90a8d-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90a8d-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90a8d-137">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90a8d-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90a8d-138">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90a8d-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90a8d-139">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90a8d-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a8d-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="90a8d-140">See also</span></span>

- [<span data-ttu-id="90a8d-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="90a8d-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
