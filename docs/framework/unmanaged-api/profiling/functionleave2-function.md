---
title: FunctionLeave2 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: e40687f7f843dc563801bb01b503d2ae94a094fc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446024"
---
# <a name="functionleave2-function"></a><span data-ttu-id="bf675-102">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="bf675-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="bf675-103">通知分析工具，函式即將傳回給呼叫端，並提供堆疊框架和函數傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf675-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf675-104">語法</span><span class="sxs-lookup"><span data-stu-id="bf675-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf675-105">參數</span><span class="sxs-lookup"><span data-stu-id="bf675-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="bf675-106">在傳回之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bf675-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="bf675-107">在重新對應的函式識別碼，分析工具先前透過[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函數指定。</span><span class="sxs-lookup"><span data-stu-id="bf675-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="bf675-108">在`COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bf675-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="bf675-109">分析工具應該將此視為不透明的控制碼，以便在[ICorProfilerInfo2：： GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法中傳回給執行引擎。</span><span class="sxs-lookup"><span data-stu-id="bf675-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="bf675-110">在[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構的指標，指定函式傳回值的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="bf675-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="bf675-111">為了存取傳回值資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_RETVAL` 旗標。</span><span class="sxs-lookup"><span data-stu-id="bf675-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="bf675-112">分析工具可以使用[ICorProfilerInfo：： SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="bf675-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf675-113">備註</span><span class="sxs-lookup"><span data-stu-id="bf675-113">Remarks</span></span>  
 <span data-ttu-id="bf675-114">`FunctionLeave2` 函數傳回之後，`func` 和 `retvalRange` 參數的值無效，因為這些值可能會變更或終結。</span><span class="sxs-lookup"><span data-stu-id="bf675-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="bf675-115">`FunctionLeave2` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="bf675-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="bf675-116">此執行必須使用 `__declspec`（`naked`）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="bf675-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="bf675-117">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="bf675-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="bf675-118">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="bf675-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="bf675-119">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="bf675-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="bf675-120">`FunctionLeave2` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="bf675-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="bf675-121">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="bf675-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="bf675-122">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionLeave2` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="bf675-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="bf675-123">此外，`FunctionLeave2` 函式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="bf675-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf675-124">需求</span><span class="sxs-lookup"><span data-stu-id="bf675-124">Requirements</span></span>  
 <span data-ttu-id="bf675-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bf675-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf675-126">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="bf675-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="bf675-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf675-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf675-128">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf675-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf675-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf675-129">See also</span></span>

- [<span data-ttu-id="bf675-130">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="bf675-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="bf675-131">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="bf675-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="bf675-132">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="bf675-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="bf675-133">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="bf675-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
