---
title: ICorDebugThread 介面
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: c7333f4210d0a2ec4ff71a0fac0ea00068fecc57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133502"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="ea340-102">ICorDebugThread 介面</span><span class="sxs-lookup"><span data-stu-id="ea340-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="ea340-103">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ea340-103">Represents a thread in a process.</span></span> <span data-ttu-id="ea340-104">`ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="ea340-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea340-105">方法</span><span class="sxs-lookup"><span data-stu-id="ea340-105">Methods</span></span>  
  
|<span data-ttu-id="ea340-106">方法</span><span class="sxs-lookup"><span data-stu-id="ea340-106">Method</span></span>|<span data-ttu-id="ea340-107">描述</span><span class="sxs-lookup"><span data-stu-id="ea340-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea340-108">ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="ea340-109">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="ea340-109">This method is not implemented.</span></span> <span data-ttu-id="ea340-110">不要使用它。</span><span class="sxs-lookup"><span data-stu-id="ea340-110">Do not use it.</span></span>|  
|[<span data-ttu-id="ea340-111">CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="ea340-112">建立可在此 `ICorDebugThread`上運作的 ICorDebugEval 物件。</span><span class="sxs-lookup"><span data-stu-id="ea340-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-113">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="ea340-114">建立 ICorDebugStepper 物件，允許在此 `ICorDebugThread`中逐步執行使用中的框架。</span><span class="sxs-lookup"><span data-stu-id="ea340-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-115">EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="ea340-116">取得 ICorDebugChainEnum 列舉值的介面指標，其中包含此 `ICorDebugThread`中的所有堆疊鏈。</span><span class="sxs-lookup"><span data-stu-id="ea340-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-117">GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="ea340-118">取得此 `ICorDebugThread`上作用中 ICorDebugChain 的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea340-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-119">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="ea340-120">取得此 `ICorDebugThread`上作用中 ICorDebugFrame 的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea340-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-121">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="ea340-122">取得此 `ICorDebugThread` 目前執行所在之應用程式域的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea340-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="ea340-123">GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="ea340-124">取得 ICorDebugValue 物件的介面指標，代表目前由 managed 程式碼擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ea340-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="ea340-125">GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="ea340-126">取得描述此 `ICorDebugThread`目前的 debug 狀態的 CorDebugThreadState 值。</span><span class="sxs-lookup"><span data-stu-id="ea340-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-127">GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="ea340-128">取得此 `ICorDebugThread`之使用中部分的目前控制碼。</span><span class="sxs-lookup"><span data-stu-id="ea340-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-129">GetID 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="ea340-130">取得此 `ICorDebugThread`之使用中部分的目前作業系統識別碼。</span><span class="sxs-lookup"><span data-stu-id="ea340-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-131">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="ea340-132">取得 common language runtime （CLR）執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea340-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="ea340-133">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="ea340-134">取得此 `ICorDebugThread` 構成元件之進程的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea340-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="ea340-135">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="ea340-136">取得與此 `ICorDebugThread`相關聯之緩存集的介面指標。</span><span class="sxs-lookup"><span data-stu-id="ea340-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-137">GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="ea340-138">取得 CorDebugUserState 值的位元組合，這個組合會描述這個 `ICorDebugThread`的目前狀態。</span><span class="sxs-lookup"><span data-stu-id="ea340-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="ea340-139">SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="ea340-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="ea340-140">設定 `CorDebugThreadState` 值的位元組合，以描述此 `ICorDebugThread`的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="ea340-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea340-141">備註</span><span class="sxs-lookup"><span data-stu-id="ea340-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea340-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="ea340-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea340-143">需求</span><span class="sxs-lookup"><span data-stu-id="ea340-143">Requirements</span></span>  
 <span data-ttu-id="ea340-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ea340-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea340-145">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea340-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea340-146">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea340-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea340-147">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea340-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea340-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="ea340-148">See also</span></span>

- [<span data-ttu-id="ea340-149">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="ea340-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
