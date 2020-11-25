---
title: FunctionTailcall2 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: e1cd3ef78d303aaa325699e1bcdec95f077fef21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703976"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="fd20d-102">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="fd20d-102">FunctionTailcall2 Function</span></span>

<span data-ttu-id="fd20d-103">通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫，並提供堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fd20d-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd20d-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd20d-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd20d-105">參數</span><span class="sxs-lookup"><span data-stu-id="fd20d-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="fd20d-106">\[in] 目前正在執行之函式的識別碼，即將進行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="fd20d-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="fd20d-107">\[在中，分析工具先前透過 [FunctionIDMapper](functionidmapper-function.md)指定的重新對應函式識別碼，目前正在執行的函式即將進行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="fd20d-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="fd20d-108">\[in] `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fd20d-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="fd20d-109">分析工具應該將它視為不透明的控制碼，可以傳回給 [ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) 方法中的執行引擎。</span><span class="sxs-lookup"><span data-stu-id="fd20d-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="fd20d-110">備註</span><span class="sxs-lookup"><span data-stu-id="fd20d-110">Remarks</span></span>  

 <span data-ttu-id="fd20d-111">Tail 呼叫的目標函式會使用目前的堆疊框架，並且會直接傳回給發出 tail 呼叫之函式的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="fd20d-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="fd20d-112">這表示將不會對做為 tail 呼叫目標的函式發出 [FunctionLeave2](functionleave2-function.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="fd20d-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="fd20d-113">函數傳回之後，參數的值無效， `func` `FunctionTailcall2` 因為該值可能會變更或終結。</span><span class="sxs-lookup"><span data-stu-id="fd20d-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="fd20d-114">`FunctionTailcall2`函數是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="fd20d-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="fd20d-115">實作為必須使用 `__declspec` (`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="fd20d-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="fd20d-116">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="fd20d-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="fd20d-117">輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。</span><span class="sxs-lookup"><span data-stu-id="fd20d-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="fd20d-118">在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="fd20d-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="fd20d-119">的執行 `FunctionTailcall2` 不應封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="fd20d-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="fd20d-120">執行不應嘗試垃圾收集，因為堆疊可能不是處於垃圾收集的易記狀態。</span><span class="sxs-lookup"><span data-stu-id="fd20d-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="fd20d-121">如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionTailcall2` 。</span><span class="sxs-lookup"><span data-stu-id="fd20d-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="fd20d-122">此外，此函式 `FunctionTailcall2` 不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="fd20d-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd20d-123">需求</span><span class="sxs-lookup"><span data-stu-id="fd20d-123">Requirements</span></span>  

 <span data-ttu-id="fd20d-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fd20d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd20d-125">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="fd20d-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fd20d-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd20d-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd20d-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd20d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd20d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd20d-128">See also</span></span>

- [<span data-ttu-id="fd20d-129">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="fd20d-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="fd20d-130">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="fd20d-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="fd20d-131">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="fd20d-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="fd20d-132">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="fd20d-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
