---
title: "FunctionTailcall3 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionTailcall3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionTailcall3
helpviewer_keywords: FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5d274c966a345e0e2984018bcd8aa1e2dade03b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="ad423-102">FunctionTailcall3 函式</span><span class="sxs-lookup"><span data-stu-id="ad423-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="ad423-103">通知分析工具目前執行函式即將執行對另一個函式的 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="ad423-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad423-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad423-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad423-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad423-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="ad423-106">[in]目前執行的函式進行呼叫的結尾的識別項。</span><span class="sxs-lookup"><span data-stu-id="ad423-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad423-107">備註</span><span class="sxs-lookup"><span data-stu-id="ad423-107">Remarks</span></span>  
 <span data-ttu-id="ad423-108">`FunctionTailcall3`正在呼叫函式時，回呼函式會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="ad423-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="ad423-109">使用[icorprofilerinfo3:: Setenterleavefunctionhooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。</span><span class="sxs-lookup"><span data-stu-id="ad423-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ad423-110">`FunctionTailcall3`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="ad423-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="ad423-111">實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="ad423-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="ad423-112">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="ad423-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="ad423-113">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="ad423-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="ad423-114">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="ad423-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ad423-115">實作`FunctionTailcall3`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="ad423-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="ad423-116">實作不應嘗試回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="ad423-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ad423-117">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionTailcall3`傳回。</span><span class="sxs-lookup"><span data-stu-id="ad423-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="ad423-118">`FunctionTailcall3`函式不能呼叫 managed 程式碼或以任何方式導致受管理的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="ad423-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad423-119">需求</span><span class="sxs-lookup"><span data-stu-id="ad423-119">Requirements</span></span>  
 <span data-ttu-id="ad423-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad423-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad423-121">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="ad423-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ad423-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad423-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad423-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad423-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad423-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad423-124">See Also</span></span>  
 [<span data-ttu-id="ad423-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ad423-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="ad423-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ad423-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="ad423-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ad423-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="ad423-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ad423-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="ad423-129">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="ad423-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="ad423-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="ad423-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="ad423-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ad423-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="ad423-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="ad423-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="ad423-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="ad423-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="ad423-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ad423-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
