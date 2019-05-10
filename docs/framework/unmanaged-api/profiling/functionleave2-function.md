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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8bde206d56bc7e8c930e1e428512232caccfb940
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586836"
---
# <a name="functionleave2-function"></a><span data-ttu-id="3a96d-102">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="3a96d-102">FunctionLeave2 Function</span></span>
<span data-ttu-id="3a96d-103">函式傳回給呼叫者，並提供堆疊框架和函式傳回值的相關資訊，請通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="3a96d-103">Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a96d-104">語法</span><span class="sxs-lookup"><span data-stu-id="3a96d-104">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a96d-105">參數</span><span class="sxs-lookup"><span data-stu-id="3a96d-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="3a96d-106">[in]函式傳回的識別項。</span><span class="sxs-lookup"><span data-stu-id="3a96d-106">[in] The identifier of the function that is returning.</span></span>  
  
 `clientData`  
 <span data-ttu-id="3a96d-107">[in]重新對應的函式識別項，透過先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="3a96d-107">[in] The remapped function identifier, which the profiler previously specified via the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.</span></span>  
  
 `func`  
 <span data-ttu-id="3a96d-108">[in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="3a96d-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="3a96d-109">分析工具應該將這視為不透明的控制代碼可傳遞給在執行引擎[ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="3a96d-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
 `retvalRange`  
 <span data-ttu-id="3a96d-110">[in]指標[COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md)結構，指定函式的傳回值的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="3a96d-110">[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) structure that specifies the memory location of the function's return value.</span></span>  
  
 <span data-ttu-id="3a96d-111">若要存取傳回值的詳細資訊，`COR_PRF_ENABLE_FUNCTION_RETVAL`旗標必須設定。</span><span class="sxs-lookup"><span data-stu-id="3a96d-111">In order to access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag must be set.</span></span> <span data-ttu-id="3a96d-112">可以使用分析工具[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="3a96d-112">The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a96d-113">備註</span><span class="sxs-lookup"><span data-stu-id="3a96d-113">Remarks</span></span>  
 <span data-ttu-id="3a96d-114">值`func`並`retvalRange`參數都不是有效之後`FunctionLeave2`函式會傳回，因為可能會變更的值，或被終結。</span><span class="sxs-lookup"><span data-stu-id="3a96d-114">The values of the `func` and `retvalRange` parameters are not valid after the `FunctionLeave2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="3a96d-115">`FunctionLeave2`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="3a96d-115">The `FunctionLeave2` function is a callback; you must implement it.</span></span> <span data-ttu-id="3a96d-116">的實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="3a96d-116">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3a96d-117">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="3a96d-117">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3a96d-118">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="3a96d-118">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3a96d-119">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="3a96d-119">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3a96d-120">實作`FunctionLeave2`應該不會封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3a96d-120">The implementation of `FunctionLeave2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3a96d-121">實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="3a96d-121">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3a96d-122">如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionLeave2`傳回。</span><span class="sxs-lookup"><span data-stu-id="3a96d-122">If a garbage collection is attempted, the runtime will block until `FunctionLeave2` returns.</span></span>  
  
 <span data-ttu-id="3a96d-123">此外，`FunctionLeave2`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="3a96d-123">Also, the `FunctionLeave2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a96d-124">需求</span><span class="sxs-lookup"><span data-stu-id="3a96d-124">Requirements</span></span>  
 <span data-ttu-id="3a96d-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3a96d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a96d-126">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3a96d-126">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3a96d-127">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a96d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a96d-128">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a96d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a96d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a96d-129">See also</span></span>

- [<span data-ttu-id="3a96d-130">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="3a96d-130">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="3a96d-131">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="3a96d-131">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="3a96d-132">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="3a96d-132">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3a96d-133">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3a96d-133">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
