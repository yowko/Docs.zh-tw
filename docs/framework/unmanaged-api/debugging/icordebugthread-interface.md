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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db322bbdc7293410968542d0d22c572edb87795a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184700"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="812a7-102">ICorDebugThread 介面</span><span class="sxs-lookup"><span data-stu-id="812a7-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="812a7-103">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="812a7-103">Represents a thread in a process.</span></span> <span data-ttu-id="812a7-104">`ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="812a7-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="812a7-105">方法</span><span class="sxs-lookup"><span data-stu-id="812a7-105">Methods</span></span>  
  
|<span data-ttu-id="812a7-106">方法</span><span class="sxs-lookup"><span data-stu-id="812a7-106">Method</span></span>|<span data-ttu-id="812a7-107">描述</span><span class="sxs-lookup"><span data-stu-id="812a7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="812a7-108">ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-108">ClearCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="812a7-109">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="812a7-109">This method is not implemented.</span></span> <span data-ttu-id="812a7-110">不要使用它。</span><span class="sxs-lookup"><span data-stu-id="812a7-110">Do not use it.</span></span>|  
|[<span data-ttu-id="812a7-111">CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-111">CreateEval Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createeval-method.md)|<span data-ttu-id="812a7-112">在此建立操作的 ICorDebugEval 物件`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-113">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-113">CreateStepper Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-createstepper-method.md)|<span data-ttu-id="812a7-114">建立 ICorDebugStepper 物件，可讓您逐步完成每個在此使用中畫面格`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-115">EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-115">EnumerateChains Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-enumeratechains-method.md)|<span data-ttu-id="812a7-116">ICorDebugChainEnum 列舉值，其中包含所有的堆疊鏈結，在此取得的介面指標`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-117">GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-117">GetActiveChain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactivechain-method.md)|<span data-ttu-id="812a7-118">取得作用中的 ICorDebugChain 的介面指標，此`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-119">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-119">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getactiveframe-method.md)|<span data-ttu-id="812a7-120">取得作用中的 ICorDebugFrame 的介面指標，此`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-121">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-121">GetAppDomain Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getappdomain-method.md)|<span data-ttu-id="812a7-122">取得應用程式定義域的介面指標，這個`ICorDebugThread`目前正在執行。</span><span class="sxs-lookup"><span data-stu-id="812a7-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="812a7-123">GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-123">GetCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="812a7-124">ICorDebugValue 物件，表示目前所擲回例外狀況的 managed 程式碼中取得的介面指標。</span><span class="sxs-lookup"><span data-stu-id="812a7-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="812a7-125">GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-125">GetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getdebugstate-method.md)|<span data-ttu-id="812a7-126">取得描述目前的偵錯狀態，這個 CorDebugThreadState 值`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-127">GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-127">GetHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-gethandle-method.md)|<span data-ttu-id="812a7-128">取得目前的控制代碼的作用中的部分`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-129">GetID 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-129">GetID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getid-method.md)|<span data-ttu-id="812a7-130">取得目前的作業系統識別項的使用中的這部分`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-131">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-131">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getobject-method.md)|<span data-ttu-id="812a7-132">取得 common language runtime (CLR) 執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="812a7-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="812a7-133">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-133">GetProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getprocess-method.md)|<span data-ttu-id="812a7-134">這個程序中取得的介面指標`ICorDebugThread`構成部分。</span><span class="sxs-lookup"><span data-stu-id="812a7-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="812a7-135">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-135">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getregisterset-method.md)|<span data-ttu-id="812a7-136">取得與此相關聯的暫存器集的介面指標`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-137">GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-137">GetUserState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)|<span data-ttu-id="812a7-138">取得描述這個的目前狀態的 CorDebugUserState 值的位元組合`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="812a7-139">SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="812a7-139">SetDebugState Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)|<span data-ttu-id="812a7-140">設定的位元組合`CorDebugThreadState`值，描述偵錯的狀態這`ICorDebugThread`。</span><span class="sxs-lookup"><span data-stu-id="812a7-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="812a7-141">備註</span><span class="sxs-lookup"><span data-stu-id="812a7-141">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="812a7-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="812a7-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="812a7-143">需求</span><span class="sxs-lookup"><span data-stu-id="812a7-143">Requirements</span></span>  
 <span data-ttu-id="812a7-144">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="812a7-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="812a7-145">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="812a7-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="812a7-146">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="812a7-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="812a7-147">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="812a7-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="812a7-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="812a7-148">See also</span></span>

- [<span data-ttu-id="812a7-149">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="812a7-149">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
