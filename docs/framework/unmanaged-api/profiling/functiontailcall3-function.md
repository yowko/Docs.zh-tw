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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 979b3401cbf13761bc5b58b4d8734dfa5e83ec49
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586757"
---
# <a name="functiontailcall3-function"></a><span data-ttu-id="e4675-102">FunctionTailcall3 函式</span><span class="sxs-lookup"><span data-stu-id="e4675-102">FunctionTailcall3 Function</span></span>
<span data-ttu-id="e4675-103">通知分析工具目前正在執行的函式即將執行的另一個函式的 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="e4675-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4675-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4675-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall3 (FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4675-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4675-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="e4675-106">[in]目前正在執行時進行呼叫的結尾的函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="e4675-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4675-107">備註</span><span class="sxs-lookup"><span data-stu-id="e4675-107">Remarks</span></span>  
 <span data-ttu-id="e4675-108">`FunctionTailcall3`回呼函式會通知分析工具，為所呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="e4675-108">The `FunctionTailcall3` callback function notifies the profiler as functions are being called.</span></span> <span data-ttu-id="e4675-109">使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。</span><span class="sxs-lookup"><span data-stu-id="e4675-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="e4675-110">`FunctionTailcall3`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="e4675-110">The `FunctionTailcall3` function is a callback; you must implement it.</span></span> <span data-ttu-id="e4675-111">的實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="e4675-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="e4675-112">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="e4675-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="e4675-113">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="e4675-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="e4675-114">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="e4675-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="e4675-115">實作`FunctionTailcall3`不應封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="e4675-115">The implementation of `FunctionTailcall3` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="e4675-116">實作不應嘗試回收，因為堆疊可能無法在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="e4675-116">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="e4675-117">如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionTailcall3`傳回。</span><span class="sxs-lookup"><span data-stu-id="e4675-117">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3` returns.</span></span>  
  
 <span data-ttu-id="e4675-118">`FunctionTailcall3`函式不能呼叫 managed 程式碼或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="e4675-118">The `FunctionTailcall3` function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4675-119">需求</span><span class="sxs-lookup"><span data-stu-id="e4675-119">Requirements</span></span>  
 <span data-ttu-id="e4675-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4675-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4675-121">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="e4675-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="e4675-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4675-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4675-123">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4675-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4675-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4675-124">See also</span></span>

- [<span data-ttu-id="e4675-125">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="e4675-125">FunctionEnter3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [<span data-ttu-id="e4675-126">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="e4675-126">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="e4675-127">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4675-127">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="e4675-128">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4675-128">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="e4675-129">FunctionTailcall3WithInfo 函式</span><span class="sxs-lookup"><span data-stu-id="e4675-129">FunctionTailcall3WithInfo Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="e4675-130">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="e4675-130">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="e4675-131">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="e4675-131">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="e4675-132">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="e4675-132">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="e4675-133">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="e4675-133">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="e4675-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="e4675-134">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
