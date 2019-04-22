---
title: ICorDebugStepper 介面
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212514"
---
# <a name="icordebugstepper-interface"></a><span data-ttu-id="a042c-102">ICorDebugStepper 介面</span><span class="sxs-lookup"><span data-stu-id="a042c-102">ICorDebugStepper Interface</span></span>
<span data-ttu-id="a042c-103">表示偵錯工具在程式碼執行作業中所執行的步驟，做為命令的發出和完成之間的識別項，並可提供方法來取消步驟。</span><span class="sxs-lookup"><span data-stu-id="a042c-103">Represents a step in code execution that is performed by a debugger, serves as an identifier between the issuance and completion of a command, and provides a way to cancel a step.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a042c-104">方法</span><span class="sxs-lookup"><span data-stu-id="a042c-104">Methods</span></span>  
  
|<span data-ttu-id="a042c-105">方法</span><span class="sxs-lookup"><span data-stu-id="a042c-105">Method</span></span>|<span data-ttu-id="a042c-106">描述</span><span class="sxs-lookup"><span data-stu-id="a042c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a042c-107">Deactivate 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-107">Deactivate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|<span data-ttu-id="a042c-108">這會導致`ICorDebugStepper`取消它收到的最後一個步驟命令。</span><span class="sxs-lookup"><span data-stu-id="a042c-108">Causes this `ICorDebugStepper` to cancel the last step command it received.</span></span>|  
|[<span data-ttu-id="a042c-109">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|<span data-ttu-id="a042c-110">取得值，指出是否此`ICorDebugStepper`目前正在執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="a042c-110">Gets a value that indicates whether this `ICorDebugStepper` is currently executing a step.</span></span>|  
|[<span data-ttu-id="a042c-111">SetInterceptMask 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-111">SetInterceptMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|<span data-ttu-id="a042c-112">設定 CorDebugIntercept 值，指定 逐步執行的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="a042c-112">Sets a CorDebugIntercept value that specifies the types of code that are stepped into.</span></span>|  
|[<span data-ttu-id="a042c-113">SetRangeIL 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-113">SetRangeIL Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|<span data-ttu-id="a042c-114">設定值，這個值，指出是否呼叫[icordebugstepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)傳遞引數的值相對於原生程式碼或為正在逐步執行方法的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a042c-114">Sets a value that indicates whether calls to [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) pass argument values relative to the native code or to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>|  
|[<span data-ttu-id="a042c-115">SetUnmappedStopMask 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-115">SetUnmappedStopMask Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|<span data-ttu-id="a042c-116">設定 CorDebugUnmappedStop 值，指定執行將會暫止未對應的程式碼的類型。</span><span class="sxs-lookup"><span data-stu-id="a042c-116">Sets a CorDebugUnmappedStop value that specifies the type of unmapped code in which execution will halt.</span></span>|  
|[<span data-ttu-id="a042c-117">Step 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-117">Step Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|<span data-ttu-id="a042c-118">這會導致`ICorDebugStepper`單一步驟及其包含的執行緒，以及 （選擇性） 若要繼續單一位逐步執行會在執行緒內呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="a042c-118">Causes this `ICorDebugStepper` to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>|  
|[<span data-ttu-id="a042c-119">StepOut 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-119">StepOut Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|<span data-ttu-id="a042c-120">這會導致`ICorDebugStepper`逐步執行其包含的執行緒，以及完成時，目前的框架將控制權傳回給呼叫端的框架。</span><span class="sxs-lookup"><span data-stu-id="a042c-120">Causes this `ICorDebugStepper` to single-step through its containing thread, and to complete when the current frame returns control to the calling frame.</span></span>|  
|[<span data-ttu-id="a042c-121">StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="a042c-121">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|<span data-ttu-id="a042c-122">這會導致`ICorDebugStepper`單一步驟透過其包含的執行緒，並傳回當到達指定範圍的最後一個以外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="a042c-122">Causes this `ICorDebugStepper` to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a042c-123">備註</span><span class="sxs-lookup"><span data-stu-id="a042c-123">Remarks</span></span>  
 <span data-ttu-id="a042c-124">`ICorDebugStepper`介面會提供下列用途：</span><span class="sxs-lookup"><span data-stu-id="a042c-124">The `ICorDebugStepper` interface serves the following purposes:</span></span>  
  
-   <span data-ttu-id="a042c-125">它會充當之間逐步執行 命令發出和完成該命令的識別項。</span><span class="sxs-lookup"><span data-stu-id="a042c-125">It acts as an identifier between a step command that is issued and the completion of that command.</span></span>  
  
-   <span data-ttu-id="a042c-126">它提供可執行的封裝所有逐步執行的中央介面。</span><span class="sxs-lookup"><span data-stu-id="a042c-126">It provides a central interface to encapsulate all the stepping that can be performed.</span></span>  
  
-   <span data-ttu-id="a042c-127">它提供方法來提前取消 逐步執行的作業。</span><span class="sxs-lookup"><span data-stu-id="a042c-127">It provides a way to prematurely cancel a stepping operation.</span></span>  
  
 <span data-ttu-id="a042c-128">可以有一個以上的步進，每個執行緒。</span><span class="sxs-lookup"><span data-stu-id="a042c-128">There can be more than one stepper per thread.</span></span> <span data-ttu-id="a042c-129">比方說，可能會叫用中斷點時不進入函式，使用者可能想要開始新的逐步執行作業，在此函式。</span><span class="sxs-lookup"><span data-stu-id="a042c-129">For example, a breakpoint may be hit while stepping over a function, and the user may wish to start a new stepping operation inside that function.</span></span> <span data-ttu-id="a042c-130">這是由偵錯工具來判斷如何處理這種情況。</span><span class="sxs-lookup"><span data-stu-id="a042c-130">It is up to the debugger to determine how to handle this situation.</span></span> <span data-ttu-id="a042c-131">偵錯工具可能會想要取消原始逐步執行的作業，或巢狀化的兩項作業。</span><span class="sxs-lookup"><span data-stu-id="a042c-131">The debugger may want to cancel the original stepping operation or nest the two operations.</span></span> <span data-ttu-id="a042c-132">`ICorDebugStepper`介面支援這兩種選項。</span><span class="sxs-lookup"><span data-stu-id="a042c-132">The `ICorDebugStepper` interface supports both choices.</span></span>  
  
 <span data-ttu-id="a042c-133">如果 common language runtime (CLR) 會跨執行緒與封送處理呼叫，可能會在執行緒之間移轉步進。</span><span class="sxs-lookup"><span data-stu-id="a042c-133">A stepper may migrate between threads if the common language runtime (CLR) makes a cross-threaded, marshaled call.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a042c-134">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="a042c-134">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a042c-135">需求</span><span class="sxs-lookup"><span data-stu-id="a042c-135">Requirements</span></span>  
 <span data-ttu-id="a042c-136">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a042c-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a042c-137">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a042c-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a042c-138">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a042c-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a042c-139">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a042c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a042c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a042c-140">See also</span></span>

- [<span data-ttu-id="a042c-141">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="a042c-141">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
