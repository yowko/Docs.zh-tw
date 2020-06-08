---
title: FunctionTailcall 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: 42ea497bdcab71518bec08514b827d76f0317d57
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500594"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="19bd4-102">FunctionTailcall 函式</span><span class="sxs-lookup"><span data-stu-id="19bd4-102">FunctionTailcall Function</span></span>
<span data-ttu-id="19bd4-103">通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="19bd4-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="19bd4-104">函式 `FunctionTailcall` 在 .NET Framework 版本2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="19bd4-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="19bd4-105">它會繼續工作，但會造成效能上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="19bd4-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="19bd4-106">請改用[FunctionTailcall2](functiontailcall2-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="19bd4-106">Use the [FunctionTailcall2](functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19bd4-107">語法</span><span class="sxs-lookup"><span data-stu-id="19bd4-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19bd4-108">參數</span><span class="sxs-lookup"><span data-stu-id="19bd4-108">Parameters</span></span>

- `funcID`

  <span data-ttu-id="19bd4-109">\[in] 目前正在執行之函式的識別碼，即將進行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="19bd4-109">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

## <a name="remarks"></a><span data-ttu-id="19bd4-110">備註</span><span class="sxs-lookup"><span data-stu-id="19bd4-110">Remarks</span></span>  
 <span data-ttu-id="19bd4-111">Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回呼叫端呼叫之函式的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="19bd4-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="19bd4-112">這表示不會針對做為 tail 呼叫目標的函式發出[FunctionLeave](functionleave-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="19bd4-112">This means that a [FunctionLeave](functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="19bd4-113">函式 `FunctionTailcall` 是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="19bd4-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="19bd4-114">此執行必須使用 `__declspec` （ `naked` ）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="19bd4-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="19bd4-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="19bd4-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="19bd4-116">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="19bd4-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="19bd4-117">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="19bd4-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="19bd4-118">的執行 `FunctionTailcall` 不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="19bd4-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="19bd4-119">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="19bd4-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="19bd4-120">如果嘗試垃圾收集，執行時間將會封鎖，直到傳回為止 `FunctionTailcall` 。</span><span class="sxs-lookup"><span data-stu-id="19bd4-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="19bd4-121">此外，函式 `FunctionTailcall` 不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="19bd4-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19bd4-122">規格需求</span><span class="sxs-lookup"><span data-stu-id="19bd4-122">Requirements</span></span>  
 <span data-ttu-id="19bd4-123">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19bd4-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19bd4-124">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="19bd4-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="19bd4-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19bd4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19bd4-126">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="19bd4-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bd4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19bd4-127">See also</span></span>

- [<span data-ttu-id="19bd4-128">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="19bd4-128">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="19bd4-129">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="19bd4-129">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="19bd4-130">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="19bd4-130">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="19bd4-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="19bd4-131">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
