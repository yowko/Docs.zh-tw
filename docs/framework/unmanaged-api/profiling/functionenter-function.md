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
ms.openlocfilehash: 52870c7446987817ff00b90db26c3265bccdd096
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500724"
---
# <a name="functionenter-function"></a><span data-ttu-id="15c0f-102">FunctionEnter 函式</span><span class="sxs-lookup"><span data-stu-id="15c0f-102">FunctionEnter Function</span></span>
<span data-ttu-id="15c0f-103">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="15c0f-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15c0f-104">函式 `FunctionEnter` 在 .NET Framework 版本2.0 中已被取代，而且其使用會導致效能降低。</span><span class="sxs-lookup"><span data-stu-id="15c0f-104">The `FunctionEnter` function is deprecated in the .NET Framework version 2.0, and its use will incur a performance penalty.</span></span> <span data-ttu-id="15c0f-105">請改用[FunctionEnter2](functionenter2-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="15c0f-105">Use the [FunctionEnter2](functionenter2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c0f-106">語法</span><span class="sxs-lookup"><span data-stu-id="15c0f-106">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter (  
    [in]  FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15c0f-107">參數</span><span class="sxs-lookup"><span data-stu-id="15c0f-107">Parameters</span></span>

- `funcID`

  <span data-ttu-id="15c0f-108">\[in] 傳遞控制項的目標函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="15c0f-108">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="15c0f-109">備註</span><span class="sxs-lookup"><span data-stu-id="15c0f-109">Remarks</span></span>  
 <span data-ttu-id="15c0f-110">函式 `FunctionEnter` 是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="15c0f-110">The `FunctionEnter` function is a callback; you must implement it.</span></span> <span data-ttu-id="15c0f-111">此執行必須使用 `__declspec` （ `naked` ）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="15c0f-111">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="15c0f-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="15c0f-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="15c0f-113">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="15c0f-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="15c0f-114">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="15c0f-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="15c0f-115">的執行 `FunctionEnter` 不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="15c0f-115">The implementation of `FunctionEnter` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="15c0f-116">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="15c0f-116">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="15c0f-117">如果嘗試垃圾收集，執行時間將會封鎖，直到傳回為止 `FunctionEnter` 。</span><span class="sxs-lookup"><span data-stu-id="15c0f-117">If a garbage collection is attempted, the runtime will block until `FunctionEnter` returns.</span></span>  
  
 <span data-ttu-id="15c0f-118">此外，函式 `FunctionEnter` 不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="15c0f-118">Also, the `FunctionEnter` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c0f-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="15c0f-119">Requirements</span></span>  
 <span data-ttu-id="15c0f-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15c0f-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c0f-121">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="15c0f-121">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="15c0f-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15c0f-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15c0f-123">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="15c0f-123">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c0f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15c0f-124">See also</span></span>

- [<span data-ttu-id="15c0f-125">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="15c0f-125">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="15c0f-126">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="15c0f-126">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="15c0f-127">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="15c0f-127">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="15c0f-128">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="15c0f-128">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="15c0f-129">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="15c0f-129">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
