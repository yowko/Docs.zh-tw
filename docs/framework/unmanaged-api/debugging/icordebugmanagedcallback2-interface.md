---
title: "ICorDebugManagedCallback2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2
helpviewer_keywords: ICorDebugManagedCallback2 interface [.NET Framework debugging]
ms.assetid: cf7b7cfa-1c4b-4d8c-be70-4f9ed15a788b
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a46e8e4f23c57391877d8cb6ba6b35d50de151b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2-interface"></a><span data-ttu-id="61873-102">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="61873-102">ICorDebugManagedCallback2 Interface</span></span>
<span data-ttu-id="61873-103">提供方法來支援偵錯工具例外狀況處理和 Managed 偵錯助理 (MDA)。</span><span class="sxs-lookup"><span data-stu-id="61873-103">Provides methods to support debugger exception handling and managed debugging assistants (MDAs).</span></span> <span data-ttu-id="61873-104">`ICorDebugManagedCallback2`是的邏輯擴充功能[ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="61873-104">`ICorDebugManagedCallback2` is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="61873-105">方法</span><span class="sxs-lookup"><span data-stu-id="61873-105">Methods</span></span>  
  
|<span data-ttu-id="61873-106">方法</span><span class="sxs-lookup"><span data-stu-id="61873-106">Method</span></span>|<span data-ttu-id="61873-107">描述</span><span class="sxs-lookup"><span data-stu-id="61873-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="61873-108">ChangeConnection 方法</span><span class="sxs-lookup"><span data-stu-id="61873-108">ChangeConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)|<span data-ttu-id="61873-109">告知偵錯工具使用指定的連接相關聯的工作集，已變更。</span><span class="sxs-lookup"><span data-stu-id="61873-109">Notifies the debugger that the set of tasks associated with the specified connection has changed.</span></span>|  
|[<span data-ttu-id="61873-110">CreateConnection 方法</span><span class="sxs-lookup"><span data-stu-id="61873-110">CreateConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)|<span data-ttu-id="61873-111">告知偵錯工具已建立新的連接。</span><span class="sxs-lookup"><span data-stu-id="61873-111">Notifies the debugger that a new connection has been created.</span></span>|  
|[<span data-ttu-id="61873-112">DestroyConnection 方法</span><span class="sxs-lookup"><span data-stu-id="61873-112">DestroyConnection Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-destroyconnection-method.md)|<span data-ttu-id="61873-113">指定的連接已終止會告知偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="61873-113">Notifies the debugger that the specified connection has been terminated.</span></span>|  
|[<span data-ttu-id="61873-114">Exception 方法</span><span class="sxs-lookup"><span data-stu-id="61873-114">Exception Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)|<span data-ttu-id="61873-115">告知偵錯工具搜尋例外狀況處理常式已開始。</span><span class="sxs-lookup"><span data-stu-id="61873-115">Notifies the debugger that a search for an exception handler has started.</span></span>|  
|[<span data-ttu-id="61873-116">ExceptionUnwind 方法</span><span class="sxs-lookup"><span data-stu-id="61873-116">ExceptionUnwind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exceptionunwind-method.md)|<span data-ttu-id="61873-117">提供例外狀況回溯程序期間的狀態通知。</span><span class="sxs-lookup"><span data-stu-id="61873-117">Provides a status notification during the exception unwinding process.</span></span>|  
|[<span data-ttu-id="61873-118">FunctionRemapComplete 方法</span><span class="sxs-lookup"><span data-stu-id="61873-118">FunctionRemapComplete Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapcomplete-method.md)|<span data-ttu-id="61873-119">告知偵錯工具執行程式碼已切換為編輯的函式的新版本。</span><span class="sxs-lookup"><span data-stu-id="61873-119">Notifies the debugger that code execution has switched to a new version of an edited function.</span></span>|  
|[<span data-ttu-id="61873-120">FunctionRemapOpportunity 方法</span><span class="sxs-lookup"><span data-stu-id="61873-120">FunctionRemapOpportunity Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)|<span data-ttu-id="61873-121">告知偵錯工具執行程式碼已達到較舊版本的已編輯函式中的序列點。</span><span class="sxs-lookup"><span data-stu-id="61873-121">Notifies the debugger that code execution has reached a sequence point in an older version of an edited function.</span></span>|  
|[<span data-ttu-id="61873-122">MDANotification 方法</span><span class="sxs-lookup"><span data-stu-id="61873-122">MDANotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-mdanotification-method.md)|<span data-ttu-id="61873-123">提供執行程式碼發現 managed 偵錯助理 (MDA) 訊息的通知。</span><span class="sxs-lookup"><span data-stu-id="61873-123">Provides notification that code execution has encountered a managed debugging assistant (MDA) message.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61873-124">備註</span><span class="sxs-lookup"><span data-stu-id="61873-124">Remarks</span></span>  
 <span data-ttu-id="61873-125">`ICorDebugManagedCallback2`介面延伸`ICorDebugManagedCallback`處理 .NET Framework 2.0 版中引進的新偵錯事件介面。</span><span class="sxs-lookup"><span data-stu-id="61873-125">The `ICorDebugManagedCallback2` interface extends the `ICorDebugManagedCallback` interface to handle new debug events introduced in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="61873-126">偵錯工具必須實作`ICorDebugManagedCallback2`如果它.NET Framework 2.0 應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="61873-126">A debugger must implement `ICorDebugManagedCallback2` if it is debugging .NET Framework 2.0 applications.</span></span> <span data-ttu-id="61873-127">執行個體`ICorDebugManagedCallback`或`ICorDebugManagedCallback2`為回呼物件，以傳遞[icordebug:: Setmanagedhandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md)。</span><span class="sxs-lookup"><span data-stu-id="61873-127">An instance of `ICorDebugManagedCallback` or `ICorDebugManagedCallback2` is passed as the callback object to [ICorDebug::SetManagedHandler](../../../../docs/framework/unmanaged-api/debugging/icordebug-setmanagedhandler-method.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61873-128">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="61873-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61873-129">需求</span><span class="sxs-lookup"><span data-stu-id="61873-129">Requirements</span></span>  
 <span data-ttu-id="61873-130">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61873-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61873-131">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61873-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61873-132">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61873-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61873-133">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61873-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61873-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="61873-134">See Also</span></span>  
 [<span data-ttu-id="61873-135">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="61873-135">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="61873-136">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="61873-136">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="61873-137">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="61873-137">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
