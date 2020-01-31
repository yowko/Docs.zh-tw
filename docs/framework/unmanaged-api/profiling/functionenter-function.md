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
ms.openlocfilehash: caea1d3d526017c0118f95bb138ee4ac45d2c137
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866992"
---
# <a name="functionenter-function"></a><span data-ttu-id="2edd6-102">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="2edd6-102">FunctionEnter Function</span></span>
<span data-ttu-id="2edd6-103">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="2edd6-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2edd6-104">.NET Framework 版本2.0 中的 `FunctionEnter` 函式已被取代，而且其使用方式會造成效能上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="2edd6-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="2edd6-105">請改用[FunctionEnter2](functionenter2-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="2edd6-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2edd6-106">語法</span><span class="sxs-lookup"><span data-stu-id="2edd6-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2edd6-107">參數</span><span class="sxs-lookup"><span data-stu-id="2edd6-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="2edd6-108">中的 \[]）傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="2edd6-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="2edd6-109">備註</span><span class="sxs-lookup"><span data-stu-id="2edd6-109">Remarks</span></span>  
 <span data-ttu-id="2edd6-110">`FunctionEnter` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="2edd6-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="2edd6-111">此執行必須使用 `__declspec`（`naked`）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="2edd6-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="2edd6-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="2edd6-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="2edd6-113">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="2edd6-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="2edd6-114">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="2edd6-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="2edd6-115">`FunctionEnter` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="2edd6-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="2edd6-116">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="2edd6-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="2edd6-117">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionEnter` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="2edd6-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="2edd6-118">此外，`FunctionEnter` 函式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="2edd6-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2edd6-119">需求</span><span class="sxs-lookup"><span data-stu-id="2edd6-119">Requirements</span></span>  
 <span data-ttu-id="2edd6-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2edd6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2edd6-121">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="2edd6-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="2edd6-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2edd6-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2edd6-123">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="2edd6-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edd6-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="2edd6-124">See also</span></span>

- [<span data-ttu-id="2edd6-125">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="2edd6-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="2edd6-126">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="2edd6-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="2edd6-127">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="2edd6-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="2edd6-128">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="2edd6-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="2edd6-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="2edd6-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
