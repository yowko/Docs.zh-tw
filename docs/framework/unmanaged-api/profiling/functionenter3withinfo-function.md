---
title: "FunctionEnter3WithInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionEnter3WithInfo
api_location: mscorwks.cll
api_type: COM
f1_keywords: FunctionEnter3WithInfo
helpviewer_keywords: FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 37cdf823cc910dd1cebcb587d2616406a842fef2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="functionenter3withinfo-function"></a><span data-ttu-id="1cae3-102">FunctionEnter3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="1cae3-102">FunctionEnter3WithInfo Function</span></span>
<span data-ttu-id="1cae3-103">通知分析工具，控制權會被傳遞給函式，並提供的控制代碼，可以傳遞至[icorprofilerinfo3:: Getfunctionenter3info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)擷取的堆疊框架和函式引數。</span><span class="sxs-lookup"><span data-stu-id="1cae3-103">Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cae3-104">語法</span><span class="sxs-lookup"><span data-stu-id="1cae3-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cae3-105">參數</span><span class="sxs-lookup"><span data-stu-id="1cae3-105">Parameters</span></span>  
 `functionIDOrClientID`  
 <span data-ttu-id="1cae3-106">[in]控制權會傳遞函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="1cae3-106">[in] The identifier of the function to which control is passed.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="1cae3-107">[in] 代表特定堆疊框架之資訊的不透明控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1cae3-107">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="1cae3-108">這個控制代碼無效，只在它所傳遞的回呼。</span><span class="sxs-lookup"><span data-stu-id="1cae3-108">This handle is valid only during the callback to which it is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cae3-109">備註</span><span class="sxs-lookup"><span data-stu-id="1cae3-109">Remarks</span></span>  
 <span data-ttu-id="1cae3-110">`FunctionEnter3WithInfo`回呼方法會通知分析工具函式呼叫，並可讓分析工具使用[icorprofilerinfo3:: Getfunctionenter3info 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)檢查引數的值。</span><span class="sxs-lookup"><span data-stu-id="1cae3-110">The `FunctionEnter3WithInfo` callback method notifies the profiler as functions are called, and enables the profiler to use the [ICorProfilerInfo3::GetFunctionEnter3Info method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to inspect argument values.</span></span> <span data-ttu-id="1cae3-111">若要存取引數的詳細資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`旗標必須設定。</span><span class="sxs-lookup"><span data-stu-id="1cae3-111">To access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag has to be set.</span></span> <span data-ttu-id="1cae3-112">分析工具可以使用[icorprofilerinfo:: Seteventmask 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)來設定事件的旗標，然後使用[icorprofilerinfo3:: Setenterleavefunctionhooks3withinfo 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)註冊您此函式實作。</span><span class="sxs-lookup"><span data-stu-id="1cae3-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="1cae3-113">`FunctionEnter3WithInfo`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="1cae3-113">The `FunctionEnter3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="1cae3-114">實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="1cae3-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="1cae3-115">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="1cae3-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="1cae3-116">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="1cae3-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="1cae3-117">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="1cae3-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="1cae3-118">實作`FunctionEnter3WithInfo`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="1cae3-118">The implementation of `FunctionEnter3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="1cae3-119">實作不應嘗試回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="1cae3-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="1cae3-120">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionEnter3WithInfo`傳回。</span><span class="sxs-lookup"><span data-stu-id="1cae3-120">If a garbage collection is attempted, the runtime will block until `FunctionEnter3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="1cae3-121">`FunctionEnter3WithInfo`函式不能呼叫 managed 程式碼或以任何方式導致受管理的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="1cae3-121">The `FunctionEnter3WithInfo` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cae3-122">需求</span><span class="sxs-lookup"><span data-stu-id="1cae3-122">Requirements</span></span>  
 <span data-ttu-id="1cae3-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1cae3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cae3-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="1cae3-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1cae3-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cae3-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cae3-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cae3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cae3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cae3-127">See Also</span></span>  
 [<span data-ttu-id="1cae3-128">GetFunctionEnter3Info</span><span class="sxs-lookup"><span data-stu-id="1cae3-128">GetFunctionEnter3Info</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [<span data-ttu-id="1cae3-129">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="1cae3-129">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [<span data-ttu-id="1cae3-130">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="1cae3-130">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="1cae3-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="1cae3-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
