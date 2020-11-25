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
ms.openlocfilehash: 9bc88d7dd5b00213da634dc9f511cfe0d39b42f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729833"
---
# <a name="functionenter-function"></a><span data-ttu-id="b7c31-102">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="b7c31-102">FunctionEnter Function</span></span>

<span data-ttu-id="b7c31-103">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="b7c31-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7c31-104">函式 `FunctionEnter` 在 .NET Framework 版本2.0 中已被取代，而且其使用會產生效能負面影響。</span><span class="sxs-lookup"><span data-stu-id="b7c31-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="b7c31-105">請改用 [FunctionEnter2](functionenter2-function.md) 函數。</span><span class="sxs-lookup"><span data-stu-id="b7c31-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7c31-106">語法</span><span class="sxs-lookup"><span data-stu-id="b7c31-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7c31-107">參數</span><span class="sxs-lookup"><span data-stu-id="b7c31-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="b7c31-108">\[in] 要傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="b7c31-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b7c31-109">備註</span><span class="sxs-lookup"><span data-stu-id="b7c31-109">Remarks</span></span>  

 <span data-ttu-id="b7c31-110">`FunctionEnter`函數是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="b7c31-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="b7c31-111">實作為必須使用 `__declspec` (`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="b7c31-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b7c31-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="b7c31-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b7c31-113">輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。</span><span class="sxs-lookup"><span data-stu-id="b7c31-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b7c31-114">在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="b7c31-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b7c31-115">的執行 `FunctionEnter` 不應封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="b7c31-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b7c31-116">執行不應嘗試垃圾收集，因為堆疊可能不是處於垃圾收集的易記狀態。</span><span class="sxs-lookup"><span data-stu-id="b7c31-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b7c31-117">如果嘗試垃圾收集，則執行時間會封鎖直到傳回為止 `FunctionEnter` 。</span><span class="sxs-lookup"><span data-stu-id="b7c31-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="b7c31-118">此外，此函式 `FunctionEnter` 不能呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="b7c31-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7c31-119">需求</span><span class="sxs-lookup"><span data-stu-id="b7c31-119">Requirements</span></span>  

 <span data-ttu-id="b7c31-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b7c31-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7c31-121">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="b7c31-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b7c31-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7c31-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7c31-123">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="b7c31-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7c31-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7c31-124">See also</span></span>

- [<span data-ttu-id="b7c31-125">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="b7c31-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="b7c31-126">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="b7c31-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="b7c31-127">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="b7c31-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="b7c31-128">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="b7c31-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b7c31-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b7c31-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
