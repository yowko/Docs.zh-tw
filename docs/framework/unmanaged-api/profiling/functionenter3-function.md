---
title: "FunctionEnter3 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bbdfa608f1ea60462dc432a7c2b98cafe66d7be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="functionenter3-function"></a><span data-ttu-id="7393e-102">FunctionEnter3 函式</span><span class="sxs-lookup"><span data-stu-id="7393e-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="7393e-103">通知分析工具控制會傳遞至函數。</span><span class="sxs-lookup"><span data-stu-id="7393e-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7393e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7393e-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7393e-105">參數</span><span class="sxs-lookup"><span data-stu-id="7393e-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="7393e-106">[in]控制權會傳遞函式的識別項。</span><span class="sxs-lookup"><span data-stu-id="7393e-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7393e-107">備註</span><span class="sxs-lookup"><span data-stu-id="7393e-107">Remarks</span></span>  
 <span data-ttu-id="7393e-108">`FunctionEnter3`回呼函式會通知分析工具函式呼叫，但不支援引數檢查。</span><span class="sxs-lookup"><span data-stu-id="7393e-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="7393e-109">使用[icorprofilerinfo3:: Setenterleavefunctionhooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。</span><span class="sxs-lookup"><span data-stu-id="7393e-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7393e-110">`FunctionEnter3`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="7393e-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="7393e-111">實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="7393e-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7393e-112">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="7393e-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="7393e-113">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="7393e-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="7393e-114">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="7393e-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7393e-115">需求</span><span class="sxs-lookup"><span data-stu-id="7393e-115">Requirements</span></span>  
 <span data-ttu-id="7393e-116">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7393e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7393e-117">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7393e-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7393e-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7393e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7393e-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7393e-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7393e-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="7393e-120">See Also</span></span>  
 [<span data-ttu-id="7393e-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="7393e-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [<span data-ttu-id="7393e-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="7393e-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [<span data-ttu-id="7393e-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7393e-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 [<span data-ttu-id="7393e-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7393e-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [<span data-ttu-id="7393e-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7393e-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 [<span data-ttu-id="7393e-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="7393e-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [<span data-ttu-id="7393e-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7393e-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [<span data-ttu-id="7393e-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7393e-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="7393e-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7393e-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [<span data-ttu-id="7393e-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="7393e-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
