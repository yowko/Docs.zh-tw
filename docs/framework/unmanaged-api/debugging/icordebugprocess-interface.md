---
title: ICorDebugProcess 介面
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: 393ac8c119f111b645e7ccdb6ea94efee7207fa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128799"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="6e602-102">ICorDebugProcess 介面</span><span class="sxs-lookup"><span data-stu-id="6e602-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="6e602-103">表示執行 Managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="6e602-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="6e602-104">這個介面是 ICorDebugController 的子類別。</span><span class="sxs-lookup"><span data-stu-id="6e602-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e602-105">方法</span><span class="sxs-lookup"><span data-stu-id="6e602-105">Methods</span></span>  
  
|<span data-ttu-id="6e602-106">方法</span><span class="sxs-lookup"><span data-stu-id="6e602-106">Method</span></span>|<span data-ttu-id="6e602-107">描述</span><span class="sxs-lookup"><span data-stu-id="6e602-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e602-108">ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="6e602-109">清除指定執行緒上目前的非受控例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6e602-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="6e602-110">EnableLogMessages 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="6e602-111">啟用和停用將記錄訊息傳送至偵錯工具的功能。</span><span class="sxs-lookup"><span data-stu-id="6e602-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="6e602-112">EnumerateAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="6e602-113">列舉進程中的所有應用程式域。</span><span class="sxs-lookup"><span data-stu-id="6e602-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="6e602-114">EnumerateObjects 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="6e602-115">未實作。</span><span class="sxs-lookup"><span data-stu-id="6e602-115">Not implemented.</span></span>|  
|[<span data-ttu-id="6e602-116">GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="6e602-117">取得進程的控制碼。</span><span class="sxs-lookup"><span data-stu-id="6e602-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="6e602-118">GetHelperThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="6e602-119">取得偵錯工具內部 helper 執行緒的作業系統（OS）執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="6e602-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="6e602-120">GetID 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="6e602-121">取得進程的作業系統（OS）識別碼。</span><span class="sxs-lookup"><span data-stu-id="6e602-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="6e602-122">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="6e602-123">未實作。</span><span class="sxs-lookup"><span data-stu-id="6e602-123">Not implemented.</span></span>|  
|[<span data-ttu-id="6e602-124">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="6e602-125">取得具有指定之 OS 執行緒識別碼的 ICorDebugThread 實例。</span><span class="sxs-lookup"><span data-stu-id="6e602-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="6e602-126">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="6e602-127">取得給定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="6e602-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="6e602-128">IsOSSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="6e602-129">判斷線程是否因偵錯工具停止進程而暫停。</span><span class="sxs-lookup"><span data-stu-id="6e602-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="6e602-130">IsTransitionStub 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="6e602-131">判斷位址是否在將導致轉換成 managed 程式碼的存根內部。</span><span class="sxs-lookup"><span data-stu-id="6e602-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="6e602-132">ModifyLogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="6e602-133">設定指定之記錄參數的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="6e602-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="6e602-134">ReadMemory 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="6e602-135">從進程讀取記憶體。</span><span class="sxs-lookup"><span data-stu-id="6e602-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="6e602-136">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="6e602-137">設定指定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="6e602-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="6e602-138">ThreadForFiberCookie 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="6e602-139">已取代。</span><span class="sxs-lookup"><span data-stu-id="6e602-139">Deprecated.</span></span>|  
|[<span data-ttu-id="6e602-140">WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="6e602-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="6e602-141">將資料寫入進程中的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="6e602-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e602-142">備註</span><span class="sxs-lookup"><span data-stu-id="6e602-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e602-143">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="6e602-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e602-144">需求</span><span class="sxs-lookup"><span data-stu-id="6e602-144">Requirements</span></span>  
 <span data-ttu-id="6e602-145">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6e602-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e602-146">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e602-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e602-147">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e602-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e602-148">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e602-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e602-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e602-149">See also</span></span>

- [<span data-ttu-id="6e602-150">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="6e602-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
- [<span data-ttu-id="6e602-151">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="6e602-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
