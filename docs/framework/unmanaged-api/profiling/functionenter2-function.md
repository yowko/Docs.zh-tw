---
title: "FunctionEnter2 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter2
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionEnter2
helpviewer_keywords: FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type: apiref
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0709d54589b3f88b461adde3f3d380407d263855
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter2-function"></a><span data-ttu-id="f5a95-102">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="f5a95-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="f5a95-103">控制項傳遞至函式，並提供堆疊的相關資訊框架和函式的引數，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="f5a95-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="f5a95-104">這個函數會取代[FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f5a95-104">This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5a95-105">語法</span><span class="sxs-lookup"><span data-stu-id="f5a95-105">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5a95-106">參數</span><span class="sxs-lookup"><span data-stu-id="f5a95-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="f5a95-107">[in]控制權會傳遞函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="f5a95-107">[in] The identifier of the function to which control is passed.</span></span>  
  
 `clientData`  
 <span data-ttu-id="f5a95-108">[in]重新對應的函式識別項，利用先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="f5a95-108">[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="f5a95-109">[in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="f5a95-109">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="f5a95-110">程式碼剖析工具應該將此視為不透明控制代碼可傳遞回執行引擎中[icorprofilerinfo2:: Getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f5a95-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `argumentInfo`  
 <span data-ttu-id="f5a95-111">[in]指標[COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md)結構，在記憶體中的函式的引數指定的位置。</span><span class="sxs-lookup"><span data-stu-id="f5a95-111">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>  
  
 <span data-ttu-id="f5a95-112">若要存取引數的詳細資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`旗標必須設定。</span><span class="sxs-lookup"><span data-stu-id="f5a95-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="f5a95-113">分析工具可以使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="f5a95-113">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5a95-114">備註</span><span class="sxs-lookup"><span data-stu-id="f5a95-114">Remarks</span></span>  
 <span data-ttu-id="f5a95-115">值`func`和`argumentInfo`參數都不是有效之後`FunctionEnter2`函式傳回，因為可能會變更的值，或被終結。</span><span class="sxs-lookup"><span data-stu-id="f5a95-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="f5a95-116">`FunctionEnter2`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="f5a95-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="f5a95-117">實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="f5a95-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="f5a95-118">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="f5a95-118">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="f5a95-119">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="f5a95-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="f5a95-120">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="f5a95-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="f5a95-121">實作`FunctionEnter2`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="f5a95-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="f5a95-122">實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="f5a95-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="f5a95-123">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionEnter2`傳回。</span><span class="sxs-lookup"><span data-stu-id="f5a95-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="f5a95-124">此外，`FunctionEnter2`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="f5a95-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5a95-125">需求</span><span class="sxs-lookup"><span data-stu-id="f5a95-125">Requirements</span></span>  
 <span data-ttu-id="f5a95-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f5a95-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5a95-127">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="f5a95-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="f5a95-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5a95-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5a95-129">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5a95-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a95-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="f5a95-130">See Also</span></span>  
 [<span data-ttu-id="f5a95-131">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="f5a95-131">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="f5a95-132">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="f5a95-132">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="f5a95-133">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="f5a95-133">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="f5a95-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="f5a95-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
