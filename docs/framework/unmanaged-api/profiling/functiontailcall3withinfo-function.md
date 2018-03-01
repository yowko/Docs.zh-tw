---
title: "FunctionTailcall3WithInfo 函式"
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
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bd2bb56724f977d93e6ebff7d2c4c855a5a222b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="0a5e6-102">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="0a5e6-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="0a5e6-103">通知分析工具目前執行函式即將執行 tail 呼叫另一個函式，並提供的控制代碼，可以傳遞至[icorprofilerinfo3:: Getfunctiontailcall3info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)擷取堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a5e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a5e6-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a5e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="0a5e6-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="0a5e6-106">[in]目前執行的函式進行呼叫的結尾的識別項。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="0a5e6-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="0a5e6-108">這個控制代碼無效，只在它所傳遞的回呼。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a5e6-109">備註</span><span class="sxs-lookup"><span data-stu-id="0a5e6-109">Remarks</span></span>  
 <span data-ttu-id="0a5e6-110">`FunctionTailcall3WithInfo`回呼方法會通知分析工具函式呼叫，並可讓分析工具使用[icorprofilerinfo3:: Getfunctiontailcall3info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)檢查堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="0a5e6-111">若要存取堆疊框架資訊，`COR_PRF_ENABLE_FRAME_INFO`旗標必須設定。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="0a5e6-112">分析工具可以使用[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[icorprofilerinfo3:: Setenterleavefunctionhooks3withinfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式實作。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="0a5e6-113">`FunctionTailcall3WithInfo`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="0a5e6-114">實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="0a5e6-115">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="0a5e6-116">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="0a5e6-117">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0a5e6-118">實作`FunctionTailcall3WithInfo`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="0a5e6-119">實作不應嘗試回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0a5e6-120">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionTailcall3WithInfo`傳回。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="0a5e6-121">此外，FunctionTailcall3WithInfo 函式必須不呼叫 managed 程式碼，或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a5e6-122">需求</span><span class="sxs-lookup"><span data-stu-id="0a5e6-122">Requirements</span></span>  
 <span data-ttu-id="0a5e6-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a5e6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a5e6-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="0a5e6-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0a5e6-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a5e6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a5e6-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a5e6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a5e6-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="0a5e6-127">See Also</span></span>  
 [<span data-ttu-id="0a5e6-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="0a5e6-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="0a5e6-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0a5e6-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="0a5e6-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="0a5e6-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="0a5e6-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0a5e6-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="0a5e6-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0a5e6-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="0a5e6-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="0a5e6-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="0a5e6-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0a5e6-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="0a5e6-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="0a5e6-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="0a5e6-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="0a5e6-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="0a5e6-137">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="0a5e6-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
