---
title: ICorDebugThread Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread
helpviewer_keywords: ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25b5c8f0720402cce56c69394c6fbe2fb70a6177
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread-interface1"></a><span data-ttu-id="e8236-102">ICorDebugThread Interface1</span><span class="sxs-lookup"><span data-stu-id="e8236-102">ICorDebugThread Interface1</span></span>
<span data-ttu-id="e8236-103">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="e8236-103">Represents a thread in a process.</span></span> <span data-ttu-id="e8236-104">`ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="e8236-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8236-105">方法</span><span class="sxs-lookup"><span data-stu-id="e8236-105">Methods</span></span>  
  
|<span data-ttu-id="e8236-106">方法</span><span class="sxs-lookup"><span data-stu-id="e8236-106">Method</span></span>|<span data-ttu-id="e8236-107">說明</span><span class="sxs-lookup"><span data-stu-id="e8236-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8236-108">ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="e8236-109">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="e8236-109">This method is not implemented.</span></span> <span data-ttu-id="e8236-110">不要使用它。</span><span class="sxs-lookup"><span data-stu-id="e8236-110">Do not use it.</span></span>|  
|[<span data-ttu-id="e8236-111">CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="e8236-112">在此建立操作的 ICorDebugEval 物件`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-113">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="e8236-114">建立可讓您逐步執行在此使用中框架的 ICorDebugStepper 物件`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-115">EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="e8236-116">ICorDebugChainEnum 列舉值，其中包含所有堆疊鏈結，在此取得的介面指標`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-117">GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="e8236-118">取得 active ICorDebugChain 介面指標上`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-119">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="e8236-120">取得 active ICorDebugFrame 介面指標上`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-121">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="e8236-122">取得應用程式定義域的介面指標，這個`ICorDebugThread`目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="e8236-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="e8236-123">GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="e8236-124">ICorDebugValue 物件，代表目前正在擲回例外狀況的 managed 程式碼中取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e8236-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="e8236-125">GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="e8236-126">取得描述目前的偵錯狀態，這個 CorDebugThreadState 值`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-127">GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="e8236-128">取得目前的控制代碼的使用中的部分`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-129">GetID 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="e8236-130">取得目前的作業系統識別項的使用中的部分`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-131">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="e8236-132">取得 common language runtime (CLR) 執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e8236-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="e8236-133">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="e8236-134">取得這個處理序的介面指標`ICorDebugThread`的一部分。</span><span class="sxs-lookup"><span data-stu-id="e8236-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="e8236-135">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="e8236-136">取得與此相關聯的暫存器集合的介面指標`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-137">GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="e8236-138">取得描述目前的狀態 CorDebugUserState 值的位元組合`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="e8236-139">SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="e8236-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="e8236-140">設定的位元組合`CorDebugThreadState`描述的偵錯的狀態，這個值`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="e8236-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8236-141">備註</span><span class="sxs-lookup"><span data-stu-id="e8236-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8236-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="e8236-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8236-143">需求</span><span class="sxs-lookup"><span data-stu-id="e8236-143">Requirements</span></span>  
 <span data-ttu-id="e8236-144">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e8236-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8236-145">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8236-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8236-146">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8236-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8236-147">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8236-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8236-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8236-148">See Also</span></span>  
 [<span data-ttu-id="e8236-149">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="e8236-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
