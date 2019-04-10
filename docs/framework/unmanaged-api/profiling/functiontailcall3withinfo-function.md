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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4352d006c95a5b85341625220e6c7e62a86b482a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178083"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="53dbe-102">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="53dbe-102">FunctionTailcall3WithInfo Function</span></span>
<span data-ttu-id="53dbe-103">通知分析工具目前正在執行的函式即將執行結尾呼叫另一個函式，並提供可以傳遞至控制代碼[ICorProfilerInfo3::GetFunctionTailcall3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)擷取堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="53dbe-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53dbe-104">語法</span><span class="sxs-lookup"><span data-stu-id="53dbe-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53dbe-105">參數</span><span class="sxs-lookup"><span data-stu-id="53dbe-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="53dbe-106">[in]目前正在執行時進行呼叫的結尾的函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="53dbe-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="53dbe-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="53dbe-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="53dbe-108">這個控制代碼傳遞到回呼期間，只是有效的。</span><span class="sxs-lookup"><span data-stu-id="53dbe-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53dbe-109">備註</span><span class="sxs-lookup"><span data-stu-id="53dbe-109">Remarks</span></span>  
 <span data-ttu-id="53dbe-110">`FunctionTailcall3WithInfo`回呼方法會通知分析工具，因為函式呼叫時，並允許使用分析工具[ICorProfilerInfo3::GetFunctionTailcall3Info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)檢查堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="53dbe-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="53dbe-111">若要存取堆疊框架資訊，`COR_PRF_ENABLE_FRAME_INFO`旗標的設定。</span><span class="sxs-lookup"><span data-stu-id="53dbe-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="53dbe-112">可以使用分析工具[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式的實作。</span><span class="sxs-lookup"><span data-stu-id="53dbe-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="53dbe-113">`FunctionTailcall3WithInfo`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="53dbe-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="53dbe-114">的實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="53dbe-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="53dbe-115">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="53dbe-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="53dbe-116">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="53dbe-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="53dbe-117">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="53dbe-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="53dbe-118">實作`FunctionTailcall3WithInfo`不應封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="53dbe-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="53dbe-119">實作不應嘗試回收，因為堆疊可能無法在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="53dbe-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="53dbe-120">如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionTailcall3WithInfo`傳回。</span><span class="sxs-lookup"><span data-stu-id="53dbe-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="53dbe-121">此外，FunctionTailcall3WithInfo 函式必須不呼叫 managed 程式碼，或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="53dbe-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53dbe-122">需求</span><span class="sxs-lookup"><span data-stu-id="53dbe-122">Requirements</span></span>  
 <span data-ttu-id="53dbe-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53dbe-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53dbe-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="53dbe-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="53dbe-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53dbe-125">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="53dbe-126">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="53dbe-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="53dbe-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53dbe-127">See also</span></span>

- [<span data-ttu-id="53dbe-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="53dbe-128">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="53dbe-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="53dbe-129">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="53dbe-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="53dbe-130">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="53dbe-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="53dbe-131">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="53dbe-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="53dbe-132">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="53dbe-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="53dbe-133">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="53dbe-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="53dbe-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="53dbe-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="53dbe-135">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="53dbe-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="53dbe-136">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="53dbe-137">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="53dbe-137">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
