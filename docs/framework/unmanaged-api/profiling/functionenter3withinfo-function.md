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
ms.openlocfilehash: 86b1c8b3f5bd88b216c59f5cc6846f83f3c094ee
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440759"
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="b2ecf-102">FunctionEnter3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="b2ecf-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="b2ecf-103">通知分析工具控制項正傳遞至函式，並提供可傳遞至[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)的控制碼，以抓取堆疊框架和函式引數。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ecf-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2ecf-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2ecf-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2ecf-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="b2ecf-106">在傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b2ecf-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b2ecf-108">這個控制碼只有在傳遞它的回呼期間才有效。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2ecf-109">備註</span><span class="sxs-lookup"><span data-stu-id="b2ecf-109">Remarks</span></span>  
 <span data-ttu-id="b2ecf-110">`FunctionEnter3WithInfo` 回呼方法會在呼叫函式時通知分析工具，並讓分析工具使用[ICorProfilerInfo3：： GetFunctionEnter3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)來檢查引數值。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="b2ecf-111">若要存取引數資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_ARGS` 旗標。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="b2ecf-112">分析工具可以使用[ICorProfilerInfo：： SetEventMask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件旗標，然後使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="b2ecf-113">`FunctionEnter3WithInfo` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="b2ecf-114">此執行必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="b2ecf-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b2ecf-116">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b2ecf-117">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b2ecf-118">`FunctionEnter3WithInfo` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="b2ecf-119">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b2ecf-120">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionEnter3WithInfo` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="b2ecf-121">`FunctionEnter3WithInfo` 函式不得呼叫 managed 程式碼，或以任何方式造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ecf-122">需求</span><span class="sxs-lookup"><span data-stu-id="b2ecf-122">Requirements</span></span>  
 <span data-ttu-id="b2ecf-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2ecf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ecf-124">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="b2ecf-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b2ecf-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2ecf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2ecf-126">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ecf-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2ecf-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2ecf-127">See also</span></span>

- [<span data-ttu-id="b2ecf-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="b2ecf-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)
- [<span data-ttu-id="b2ecf-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="b2ecf-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="b2ecf-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="b2ecf-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="b2ecf-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b2ecf-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
