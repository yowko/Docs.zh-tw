---
title: FunctionTailcall3WithInfo 函式
ms.date: 03/30/2017
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
ms.openlocfilehash: c23c791197c9925038f71e70409e4ca3ebabb23e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722854"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="d5d36-102">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="d5d36-102">FunctionTailcall3WithInfo Function</span></span>

<span data-ttu-id="d5d36-103">通知分析工具，目前正在執行的函式即將執行另一個函式的 tail 呼叫，並提供可傳遞至 [ICorProfilerInfo3：： GetFunctionTailcall3Info 方法](icorprofilerinfo3-getfunctiontailcall3info-method.md) 的控制碼，以取得堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="d5d36-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d36-104">語法</span><span class="sxs-lookup"><span data-stu-id="d5d36-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5d36-105">參數</span><span class="sxs-lookup"><span data-stu-id="d5d36-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="d5d36-106">\[in] 目前正在執行之函式的識別碼，即將進行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d5d36-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="d5d36-107">\[in] 不透明的控制碼，表示指定之堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d5d36-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="d5d36-108">這個控制碼只有在傳遞的回呼期間有效。</span><span class="sxs-lookup"><span data-stu-id="d5d36-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="d5d36-109">備註</span><span class="sxs-lookup"><span data-stu-id="d5d36-109">Remarks</span></span>  

 <span data-ttu-id="d5d36-110">`FunctionTailcall3WithInfo`回呼方法會在呼叫函式時通知分析工具，並允許 profiler 使用[ICorProfilerInfo3：： GetFunctionTailcall3Info 方法](icorprofilerinfo3-getfunctiontailcall3info-method.md)來檢查堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="d5d36-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="d5d36-111">若要存取堆疊框架資訊，必須 `COR_PRF_ENABLE_FRAME_INFO` 設定旗標。</span><span class="sxs-lookup"><span data-stu-id="d5d36-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="d5d36-112">分析工具可以使用 [ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md) 來設定事件旗標，然後使用 [ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) 來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="d5d36-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="d5d36-113">`FunctionTailcall3WithInfo`函數是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="d5d36-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="d5d36-114">實作為必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="d5d36-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="d5d36-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="d5d36-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="d5d36-116">輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。</span><span class="sxs-lookup"><span data-stu-id="d5d36-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="d5d36-117">在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="d5d36-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="d5d36-118">的執行 `FunctionTailcall3WithInfo` 不應封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="d5d36-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="d5d36-119">因為堆疊可能不是處於垃圾收集的狀態，所以不應該嘗試執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="d5d36-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="d5d36-120">如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionTailcall3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="d5d36-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="d5d36-121">此外，FunctionTailcall3WithInfo 函式不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="d5d36-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5d36-122">需求</span><span class="sxs-lookup"><span data-stu-id="d5d36-122">Requirements</span></span>  

 <span data-ttu-id="d5d36-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d5d36-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5d36-124">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="d5d36-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="d5d36-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5d36-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5d36-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5d36-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d36-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5d36-127">See also</span></span>

- [<span data-ttu-id="d5d36-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="d5d36-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="d5d36-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="d5d36-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="d5d36-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="d5d36-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="d5d36-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d5d36-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="d5d36-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d5d36-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="d5d36-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="d5d36-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="d5d36-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="d5d36-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="d5d36-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d5d36-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d5d36-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="d5d36-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="d5d36-137">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d5d36-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
