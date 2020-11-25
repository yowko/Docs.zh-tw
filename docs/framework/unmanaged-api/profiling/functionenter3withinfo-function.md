---
title: FunctionEnter3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
ms.openlocfilehash: b511c5abe10ab6c0ec856a5686b082132ed4a5d9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722855"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="e6dfb-102">FunctionEnter3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="e6dfb-102">FunctionEnter3WithInfo Function</span></span>

<span data-ttu-id="e6dfb-103">通知分析工具將控制權傳遞至函式，並提供可傳遞至 [ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md) 的控制碼，以取得堆疊框架和函式引數。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6dfb-104">語法</span><span class="sxs-lookup"><span data-stu-id="e6dfb-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6dfb-105">參數</span><span class="sxs-lookup"><span data-stu-id="e6dfb-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="e6dfb-106">\[in] 要傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="e6dfb-107">\[in] 不透明的控制碼，表示指定之堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="e6dfb-108">這個控制碼只有在傳遞的回呼期間有效。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6dfb-109">備註</span><span class="sxs-lookup"><span data-stu-id="e6dfb-109">Remarks</span></span>  

 <span data-ttu-id="e6dfb-110">`FunctionEnter3WithInfo`回呼方法會在呼叫函式時通知分析工具，並讓 profiler 使用[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)來檢查引數值。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="e6dfb-111">若要存取引數資訊，必須 `COR_PRF_ENABLE_FUNCTION_ARGS` 設定旗標。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="e6dfb-112">分析工具可以使用 [ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md) 來設定事件旗標，然後使用 [ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) 來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="e6dfb-113">`FunctionEnter3WithInfo`函數是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="e6dfb-114">實作為必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="e6dfb-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="e6dfb-116">輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="e6dfb-117">在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e6dfb-118">的執行 `FunctionEnter3WithInfo` 不應封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="e6dfb-119">因為堆疊可能不是處於垃圾收集的狀態，所以不應該嘗試執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e6dfb-120">如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionEnter3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="e6dfb-121">函式 `FunctionEnter3WithInfo` 不得以任何方式呼叫 managed 程式碼，或導致受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6dfb-122">需求</span><span class="sxs-lookup"><span data-stu-id="e6dfb-122">Requirements</span></span>  

 <span data-ttu-id="e6dfb-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e6dfb-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6dfb-124">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="e6dfb-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e6dfb-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6dfb-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6dfb-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6dfb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6dfb-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6dfb-127">See also</span></span>

- [<span data-ttu-id="e6dfb-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="e6dfb-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="e6dfb-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="e6dfb-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="e6dfb-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="e6dfb-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="e6dfb-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e6dfb-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
