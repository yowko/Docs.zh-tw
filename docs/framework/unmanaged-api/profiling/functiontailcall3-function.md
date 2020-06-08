---
title: FunctionTailcall3 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3
helpviewer_keywords:
- FunctionTailcall3 function [.NET Framework profiling]
ms.assetid: 1e48243f-5de6-4bd6-a1d0-e1d248bca4b8
topic_type:
- apiref
ms.openlocfilehash: 55955cd47bd32fb4294b0b8e852dd692702bd74f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500529"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="ff2e6-102">FunctionTailcall3 函式</span><span class="sxs-lookup"><span data-stu-id="ff2e6-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="ff2e6-103">通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff2e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="ff2e6-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff2e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="ff2e6-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="ff2e6-106">\[in] 目前正在執行之函式的識別碼，即將進行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="ff2e6-107">備註</span><span class="sxs-lookup"><span data-stu-id="ff2e6-107">Remarks</span></span>  
 <span data-ttu-id="ff2e6-108">回呼函式會通知分析工具， `FunctionTailcall3` 因為正在呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="ff2e6-109">請使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3 方法](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="ff2e6-110">函式 `FunctionTailcall3` 是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="ff2e6-111">此執行必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="ff2e6-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="ff2e6-113">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="ff2e6-114">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ff2e6-115">的執行 `FunctionTailcall3` 不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="ff2e6-116">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ff2e6-117">如果嘗試垃圾收集，執行時間將會封鎖，直到傳回為止 `FunctionTailcall3` 。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="ff2e6-118">函式 `FunctionTailcall3` 不得呼叫 managed 程式碼，或以任何方式造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff2e6-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="ff2e6-119">Requirements</span></span>  
 <span data-ttu-id="ff2e6-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ff2e6-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff2e6-121">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="ff2e6-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ff2e6-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff2e6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff2e6-123">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff2e6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff2e6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ff2e6-124">See also</span></span>

- [<span data-ttu-id="ff2e6-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="ff2e6-125">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="ff2e6-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="ff2e6-126">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="ff2e6-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ff2e6-127">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="ff2e6-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ff2e6-128">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="ff2e6-129">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="ff2e6-129">FunctionTailcall3WithInfo Function</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="ff2e6-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="ff2e6-130">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="ff2e6-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="ff2e6-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="ff2e6-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="ff2e6-132">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="ff2e6-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="ff2e6-133">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="ff2e6-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ff2e6-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
