---
title: ICorDebugManagedCallback2 介面
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2
helpviewer_keywords:
- ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type:
- apiref
ms.openlocfilehash: 97f103844c38ebd3dbff058bfe96ab953cdba960
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131477"
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="d33ad-102">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="d33ad-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="d33ad-103">提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="d33ad-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="d33ad-104">`ICorDebugManagedCallback2` 是[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)介面的邏輯擴充。</span><span class="sxs-lookup"><span data-stu-id="d33ad-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d33ad-105">方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-105">Methods</span></span>  
  
|<span data-ttu-id="d33ad-106">方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-106">Method</span></span>|<span data-ttu-id="d33ad-107">描述</span><span class="sxs-lookup"><span data-stu-id="d33ad-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d33ad-108">ChangeConnection 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="d33ad-109">通知偵錯工具與指定的連接相關聯的工作集已變更。</span><span class="sxs-lookup"><span data-stu-id="d33ad-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="d33ad-110">CreateConnection 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="d33ad-111">通知偵錯工具已建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="d33ad-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="d33ad-112">DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="d33ad-113">通知偵錯工具已終止指定的連接。</span><span class="sxs-lookup"><span data-stu-id="d33ad-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="d33ad-114">Exception 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="d33ad-115">通知偵錯工具已開始搜尋例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="d33ad-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="d33ad-116">ExceptionUnwind 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="d33ad-117">提供例外狀況回溯程式期間的狀態通知。</span><span class="sxs-lookup"><span data-stu-id="d33ad-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="d33ad-118">FunctionRemapComplete 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="d33ad-119">通知偵錯工具程式碼執行已切換至新版本的已編輯函式。</span><span class="sxs-lookup"><span data-stu-id="d33ad-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="d33ad-120">FunctionRemapOpportunity 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="d33ad-121">通知偵錯工具程式碼執行已到達較舊版本的已編輯函式中的序列點。</span><span class="sxs-lookup"><span data-stu-id="d33ad-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="d33ad-122">MDANotification 方法</span><span class="sxs-lookup"><span data-stu-id="d33ad-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="d33ad-123">提供程式碼執行已遇到 managed 偵錯工具（MDA）訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="d33ad-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d33ad-124">備註</span><span class="sxs-lookup"><span data-stu-id="d33ad-124">Remarks</span></span>  
 <span data-ttu-id="d33ad-125">`ICorDebugManagedCallback2` 介面會擴充 `ICorDebugManagedCallback` 介面，以處理 .NET Framework 版本2.0 中引進的新 debug 事件。</span><span class="sxs-lookup"><span data-stu-id="d33ad-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="d33ad-126">偵錯工具必須在 .NET Framework 2.0 應用程式中進行 `ICorDebugManagedCallback2` 時，才會執行。</span><span class="sxs-lookup"><span data-stu-id="d33ad-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="d33ad-127">`ICorDebugManagedCallback` 或 `ICorDebugManagedCallback2` 的實例會當做回呼物件傳遞至[ICorDebug：： SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d33ad-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d33ad-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="d33ad-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d33ad-129">需求</span><span class="sxs-lookup"><span data-stu-id="d33ad-129">Requirements</span></span>  
 <span data-ttu-id="d33ad-130">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d33ad-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d33ad-131">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d33ad-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d33ad-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d33ad-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d33ad-133">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d33ad-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d33ad-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="d33ad-134">See also</span></span>

- [<span data-ttu-id="d33ad-135">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="d33ad-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="d33ad-136">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d33ad-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d33ad-137">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d33ad-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
