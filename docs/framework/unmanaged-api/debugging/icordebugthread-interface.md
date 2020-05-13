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
ms.openlocfilehash: edcc0ebcadc1bd95574b0276bfd0e2d42e5474fd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379825"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="5f8cc-102">ICorDebugThread 介面</span><span class="sxs-lookup"><span data-stu-id="5f8cc-102">ICorDebugThread Interface</span></span>
<span data-ttu-id="5f8cc-103">表示處理序中的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-103">Represents a thread in a process.</span></span> <span data-ttu-id="5f8cc-104">`ICorDebugThread` 執行個體的存留期與其所表示的執行緒之存留期相同。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f8cc-105">方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-105">Methods</span></span>  
  
|<span data-ttu-id="5f8cc-106">方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-106">Method</span></span>|<span data-ttu-id="5f8cc-107">描述</span><span class="sxs-lookup"><span data-stu-id="5f8cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f8cc-108">ClearCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="5f8cc-109">這個方法尚未實作。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-109">This method is not implemented.</span></span> <span data-ttu-id="5f8cc-110">不要使用它。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-110">Do not use it.</span></span>|  
|[<span data-ttu-id="5f8cc-111">CreateEval 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="5f8cc-112">建立可在這個上操作的 ICorDebugEval 物件 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-113">CreateStepper 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="5f8cc-114">建立 ICorDebugStepper 物件，允許在這個中逐步執行使用中的框架 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-115">EnumerateChains 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="5f8cc-116">取得 ICorDebugChainEnum 列舉值的介面指標，其中包含這個中的所有堆疊鏈 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-117">GetActiveChain 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="5f8cc-118">取得這個上作用中 ICorDebugChain 的介面指標 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-119">GetActiveFrame 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="5f8cc-120">取得這個上作用中 ICorDebugFrame 的介面指標 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-121">GetAppDomain 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="5f8cc-122">取得此目前執行所在之應用程式域的介面指標 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="5f8cc-123">GetCurrentException 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="5f8cc-124">取得 ICorDebugValue 物件的介面指標，代表目前由 managed 程式碼擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="5f8cc-125">GetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="5f8cc-126">取得 CorDebugThreadState 值，描述這個的目前的偵錯工具狀態 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-127">GetHandle 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="5f8cc-128">取得這個之使用中部分的目前控制碼 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-129">GetID 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="5f8cc-130">取得這個之使用中部分的目前作業系統識別碼 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-131">GetObject 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="5f8cc-132">取得 common language runtime （CLR）執行緒的介面指標。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="5f8cc-133">GetProcess 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="5f8cc-134">取得此組成元件之進程的介面指標 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="5f8cc-135">GetRegisterSet 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="5f8cc-136">取得與這個相關聯之緩存集的介面指標 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-137">GetUserState 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="5f8cc-138">取得 CorDebugUserState 值的位元組合，這個組合會描述這個的目前狀態 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="5f8cc-139">SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="5f8cc-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="5f8cc-140">設定值的位元組合 `CorDebugThreadState` ，這個組合會描述這個的偵錯工具狀態 `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f8cc-141">備註</span><span class="sxs-lookup"><span data-stu-id="5f8cc-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f8cc-142">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f8cc-143">需求</span><span class="sxs-lookup"><span data-stu-id="5f8cc-143">Requirements</span></span>  
 <span data-ttu-id="5f8cc-144">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f8cc-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f8cc-145">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f8cc-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f8cc-146">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f8cc-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f8cc-147">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f8cc-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f8cc-148">請參閱</span><span class="sxs-lookup"><span data-stu-id="5f8cc-148">See also</span></span>

- [<span data-ttu-id="5f8cc-149">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="5f8cc-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
