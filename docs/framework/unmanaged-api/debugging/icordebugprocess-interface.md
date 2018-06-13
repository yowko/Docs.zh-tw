---
title: ICorDebugProcess Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06e4e3854a850c9639e93c8db2ec8ccd567b242b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423165"
---
# <a name="icordebugprocess-interface1"></a><span data-ttu-id="1938b-102">ICorDebugProcess Interface1</span><span class="sxs-lookup"><span data-stu-id="1938b-102">ICorDebugProcess Interface1</span></span>
<span data-ttu-id="1938b-103">表示執行 Managed 程式碼的處理序。</span><span class="sxs-lookup"><span data-stu-id="1938b-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="1938b-104">這個介面是 ICorDebugController 的子類別。</span><span class="sxs-lookup"><span data-stu-id="1938b-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1938b-105">方法</span><span class="sxs-lookup"><span data-stu-id="1938b-105">Methods</span></span>  
  
|<span data-ttu-id="1938b-106">方法</span><span class="sxs-lookup"><span data-stu-id="1938b-106">Method</span></span>|<span data-ttu-id="1938b-107">描述</span><span class="sxs-lookup"><span data-stu-id="1938b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1938b-108">ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="1938b-109">清除指定的執行緒上目前的 unmanaged 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1938b-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="1938b-110">EnableLogMessages 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-110">EnableLogMessages Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="1938b-111">啟用和停用記錄檔訊息傳送給偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="1938b-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="1938b-112">EnumerateAppDomains 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-112">EnumerateAppDomains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="1938b-113">列舉中的所有應用程式網域的程序。</span><span class="sxs-lookup"><span data-stu-id="1938b-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="1938b-114">EnumerateObjects 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-114">EnumerateObjects Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="1938b-115">未實作。</span><span class="sxs-lookup"><span data-stu-id="1938b-115">Not implemented.</span></span>|  
|[<span data-ttu-id="1938b-116">GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-116">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethandle-method.md)|<span data-ttu-id="1938b-117">取得處理程序的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1938b-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="1938b-118">GetHelperThreadID 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-118">GetHelperThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="1938b-119">取得偵錯工具的內部協助程式執行緒的作業系統 (OS) 執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="1938b-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="1938b-120">GetID 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-120">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getid-method.md)|<span data-ttu-id="1938b-121">取得處理序的作業系統 (OS) 識別碼。</span><span class="sxs-lookup"><span data-stu-id="1938b-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="1938b-122">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-122">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getobject-method.md)|<span data-ttu-id="1938b-123">未實作。</span><span class="sxs-lookup"><span data-stu-id="1938b-123">Not implemented.</span></span>|  
|[<span data-ttu-id="1938b-124">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-124">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthread-method.md)|<span data-ttu-id="1938b-125">取得具有指定的作業系統執行緒的 ICorDebugThread 執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="1938b-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="1938b-126">GetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-126">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="1938b-127">取得指定執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="1938b-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1938b-128">IsOSSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-128">IsOSSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-isossuspended-method.md)|<span data-ttu-id="1938b-129">判斷執行緒是否已暫止偵錯工具停止處理序的結果。</span><span class="sxs-lookup"><span data-stu-id="1938b-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="1938b-130">IsTransitionStub 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-130">IsTransitionStub Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="1938b-131">判斷是否會導致轉換為 managed 程式碼的虛設常式內位址。</span><span class="sxs-lookup"><span data-stu-id="1938b-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="1938b-132">ModifyLogSwitch 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-132">ModifyLogSwitch Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="1938b-133">設定參數，因為指定的記錄檔的嚴重性層級。</span><span class="sxs-lookup"><span data-stu-id="1938b-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="1938b-134">ReadMemory 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-134">ReadMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-readmemory-method.md)|<span data-ttu-id="1938b-135">處理程序會讀取記憶體。</span><span class="sxs-lookup"><span data-stu-id="1938b-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="1938b-136">SetThreadContext 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-136">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="1938b-137">設定指定之執行緒的內容。</span><span class="sxs-lookup"><span data-stu-id="1938b-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="1938b-138">ThreadForFiberCookie 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-138">ThreadForFiberCookie Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="1938b-139">已取代。</span><span class="sxs-lookup"><span data-stu-id="1938b-139">Deprecated.</span></span>|  
|[<span data-ttu-id="1938b-140">WriteMemory 方法</span><span class="sxs-lookup"><span data-stu-id="1938b-140">WriteMemory Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-writememory-method.md)|<span data-ttu-id="1938b-141">將資料寫入的處理序中的記憶體區域。</span><span class="sxs-lookup"><span data-stu-id="1938b-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1938b-142">備註</span><span class="sxs-lookup"><span data-stu-id="1938b-142">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1938b-143">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="1938b-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1938b-144">需求</span><span class="sxs-lookup"><span data-stu-id="1938b-144">Requirements</span></span>  
 <span data-ttu-id="1938b-145">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1938b-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1938b-146">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1938b-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1938b-147">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1938b-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1938b-148">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1938b-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1938b-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1938b-149">See Also</span></span>  
 [<span data-ttu-id="1938b-150">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="1938b-150">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="1938b-151">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="1938b-151">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
