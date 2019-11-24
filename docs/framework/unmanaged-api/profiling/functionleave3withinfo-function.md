---
title: FunctionLeave3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
ms.openlocfilehash: a62f402fbfae6188ab0423ea7a55a4dfc6cb4112
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427396"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="a58d6-102">FunctionLeave3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="a58d6-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="a58d6-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span><span class="sxs-lookup"><span data-stu-id="a58d6-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a58d6-104">語法</span><span class="sxs-lookup"><span data-stu-id="a58d6-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a58d6-105">參數</span><span class="sxs-lookup"><span data-stu-id="a58d6-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="a58d6-106">[in] The identifier of the function from which control is returned.</span><span class="sxs-lookup"><span data-stu-id="a58d6-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="a58d6-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a58d6-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="a58d6-108">This handle is valid only during the callback to which it is passed.</span><span class="sxs-lookup"><span data-stu-id="a58d6-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a58d6-109">備註</span><span class="sxs-lookup"><span data-stu-id="a58d6-109">Remarks</span></span>  
 <span data-ttu-id="a58d6-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span><span class="sxs-lookup"><span data-stu-id="a58d6-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="a58d6-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span><span class="sxs-lookup"><span data-stu-id="a58d6-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="a58d6-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span><span class="sxs-lookup"><span data-stu-id="a58d6-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="a58d6-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span><span class="sxs-lookup"><span data-stu-id="a58d6-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="a58d6-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span><span class="sxs-lookup"><span data-stu-id="a58d6-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="a58d6-115">The execution engine does not save any registers before calling this function.</span><span class="sxs-lookup"><span data-stu-id="a58d6-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="a58d6-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span><span class="sxs-lookup"><span data-stu-id="a58d6-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="a58d6-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span><span class="sxs-lookup"><span data-stu-id="a58d6-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="a58d6-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span><span class="sxs-lookup"><span data-stu-id="a58d6-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="a58d6-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span><span class="sxs-lookup"><span data-stu-id="a58d6-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="a58d6-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span><span class="sxs-lookup"><span data-stu-id="a58d6-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="a58d6-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span><span class="sxs-lookup"><span data-stu-id="a58d6-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a58d6-122">需求</span><span class="sxs-lookup"><span data-stu-id="a58d6-122">Requirements</span></span>  
 <span data-ttu-id="a58d6-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a58d6-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a58d6-124">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="a58d6-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="a58d6-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a58d6-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a58d6-126">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a58d6-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a58d6-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="a58d6-127">See also</span></span>

- [<span data-ttu-id="a58d6-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="a58d6-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="a58d6-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="a58d6-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="a58d6-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="a58d6-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="a58d6-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="a58d6-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="a58d6-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a58d6-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="a58d6-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a58d6-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="a58d6-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="a58d6-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="a58d6-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="a58d6-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="a58d6-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="a58d6-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="a58d6-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="a58d6-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="a58d6-138">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="a58d6-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
