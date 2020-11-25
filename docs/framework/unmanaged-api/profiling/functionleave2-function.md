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
ms.openlocfilehash: 5fa6ffff3cdb64a7471568e1f6e76fea9194c5a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722280"
---
# <a name="functionleave2-function"></a><span data-ttu-id="08902-102">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="08902-102">FunctionLeave2 Function</span></span>

<span data-ttu-id="08902-103">通知分析工具，函式即將傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="08902-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08902-104">語法</span><span class="sxs-lookup"><span data-stu-id="08902-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08902-105">參數</span><span class="sxs-lookup"><span data-stu-id="08902-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="08902-106">\[in] 傳回之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="08902-106">\[in] The identifier of the function that is returning.</span></span>

- `clientData`

  <span data-ttu-id="08902-107">\[in] 重新對應的函式識別碼，分析工具先前透過 [FunctionIDMapper](functionidmapper-function.md) 函式指定。</span><span class="sxs-lookup"><span data-stu-id="08902-107">\[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>

- `func`

  <span data-ttu-id="08902-108">\[in] `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="08902-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="08902-109">分析工具應該將它視為不透明的控制碼，可以傳回給 [ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) 方法中的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="08902-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `retvalRange`

  <span data-ttu-id="08902-110">\[in] [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) 結構的指標，指定函式傳回值的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="08902-110">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>

  <span data-ttu-id="08902-111">為了存取傳回值資訊， `COR_PRF_ENABLE_FUNCTION_RETVAL` 必須設定旗標。</span><span class="sxs-lookup"><span data-stu-id="08902-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="08902-112">分析工具可以使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md) 方法來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="08902-112">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="08902-113">備註</span><span class="sxs-lookup"><span data-stu-id="08902-113">Remarks</span></span>  

 <span data-ttu-id="08902-114">當函式傳回 `func` 時，和參數的值無效， `retvalRange` `FunctionLeave2` 因為這些值可能會變更或損毀。</span><span class="sxs-lookup"><span data-stu-id="08902-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="08902-115">`FunctionLeave2`函數是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="08902-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="08902-116">實作為必須使用 `__declspec` (`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="08902-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="08902-117">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="08902-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="08902-118">輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。</span><span class="sxs-lookup"><span data-stu-id="08902-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="08902-119">在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="08902-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="08902-120">的執行 `FunctionLeave2` 不應封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="08902-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="08902-121">執行不應嘗試垃圾收集，因為堆疊可能不是處於垃圾收集的易記狀態。</span><span class="sxs-lookup"><span data-stu-id="08902-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="08902-122">如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionLeave2` 。</span><span class="sxs-lookup"><span data-stu-id="08902-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="08902-123">此外，此函式 `FunctionLeave2` 不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="08902-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08902-124">需求</span><span class="sxs-lookup"><span data-stu-id="08902-124">Requirements</span></span>  

 <span data-ttu-id="08902-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08902-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08902-126">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="08902-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="08902-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08902-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08902-128">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08902-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08902-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08902-129">See also</span></span>

- [<span data-ttu-id="08902-130">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="08902-130">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="08902-131">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="08902-131">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="08902-132">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="08902-132">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="08902-133">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="08902-133">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
