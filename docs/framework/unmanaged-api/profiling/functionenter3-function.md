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
ms.openlocfilehash: fd224279b3df6c9e8e55cd81ebfbf2e5ea2428d5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440773"
---
# <a name="functionenter3-function"></a><span data-ttu-id="fbf49-102">FunctionEnter3 函式</span><span class="sxs-lookup"><span data-stu-id="fbf49-102">FunctionEnter3 Function</span></span>
<span data-ttu-id="fbf49-103">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="fbf49-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf49-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbf49-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbf49-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbf49-105">Parameters</span></span>  
 `functionOrRemappedID`  
 <span data-ttu-id="fbf49-106">在傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="fbf49-106">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbf49-107">備註</span><span class="sxs-lookup"><span data-stu-id="fbf49-107">Remarks</span></span>  
 <span data-ttu-id="fbf49-108">`FunctionEnter3` 回呼函式會通知分析工具，因為呼叫的是函式，但不支援引數檢查。</span><span class="sxs-lookup"><span data-stu-id="fbf49-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="fbf49-109">請使用[ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="fbf49-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="fbf49-110">`FunctionEnter3` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="fbf49-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="fbf49-111">此執行必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="fbf49-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="fbf49-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="fbf49-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="fbf49-113">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="fbf49-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="fbf49-114">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="fbf49-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbf49-115">需求</span><span class="sxs-lookup"><span data-stu-id="fbf49-115">Requirements</span></span>  
 <span data-ttu-id="fbf49-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbf49-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbf49-117">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="fbf49-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fbf49-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbf49-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbf49-119">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbf49-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf49-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf49-120">See also</span></span>

- [<span data-ttu-id="fbf49-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="fbf49-121">FunctionLeave3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [<span data-ttu-id="fbf49-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="fbf49-122">FunctionTailcall3</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [<span data-ttu-id="fbf49-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fbf49-123">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="fbf49-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fbf49-124">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="fbf49-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fbf49-125">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="fbf49-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="fbf49-126">SetEnterLeaveFunctionHooks3</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="fbf49-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="fbf49-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="fbf49-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="fbf49-128">SetFunctionIDMapper</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="fbf49-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="fbf49-129">SetFunctionIDMapper2</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="fbf49-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="fbf49-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
