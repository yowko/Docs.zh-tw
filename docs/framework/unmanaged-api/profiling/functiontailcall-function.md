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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ec27277fe57bd1a291c2cfe491ea2c6f40c30e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851156"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="b6daf-102">FunctionTailcall 函式</span><span class="sxs-lookup"><span data-stu-id="b6daf-102">FunctionTailcall Function</span></span>
<span data-ttu-id="b6daf-103">通知分析工具，目前正在執行的函式即將對另一個函式執行 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="b6daf-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b6daf-104">`FunctionTailcall`函式在 .NET Framework 版本2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="b6daf-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b6daf-105">它會繼續工作，但會造成效能上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="b6daf-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="b6daf-106">請改用[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="b6daf-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6daf-107">語法</span><span class="sxs-lookup"><span data-stu-id="b6daf-107">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6daf-108">參數</span><span class="sxs-lookup"><span data-stu-id="b6daf-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="b6daf-109">在即將進行 tail 呼叫之目前正在執行之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b6daf-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6daf-110">備註</span><span class="sxs-lookup"><span data-stu-id="b6daf-110">Remarks</span></span>  
 <span data-ttu-id="b6daf-111">Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回呼叫端呼叫之函式的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b6daf-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="b6daf-112">這表示不會針對做為 tail 呼叫目標的函式發出[FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="b6daf-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="b6daf-113">`FunctionTailcall`函式是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="b6daf-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="b6daf-114">此執行必須使用`__declspec`（`naked`）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="b6daf-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="b6daf-115">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="b6daf-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="b6daf-116">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="b6daf-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="b6daf-117">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="b6daf-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="b6daf-118">的執行`FunctionTailcall`不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="b6daf-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="b6daf-119">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="b6daf-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="b6daf-120">如果嘗試垃圾收集，執行時間將會封鎖，直到`FunctionTailcall`傳回為止。</span><span class="sxs-lookup"><span data-stu-id="b6daf-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="b6daf-121">此外，函`FunctionTailcall`式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="b6daf-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6daf-122">需求</span><span class="sxs-lookup"><span data-stu-id="b6daf-122">Requirements</span></span>  
 <span data-ttu-id="b6daf-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6daf-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6daf-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="b6daf-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="b6daf-125">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6daf-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6daf-126">**.NET Framework 版本：** 1.1、1。0</span><span class="sxs-lookup"><span data-stu-id="b6daf-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6daf-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6daf-127">See also</span></span>

- [<span data-ttu-id="b6daf-128">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="b6daf-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="b6daf-129">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="b6daf-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="b6daf-130">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="b6daf-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="b6daf-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="b6daf-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
