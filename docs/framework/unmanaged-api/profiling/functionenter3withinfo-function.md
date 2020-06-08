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
ms.openlocfilehash: ff4b32185e604611eaaead2847c11bc139d405a6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500685"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="e5e8a-102">FunctionEnter3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="e5e8a-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="e5e8a-103">通知分析工具控制項正傳遞至函式，並提供可傳遞至[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)的控制碼，以抓取堆疊框架和函式引數。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e8a-104">語法</span><span class="sxs-lookup"><span data-stu-id="e5e8a-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5e8a-105">參數</span><span class="sxs-lookup"><span data-stu-id="e5e8a-105">Parameters</span></span>

- `functionIDOrClientID`

  <span data-ttu-id="e5e8a-106">\[in] 傳遞控制項的目標函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-106">\[in] The identifier of the function to which control is passed.</span></span>

- `eltInfo`

  <span data-ttu-id="e5e8a-107">\[in] 不透明的控制碼，代表指定之堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="e5e8a-108">這個控制碼只有在傳遞它的回呼期間才有效。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5e8a-109">備註</span><span class="sxs-lookup"><span data-stu-id="e5e8a-109">Remarks</span></span>  
 <span data-ttu-id="e5e8a-110">`FunctionEnter3WithInfo`回呼方法會在呼叫函式時通知分析工具，並讓分析工具使用[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](icorprofilerinfo3-getfunctionenter3info-method.md)來檢查引數值。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="e5e8a-111">若要存取引數資訊，必須 `COR_PRF_ENABLE_FUNCTION_ARGS` 設定旗標。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="e5e8a-112">分析工具可以使用[ICorProfilerInfo：： SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)來設定事件旗標，然後使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="e5e8a-113">函式 `FunctionEnter3WithInfo` 是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="e5e8a-114">此執行必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="e5e8a-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="e5e8a-116">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="e5e8a-117">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e5e8a-118">的執行 `FunctionEnter3WithInfo` 不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="e5e8a-119">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e5e8a-120">如果嘗試垃圾收集，執行時間將會封鎖，直到傳回為止 `FunctionEnter3WithInfo` 。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="e5e8a-121">函式 `FunctionEnter3WithInfo` 不得呼叫 managed 程式碼，或以任何方式造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e8a-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="e5e8a-122">Requirements</span></span>  
 <span data-ttu-id="e5e8a-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e5e8a-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e8a-124">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="e5e8a-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e5e8a-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5e8a-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5e8a-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e8a-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e8a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e8a-127">See also</span></span>

- [<span data-ttu-id="e5e8a-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="e5e8a-128">GetFunctionEnter3Info</span></span>](icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="e5e8a-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="e5e8a-129">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="e5e8a-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="e5e8a-130">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="e5e8a-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e5e8a-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
