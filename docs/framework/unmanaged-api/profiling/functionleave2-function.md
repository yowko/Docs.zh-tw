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
ms.openlocfilehash: a2a3d58e0631fceab96c32f9d86fef25973fed84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500659"
---
# <a name="functionleave2-function"></a><span data-ttu-id="96266-102">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="96266-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="96266-103">通知分析工具，函式即將傳回給呼叫端，並提供堆疊框架和函數傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="96266-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96266-104">語法</span><span class="sxs-lookup"><span data-stu-id="96266-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96266-105">參數</span><span class="sxs-lookup"><span data-stu-id="96266-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="96266-106">\[in] 傳回的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="96266-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="96266-107">\[in] 重新對應的函式識別碼，這是先前透過[FunctionIDMapper](functionidmapper-function.md)函數指定的 profiler。</span><span class="sxs-lookup"><span data-stu-id="96266-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="96266-108">\[in] `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="96266-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="96266-109">分析工具應該將此視為不透明的控制碼，以便在[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)方法中傳回給執行引擎。</span><span class="sxs-lookup"><span data-stu-id="96266-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="96266-110">\[in] [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md)結構的指標，指定函式傳回值的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="96266-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="96266-111">為了存取傳回值資訊， `COR_PRF_ENABLE_FUNCTION_RETVAL` 必須設定旗標。</span><span class="sxs-lookup"><span data-stu-id="96266-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="96266-112">分析工具可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="96266-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="96266-113">備註</span><span class="sxs-lookup"><span data-stu-id="96266-113">Remarks</span></span>  
 <span data-ttu-id="96266-114">當函式傳回 `func` 時，和參數的值 `retvalRange` 無效， `FunctionLeave2` 因為這些值可能會變更或終結。</span><span class="sxs-lookup"><span data-stu-id="96266-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="96266-115">函式 `FunctionLeave2` 是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="96266-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="96266-116">此執行必須使用 `__declspec` （ `naked` ）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="96266-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="96266-117">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="96266-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="96266-118">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="96266-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="96266-119">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="96266-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="96266-120">的執行 `FunctionLeave2` 不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="96266-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="96266-121">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="96266-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="96266-122">如果嘗試垃圾收集，執行時間將會封鎖，直到傳回為止 `FunctionLeave2` 。</span><span class="sxs-lookup"><span data-stu-id="96266-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="96266-123">此外，函式 `FunctionLeave2` 不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="96266-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96266-124">規格需求</span><span class="sxs-lookup"><span data-stu-id="96266-124">Requirements</span></span>  
 <span data-ttu-id="96266-125">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96266-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96266-126">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="96266-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="96266-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96266-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96266-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96266-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96266-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96266-129">See also</span></span>

- [<span data-ttu-id="96266-130">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="96266-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="96266-131">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="96266-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="96266-132">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="96266-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="96266-133">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="96266-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
