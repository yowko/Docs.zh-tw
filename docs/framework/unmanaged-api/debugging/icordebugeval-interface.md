---
title: ICorDebugEval 介面
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: c9e2dc95bf78d95e5d608a8ce6e9462345c20a07
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788737"
---
# <a name="icordebugeval-interface"></a><span data-ttu-id="b4ae6-102">ICorDebugEval 介面</span><span class="sxs-lookup"><span data-stu-id="b4ae6-102">ICorDebugEval Interface</span></span>

<span data-ttu-id="b4ae6-103">提供方法讓偵錯工具執行所偵錯的程式碼內容中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-103">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4ae6-104">方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-104">Methods</span></span>  
  
|<span data-ttu-id="b4ae6-105">方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-105">Method</span></span>|<span data-ttu-id="b4ae6-106">描述</span><span class="sxs-lookup"><span data-stu-id="b4ae6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4ae6-107">Abort 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-107">Abort Method</span></span>](icordebugeval-abort-method.md)|<span data-ttu-id="b4ae6-108">中止此 `ICorDebugEval` 物件目前正在執行的計算。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-108">Aborts the computation this `ICorDebugEval` object is currently performing.</span></span>|  
|[<span data-ttu-id="b4ae6-109">CallFunction 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-109">CallFunction Method</span></span>](icordebugeval-callfunction-method.md)|<span data-ttu-id="b4ae6-110">設定對指定函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-110">Sets up a call to the specified function.</span></span> <span data-ttu-id="b4ae6-111">（在 .NET Framework 版本2.0 中已過時; 請改用[ICorDebugEval2：： CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) 。）</span><span class="sxs-lookup"><span data-stu-id="b4ae6-111">(Obsolete in the .NET Framework version 2.0; use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.)</span></span>|  
|[<span data-ttu-id="b4ae6-112">CreateValue 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-112">CreateValue Method</span></span>](icordebugeval-createvalue-method.md)|<span data-ttu-id="b4ae6-113">取得指定類型之 "ICorDebugValue" 物件的介面指標，其初始值為零或 null。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-113">Gets an interface pointer to an "ICorDebugValue" object of the specified type, with an initial value of zero or null.</span></span> <span data-ttu-id="b4ae6-114">（在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2：： CreateValueForType](icordebugeval2-createvaluefortype-method.md) ）。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-114">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.)</span></span>|  
|[<span data-ttu-id="b4ae6-115">GetResult 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-115">GetResult Method</span></span>](icordebugeval-getresult-method.md)|<span data-ttu-id="b4ae6-116">取得包含評估結果之 `ICorDebugValue` 的介面指標。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-116">Gets an interface pointer to an `ICorDebugValue` that contains the results of the evaluation.</span></span>|  
|[<span data-ttu-id="b4ae6-117">GetThread 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-117">GetThread Method</span></span>](icordebugeval-getthread-method.md)|<span data-ttu-id="b4ae6-118">取得此評估正在執行或將執行之 "ICorDebugThread" 的介面指標。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-118">Gets an interface pointer to the "ICorDebugThread" where this evaluation is executing or will execute.</span></span>|  
|[<span data-ttu-id="b4ae6-119">IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-119">IsActive Method</span></span>](icordebugeval-isactive-method.md)|<span data-ttu-id="b4ae6-120">取得值，指出這個 `ICorDebugEval` 物件目前是否正在執行。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-120">Gets a value that indicates whether this `ICorDebugEval` object is currently executing.</span></span>|  
|[<span data-ttu-id="b4ae6-121">NewArray 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-121">NewArray Method</span></span>](icordebugeval-newarray-method.md)|<span data-ttu-id="b4ae6-122">配置指定之元素類型和維度的新陣列。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-122">Allocates a new array of the specified element type and dimensions.</span></span> <span data-ttu-id="b4ae6-123">（在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2：： NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) ）。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-123">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.)</span></span>|  
|[<span data-ttu-id="b4ae6-124">NewObject 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-124">NewObject Method</span></span>](icordebugeval-newobject-method.md)|<span data-ttu-id="b4ae6-125">配置新的物件實例，並呼叫指定的函式方法。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-125">Allocates a new object instance and calls the specified constructor method.</span></span> <span data-ttu-id="b4ae6-126">（在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2：： NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) ）。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-126">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.)</span></span>|  
|[<span data-ttu-id="b4ae6-127">NewObjectNoConstructor 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-127">NewObjectNoConstructor Method</span></span>](icordebugeval-newobjectnoconstructor-method.md)|<span data-ttu-id="b4ae6-128">配置指定類型的新物件實例，而不會嘗試呼叫函式方法。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-128">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span> <span data-ttu-id="b4ae6-129">（在 .NET Framework 2.0 中已過時; 請改用[ICorDebugEval2：： NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) ）。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-129">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.)</span></span>|  
|[<span data-ttu-id="b4ae6-130">NewString 方法</span><span class="sxs-lookup"><span data-stu-id="b4ae6-130">NewString Method</span></span>](icordebugeval-newstring-method.md)|<span data-ttu-id="b4ae6-131">使用指定的內容，配置新的字串物件。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-131">Allocates a new string object with the specified contents.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4ae6-132">備註</span><span class="sxs-lookup"><span data-stu-id="b4ae6-132">Remarks</span></span>  
 <span data-ttu-id="b4ae6-133">在用來執行評估的特定執行緒內容中，會建立 `ICorDebugEval` 物件。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-133">An `ICorDebugEval` object is created in the context of a specific thread that is used to perform the evaluations.</span></span> <span data-ttu-id="b4ae6-134">指定評估中使用的所有物件和類型都必須位於相同的應用程式域中。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-134">All objects and types used in a given evaluation must reside within the same application domain.</span></span> <span data-ttu-id="b4ae6-135">該應用程式域不需要與執行緒目前的應用程式域相同。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-135">That application domain need not be the same as the current application domain of the thread.</span></span> <span data-ttu-id="b4ae6-136">可以嵌套評估。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-136">Evaluations can be nested.</span></span>  
  
 <span data-ttu-id="b4ae6-137">在偵錯工具呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)之後，評估的作業才會完成，然後接收[ICorDebugManagedCallback：： EvalComplete](icordebugmanagedcallback-evalcomplete-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-137">The evaluation's operations do not complete until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md), and then receives an [ICorDebugManagedCallback::EvalComplete](icordebugmanagedcallback-evalcomplete-method.md) callback.</span></span> <span data-ttu-id="b4ae6-138">如果您需要使用評估功能而不允許其他執行緒執行，請在呼叫[ICorDebugController：： Continue](icordebugcontroller-continue-method.md)之前，使用[ICorDebugController：： SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md)或[ICorDebugController：： Stop](icordebugcontroller-stop-method.md)來暫停執行緒。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-138">If you need to use the evaluation functionality without allowing other threads to run, suspend the threads by using either [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) or [ICorDebugController::Stop](icordebugcontroller-stop-method.md) before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
 <span data-ttu-id="b4ae6-139">因為使用者程式碼正在進行評估，所以可能會發生任何 debug 事件，包括類別載入和中斷點。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-139">Because user code is running when the evaluation is in progress, any debug events can occur, including class loads and breakpoints.</span></span> <span data-ttu-id="b4ae6-140">偵錯工具會如往常般接收這些事件的回呼。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-140">The debugger will receive callbacks, as normal, for these events.</span></span> <span data-ttu-id="b4ae6-141">評估的狀態將會視為一般程式狀態檢查的一部分。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-141">The state of the evaluation will be seen as part of the inspection of the normal program state.</span></span> <span data-ttu-id="b4ae6-142">堆疊鏈會是 `CHAIN_FUNC_EVAL` 鏈（請參閱 "CorDebugStepReason" 列舉和[ICorDebugChain：： GetReason](icordebugchain-getreason-method.md)方法）。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-142">The stack chain will be a `CHAIN_FUNC_EVAL` chain (see the "CorDebugStepReason" enumeration and the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method).</span></span> <span data-ttu-id="b4ae6-143">完整的偵錯工具 API 會繼續正常運作。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-143">The full debugger API will continue to operate as normal.</span></span>  
  
 <span data-ttu-id="b4ae6-144">如果發生鎖死或無限迴圈的情況，使用者程式碼可能永遠不會完成。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-144">If a deadlocked or infinite looping situation arises, the user code may never complete.</span></span> <span data-ttu-id="b4ae6-145">在這種情況下，您必須先呼叫[ICorDebugEval：： Abort](icordebugeval-abort-method.md) ，才能繼續執行程式。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-145">In such a case, you must call [ICorDebugEval::Abort](icordebugeval-abort-method.md) before resuming the program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4ae6-146">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-146">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4ae6-147">需求</span><span class="sxs-lookup"><span data-stu-id="b4ae6-147">Requirements</span></span>  
 <span data-ttu-id="b4ae6-148">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b4ae6-148">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4ae6-149">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4ae6-149">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4ae6-150">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4ae6-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4ae6-151">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4ae6-151">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4ae6-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4ae6-152">See also</span></span>

- [<span data-ttu-id="b4ae6-153">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b4ae6-153">Debugging Interfaces</span></span>](debugging-interfaces.md)
