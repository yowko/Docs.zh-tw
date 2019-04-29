---
title: FunctionEnter3 函式
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a731df84af0991f80c560db417df0ffe053a5e2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598931"
---
# <a name="functionenter3-function"></a><span data-ttu-id="7e3a2-102">FunctionEnter3 函式</span><span class="sxs-lookup"><span data-stu-id="7e3a2-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="7e3a2-103">通知分析工具的控制項傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e3a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e3a2-104">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e3a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="7e3a2-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="7e3a2-106">[in]控制權會傳遞函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e3a2-107">備註</span><span class="sxs-lookup"><span data-stu-id="7e3a2-107">Remarks</span></span>  
 <span data-ttu-id="7e3a2-108">`FunctionEnter3`函式呼叫，但不會不支援引數的檢查，回呼函式會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="7e3a2-109">使用[ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)註冊您的實作，此函式。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="7e3a2-110">`FunctionEnter3`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="7e3a2-111">的實作必須使用`__declspec(naked)`儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="7e3a2-112">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7e3a2-113">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7e3a2-114">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e3a2-115">需求</span><span class="sxs-lookup"><span data-stu-id="7e3a2-115">Requirements</span></span>  
 <span data-ttu-id="7e3a2-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e3a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e3a2-117">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="7e3a2-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7e3a2-118">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e3a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e3a2-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e3a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3a2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e3a2-120">See also</span></span>

- [<span data-ttu-id="7e3a2-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="7e3a2-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="7e3a2-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="7e3a2-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="7e3a2-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7e3a2-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="7e3a2-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7e3a2-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="7e3a2-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7e3a2-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="7e3a2-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="7e3a2-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="7e3a2-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="7e3a2-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="7e3a2-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="7e3a2-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="7e3a2-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="7e3a2-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="7e3a2-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="7e3a2-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
