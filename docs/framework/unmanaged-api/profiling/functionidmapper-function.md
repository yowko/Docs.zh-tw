---
title: FunctionIDMapper 函式
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 23c6f0a29160b6e1dc194cf360c07374c565522b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440698"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="27212-102">FunctionIDMapper 函式</span><span class="sxs-lookup"><span data-stu-id="27212-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="27212-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span><span class="sxs-lookup"><span data-stu-id="27212-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="27212-104">`FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="27212-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27212-105">語法</span><span class="sxs-lookup"><span data-stu-id="27212-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27212-106">參數</span><span class="sxs-lookup"><span data-stu-id="27212-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="27212-107">[in] 要重新對應的函式識別項。</span><span class="sxs-lookup"><span data-stu-id="27212-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="27212-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span><span class="sxs-lookup"><span data-stu-id="27212-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27212-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="27212-109">Return Value</span></span>  
 <span data-ttu-id="27212-110">分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。</span><span class="sxs-lookup"><span data-stu-id="27212-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="27212-111">傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。</span><span class="sxs-lookup"><span data-stu-id="27212-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="27212-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span><span class="sxs-lookup"><span data-stu-id="27212-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27212-113">備註</span><span class="sxs-lookup"><span data-stu-id="27212-113">Remarks</span></span>  
 <span data-ttu-id="27212-114">The `FunctionIDMapper` function is a callback.</span><span class="sxs-lookup"><span data-stu-id="27212-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="27212-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span><span class="sxs-lookup"><span data-stu-id="27212-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="27212-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span><span class="sxs-lookup"><span data-stu-id="27212-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="27212-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span><span class="sxs-lookup"><span data-stu-id="27212-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="27212-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span><span class="sxs-lookup"><span data-stu-id="27212-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="27212-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span><span class="sxs-lookup"><span data-stu-id="27212-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="27212-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span><span class="sxs-lookup"><span data-stu-id="27212-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="27212-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span><span class="sxs-lookup"><span data-stu-id="27212-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="27212-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span><span class="sxs-lookup"><span data-stu-id="27212-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="27212-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="27212-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="27212-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="27212-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27212-125">需求</span><span class="sxs-lookup"><span data-stu-id="27212-125">Requirements</span></span>  
 <span data-ttu-id="27212-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27212-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27212-127">**Header:** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="27212-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="27212-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27212-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27212-129">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27212-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27212-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="27212-130">See also</span></span>

- [<span data-ttu-id="27212-131">SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="27212-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="27212-132">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="27212-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)
- [<span data-ttu-id="27212-133">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="27212-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="27212-134">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="27212-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="27212-135">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="27212-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="27212-136">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="27212-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
