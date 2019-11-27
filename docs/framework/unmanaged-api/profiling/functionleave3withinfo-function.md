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
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="0db8d-102">FunctionLeave3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="0db8d-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="0db8d-103">通知分析工具，控制項是從函式傳回，並提供可傳遞至[ICorProfilerInfo3：： GetFunctionLeave3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)的控制碼，以取得堆疊框架和傳回值。</span><span class="sxs-lookup"><span data-stu-id="0db8d-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0db8d-104">語法</span><span class="sxs-lookup"><span data-stu-id="0db8d-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0db8d-105">參數</span><span class="sxs-lookup"><span data-stu-id="0db8d-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="0db8d-106">在傳回控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="0db8d-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="0db8d-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="0db8d-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="0db8d-108">這個控制碼只有在傳遞它的回呼期間才有效。</span><span class="sxs-lookup"><span data-stu-id="0db8d-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0db8d-109">備註</span><span class="sxs-lookup"><span data-stu-id="0db8d-109">Remarks</span></span>  
 <span data-ttu-id="0db8d-110">`FunctionLeave3WithInfo` 回呼方法會在呼叫函式時通知分析工具，並允許分析工具使用[ICorProfilerInfo3：： GetFunctionLeave3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)來檢查傳回值。</span><span class="sxs-lookup"><span data-stu-id="0db8d-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="0db8d-111">若要存取傳回值資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_RETVAL` 旗標。</span><span class="sxs-lookup"><span data-stu-id="0db8d-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="0db8d-112">分析工具可以使用[ICorProfilerInfo：： SetEventMask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件旗標，然後使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="0db8d-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="0db8d-113">`FunctionLeave3WithInfo` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="0db8d-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="0db8d-114">此執行必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="0db8d-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="0db8d-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="0db8d-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="0db8d-116">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="0db8d-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="0db8d-117">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="0db8d-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="0db8d-118">`FunctionLeave3WithInfo` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="0db8d-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="0db8d-119">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="0db8d-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="0db8d-120">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionLeave3WithInfo` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="0db8d-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="0db8d-121">`FunctionLeave3WithInfo` 函式不得呼叫 managed 程式碼，或以任何方式造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="0db8d-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0db8d-122">需求</span><span class="sxs-lookup"><span data-stu-id="0db8d-122">Requirements</span></span>  
 <span data-ttu-id="0db8d-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0db8d-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0db8d-124">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="0db8d-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="0db8d-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0db8d-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0db8d-126">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0db8d-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db8d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0db8d-127">See also</span></span>

- [<span data-ttu-id="0db8d-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="0db8d-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="0db8d-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="0db8d-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="0db8d-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="0db8d-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="0db8d-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="0db8d-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="0db8d-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0db8d-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="0db8d-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0db8d-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="0db8d-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="0db8d-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="0db8d-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="0db8d-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="0db8d-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="0db8d-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="0db8d-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="0db8d-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="0db8d-138">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="0db8d-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
