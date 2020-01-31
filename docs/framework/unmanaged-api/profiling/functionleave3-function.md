---
title: FunctionLeave3 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 32d86f19e9c50694c7d113195e6967645b710666
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866865"
---
# <a name="functionleave3-function"></a><span data-ttu-id="c9fd6-102">FunctionLeave3 函式</span><span class="sxs-lookup"><span data-stu-id="c9fd6-102">FunctionLeave3 Function</span></span>
<span data-ttu-id="c9fd6-103">通知分析工具，控制項是從函式傳回。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-103">Notifies the profiler that control is being returned from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9fd6-104">語法</span><span class="sxs-lookup"><span data-stu-id="c9fd6-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9fd6-105">參數</span><span class="sxs-lookup"><span data-stu-id="c9fd6-105">Parameters</span></span>  

- `functionOrRemappedID`

  <span data-ttu-id="c9fd6-106">\[in] 從其傳回控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-106">\[in] The identifier of the function from which control is returned.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="c9fd6-107">備註</span><span class="sxs-lookup"><span data-stu-id="c9fd6-107">Remarks</span></span>  
 <span data-ttu-id="c9fd6-108">`FunctionLeave3` 回呼函數會通知分析工具，因為正在呼叫函式，但不支援傳回值檢查。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-108">The `FunctionLeave3` callback function notifies the profiler as functions are being called, but does not support return value inspection.</span></span> <span data-ttu-id="c9fd6-109">請使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3 方法](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="c9fd6-110">`FunctionLeave3` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-110">The `FunctionLeave3` function is a callback; you must implement it.</span></span> <span data-ttu-id="c9fd6-111">此執行必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="c9fd6-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="c9fd6-113">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="c9fd6-114">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="c9fd6-115">`FunctionLeave3` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-115">The implementation of `FunctionLeave3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="c9fd6-116">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="c9fd6-117">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionLeave3` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-117">If a garbage collection is attempted, the runtime will block until `FunctionLeave3` returns.</span></span>  
  
 <span data-ttu-id="c9fd6-118">`FunctionLeave3` 函式不得呼叫 managed 程式碼，或以任何方式造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-118">The `FunctionLeave3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9fd6-119">需求</span><span class="sxs-lookup"><span data-stu-id="c9fd6-119">Requirements</span></span>  
 <span data-ttu-id="c9fd6-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c9fd6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9fd6-121">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="c9fd6-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="c9fd6-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9fd6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9fd6-123">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9fd6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9fd6-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="c9fd6-124">See also</span></span>

- [<span data-ttu-id="c9fd6-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="c9fd6-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="c9fd6-126">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="c9fd6-126">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="c9fd6-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9fd6-127">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="c9fd6-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9fd6-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="c9fd6-129">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9fd6-129">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="c9fd6-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="c9fd6-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="c9fd6-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="c9fd6-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="c9fd6-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="c9fd6-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="c9fd6-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="c9fd6-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="c9fd6-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="c9fd6-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
