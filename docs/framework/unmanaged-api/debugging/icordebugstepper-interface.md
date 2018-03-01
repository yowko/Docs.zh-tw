---
title: ICorDebugStepper Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 266e8c664ac7c5efa1b199efc522f0b890e38e3a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstepper-interface1"></a><span data-ttu-id="50980-102">ICorDebugStepper Interface1</span><span class="sxs-lookup"><span data-stu-id="50980-102">ICorDebugStepper Interface1</span></span>
<span data-ttu-id="50980-103">表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。</span><span class="sxs-lookup"><span data-stu-id="50980-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50980-104">方法</span><span class="sxs-lookup"><span data-stu-id="50980-104">Methods</span></span>  
  
|<span data-ttu-id="50980-105">方法</span><span class="sxs-lookup"><span data-stu-id="50980-105">Method</span></span>|<span data-ttu-id="50980-106">描述</span><span class="sxs-lookup"><span data-stu-id="50980-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50980-107">Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="50980-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="50980-108">造成這個`ICorDebugStepper`取消它所收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="50980-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="50980-109">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="50980-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="50980-110">取得值，指出是否此`ICorDebugStepper`目前正在執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="50980-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="50980-111">SetInterceptMask 方法</span><span class="sxs-lookup"><span data-stu-id="50980-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="50980-112">設定 CorDebugIntercept 值，指定類型，也就逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="50980-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="50980-113">SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="50980-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="50980-114">設定值，指出是否要呼叫[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)傳遞引數的值相對於原生程式碼或正在透過逐步執行方法的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="50980-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="50980-115">SetUnmappedStopMask 方法</span><span class="sxs-lookup"><span data-stu-id="50980-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="50980-116">設定 CorDebugUnmappedStop 值，指定執行將會暫止的未對應程式碼的類型。</span><span class="sxs-lookup"><span data-stu-id="50980-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="50980-117">Step 方法</span><span class="sxs-lookup"><span data-stu-id="50980-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="50980-118">造成這個`ICorDebugStepper`單一步驟其包含的執行緒，以及 （選擇性） 若要繼續逐步執行緒內呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="50980-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="50980-119">StepOut 方法</span><span class="sxs-lookup"><span data-stu-id="50980-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="50980-120">造成這個`ICorDebugStepper`逐步執行其包含的執行緒，以及完成時，目前的框架將控制權傳回給呼叫的框架。</span><span class="sxs-lookup"><span data-stu-id="50980-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="50980-121">StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="50980-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="50980-122">造成這個`ICorDebugStepper`單一步驟透過其包含的執行緒，並傳回當到達指定範圍的最後一個以外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="50980-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50980-123">備註</span><span class="sxs-lookup"><span data-stu-id="50980-123">Remarks</span></span>  
 <span data-ttu-id="50980-124">`ICorDebugStepper`介面有下列用途：</span><span class="sxs-lookup"><span data-stu-id="50980-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="50980-125">它會充當逐步執行 命令的發出和完成的命令之間的識別項。</span><span class="sxs-lookup"><span data-stu-id="50980-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="50980-126">它提供可執行的封裝所有的逐步執行的中央介面。</span><span class="sxs-lookup"><span data-stu-id="50980-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="50980-127">它提供方法來提前取消逐步執行的作業。</span><span class="sxs-lookup"><span data-stu-id="50980-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="50980-128">可以有一個以上的 stepper，每個執行緒。</span><span class="sxs-lookup"><span data-stu-id="50980-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="50980-129">比方說，可能會不進入函式時叫用中斷點，使用者可能想要開始新逐步執行的作業，該函式內。</span><span class="sxs-lookup"><span data-stu-id="50980-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="50980-130">這是由偵錯工具，以決定如何處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="50980-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="50980-131">偵錯工具可能想要取消原始逐步執行的作業或巢狀處理這兩項操作。</span><span class="sxs-lookup"><span data-stu-id="50980-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="50980-132">`ICorDebugStepper`介面支援這兩種選項。</span><span class="sxs-lookup"><span data-stu-id="50980-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="50980-133">如果 common language runtime (CLR) 會跨執行緒的封送處理呼叫，可能會在執行緒之間移轉 stepper。</span><span class="sxs-lookup"><span data-stu-id="50980-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50980-134">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="50980-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50980-135">需求</span><span class="sxs-lookup"><span data-stu-id="50980-135">Requirements</span></span>  
 <span data-ttu-id="50980-136">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50980-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50980-137">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="50980-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50980-138">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50980-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50980-139">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50980-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50980-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="50980-140">See Also</span></span>  
 [<span data-ttu-id="50980-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="50980-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
