---
title: FunctionEnter 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter
helpviewer_keywords:
- FunctionEnter function [.NET Framework profiling]
ms.assetid: bf4ffa50-4506-4dd4-aa13-a0457b47ca74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6018b5b06a138b38b7b97df280a3e4c4ea0512d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208406"
---
# <a name="functionenter-function"></a><span data-ttu-id="53fbc-102">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="53fbc-102">FunctionEnter Function</span></span>
<span data-ttu-id="53fbc-103">通知分析工具的控制項傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="53fbc-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53fbc-104">`FunctionEnter`函式已被取代，在.NET Framework 2.0 版中，並使用它將會產生對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="53fbc-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="53fbc-105">使用[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="53fbc-105">Use the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fbc-106">語法</span><span class="sxs-lookup"><span data-stu-id="53fbc-106">Syntax</span></span>  
  
```  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53fbc-107">參數</span><span class="sxs-lookup"><span data-stu-id="53fbc-107">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="53fbc-108">[in]控制權會傳遞函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="53fbc-108">[in] The identifier of the function to which control is passed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53fbc-109">備註</span><span class="sxs-lookup"><span data-stu-id="53fbc-109">Remarks</span></span>  
 <span data-ttu-id="53fbc-110">`FunctionEnter`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="53fbc-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="53fbc-111">的實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="53fbc-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="53fbc-112">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="53fbc-112">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="53fbc-113">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="53fbc-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="53fbc-114">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="53fbc-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="53fbc-115">實作`FunctionEnter`應該不會封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="53fbc-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="53fbc-116">實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="53fbc-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="53fbc-117">如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionEnter`傳回。</span><span class="sxs-lookup"><span data-stu-id="53fbc-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="53fbc-118">此外，`FunctionEnter`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="53fbc-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53fbc-119">需求</span><span class="sxs-lookup"><span data-stu-id="53fbc-119">Requirements</span></span>  
 <span data-ttu-id="53fbc-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53fbc-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53fbc-121">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="53fbc-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="53fbc-122">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53fbc-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53fbc-123">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="53fbc-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fbc-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53fbc-124">See also</span></span>

- [<span data-ttu-id="53fbc-125">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="53fbc-125">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="53fbc-126">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="53fbc-126">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="53fbc-127">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="53fbc-127">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="53fbc-128">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="53fbc-128">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="53fbc-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="53fbc-129">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
