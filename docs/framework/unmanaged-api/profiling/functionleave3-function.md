---
title: "FunctionLeave3 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave3
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave3
helpviewer_keywords: FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 11aa67a03cfb88910704c0f1d2f586f8dbed7d52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave3-function"></a><span data-ttu-id="edad0-102">FunctionLeave3 函式</span><span class="sxs-lookup"><span data-stu-id="edad0-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="edad0-103">通知分析工具會從函式傳回控制項。</span><span class="sxs-lookup"><span data-stu-id="edad0-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edad0-104">語法</span><span class="sxs-lookup"><span data-stu-id="edad0-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edad0-105">參數</span><span class="sxs-lookup"><span data-stu-id="edad0-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="edad0-106">[in]控制項會傳回函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="edad0-106">[in] The identifier of the function from which control is returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edad0-107">備註</span><span class="sxs-lookup"><span data-stu-id="edad0-107">Remarks</span></span>  
 <span data-ttu-id="edad0-108">`FunctionLeave3`回呼函式會通知分析工具函式呼叫，但不支援傳回值檢查。</span><span class="sxs-lookup"><span data-stu-id="edad0-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="edad0-109">使用[icorprofilerinfo3:: Setenterleavefunctionhooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。</span><span class="sxs-lookup"><span data-stu-id="edad0-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="edad0-110">`FunctionLeave3`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="edad0-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="edad0-111">實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="edad0-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="edad0-112">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="edad0-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="edad0-113">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="edad0-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="edad0-114">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="edad0-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="edad0-115">實作`FunctionLeave3`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="edad0-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="edad0-116">實作不應嘗試回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="edad0-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="edad0-117">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionLeave3`傳回。</span><span class="sxs-lookup"><span data-stu-id="edad0-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="edad0-118">`FunctionLeave3`函式不能呼叫 managed 程式碼或以任何方式導致受管理的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="edad0-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edad0-119">需求</span><span class="sxs-lookup"><span data-stu-id="edad0-119">Requirements</span></span>  
 <span data-ttu-id="edad0-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edad0-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edad0-121">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="edad0-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="edad0-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edad0-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edad0-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edad0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edad0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edad0-124">See Also</span></span>  
 [<span data-ttu-id="edad0-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="edad0-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="edad0-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="edad0-126">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="edad0-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="edad0-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="edad0-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="edad0-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="edad0-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="edad0-129">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="edad0-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="edad0-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="edad0-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="edad0-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="edad0-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="edad0-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="edad0-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="edad0-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="edad0-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="edad0-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
