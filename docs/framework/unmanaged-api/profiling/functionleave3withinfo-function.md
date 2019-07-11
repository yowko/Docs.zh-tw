---
title: FunctionLeave3WithInfo 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3WithInfo
helpviewer_keywords:
- FunctionLeave3WithInfo function [.NET Framework profiling]
ms.assetid: 5fa68a67-ced6-41c6-a2c0-467060fd0692
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 495ed887126f0b569acc1309609a0c132d0766eb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763319"
---
# <a name="functionleave3withinfo-function"></a><span data-ttu-id="6552f-102">FunctionLeave3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="6552f-102">FunctionLeave3WithInfo Function</span></span>
<span data-ttu-id="6552f-103">通知分析工具，從函式，傳回控制項，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionLeave3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)擷取堆疊框架和傳回值。</span><span class="sxs-lookup"><span data-stu-id="6552f-103">Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6552f-104">語法</span><span class="sxs-lookup"><span data-stu-id="6552f-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6552f-105">參數</span><span class="sxs-lookup"><span data-stu-id="6552f-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="6552f-106">[in]控制要傳回的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6552f-106">[in] The identifier of the function from which control is returned.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="6552f-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="6552f-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="6552f-108">這個控制代碼傳遞到回呼期間，只是有效的。</span><span class="sxs-lookup"><span data-stu-id="6552f-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6552f-109">備註</span><span class="sxs-lookup"><span data-stu-id="6552f-109">Remarks</span></span>  
 <span data-ttu-id="6552f-110">`FunctionLeave3WithInfo`回呼方法會通知分析工具，因為函式呼叫時，並允許使用分析工具[ICorProfilerInfo3::GetFunctionLeave3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)檢查傳回的值。</span><span class="sxs-lookup"><span data-stu-id="6552f-110">The `FunctionLeave3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionLeave3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to inspect the return value.</span></span> <span data-ttu-id="6552f-111">若要存取傳回值的詳細資訊，`COR_PRF_ENABLE_FUNCTION_RETVAL`旗標的設定。</span><span class="sxs-lookup"><span data-stu-id="6552f-111">To access return value information, the `COR_PRF_ENABLE_FUNCTION_RETVAL` flag has to be set.</span></span> <span data-ttu-id="6552f-112">可以使用分析工具[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式的實作。</span><span class="sxs-lookup"><span data-stu-id="6552f-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="6552f-113">`FunctionLeave3WithInfo`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="6552f-113">The `FunctionLeave3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="6552f-114">的實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="6552f-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="6552f-115">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="6552f-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="6552f-116">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="6552f-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="6552f-117">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="6552f-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="6552f-118">實作`FunctionLeave3WithInfo`不應封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="6552f-118">The implementation of `FunctionLeave3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="6552f-119">實作不應嘗試回收，因為堆疊可能無法在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="6552f-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="6552f-120">如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionLeave3WithInfo`傳回。</span><span class="sxs-lookup"><span data-stu-id="6552f-120">If a garbage collection is attempted, the runtime will block until `FunctionLeave3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="6552f-121">`FunctionLeave3WithInfo`函式不能呼叫 managed 程式碼或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="6552f-121">The `FunctionLeave3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6552f-122">需求</span><span class="sxs-lookup"><span data-stu-id="6552f-122">Requirements</span></span>  
 <span data-ttu-id="6552f-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6552f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6552f-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="6552f-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="6552f-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6552f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6552f-126">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6552f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6552f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6552f-127">See also</span></span>

- [<span data-ttu-id="6552f-128">GetFunctionLeave3Info</span><span class="sxs-lookup"><span data-stu-id="6552f-128">GetFunctionLeave3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)
- [<span data-ttu-id="6552f-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="6552f-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="6552f-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="6552f-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="6552f-131">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="6552f-131">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="6552f-132">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6552f-132">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="6552f-133">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6552f-133">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="6552f-134">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="6552f-134">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="6552f-135">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="6552f-135">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="6552f-136">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="6552f-136">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="6552f-137">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="6552f-137">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="6552f-138">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6552f-138">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
