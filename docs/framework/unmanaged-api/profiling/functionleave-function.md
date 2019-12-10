---
title: FunctionLeave 函式
ms.date: 03/30/2017
api_name:
- FunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave
helpviewer_keywords:
- FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type:
- apiref
ms.openlocfilehash: 774a5d4e48f00ea8c28977f3f685dcd5a8da3199
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440582"
---
# <a name="functionleave-function"></a><span data-ttu-id="3900a-102">FunctionLeave 函式</span><span class="sxs-lookup"><span data-stu-id="3900a-102">FunctionLeave Function</span></span>
<span data-ttu-id="3900a-103">通知分析工具，函式即將傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="3900a-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3900a-104">.NET Framework 2.0 中的 `FunctionLeave` 函數已被取代。</span><span class="sxs-lookup"><span data-stu-id="3900a-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="3900a-105">它會繼續工作，但會造成效能上的負面影響。</span><span class="sxs-lookup"><span data-stu-id="3900a-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="3900a-106">請改用[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="3900a-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3900a-107">語法</span><span class="sxs-lookup"><span data-stu-id="3900a-107">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3900a-108">參數</span><span class="sxs-lookup"><span data-stu-id="3900a-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="3900a-109">在傳回之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="3900a-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3900a-110">備註</span><span class="sxs-lookup"><span data-stu-id="3900a-110">Remarks</span></span>  
 <span data-ttu-id="3900a-111">`FunctionLeave` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="3900a-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="3900a-112">此執行必須使用 `__declspec`（`naked`）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="3900a-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3900a-113">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="3900a-113">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="3900a-114">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="3900a-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="3900a-115">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="3900a-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3900a-116">`FunctionLeave` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="3900a-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3900a-117">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="3900a-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3900a-118">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionLeave` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="3900a-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="3900a-119">此外，`FunctionLeave` 函式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="3900a-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3900a-120">需求</span><span class="sxs-lookup"><span data-stu-id="3900a-120">Requirements</span></span>  
 <span data-ttu-id="3900a-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3900a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3900a-122">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="3900a-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3900a-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3900a-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3900a-124">**.NET Framework 版本：** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="3900a-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3900a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="3900a-125">See also</span></span>

- [<span data-ttu-id="3900a-126">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="3900a-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="3900a-127">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="3900a-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="3900a-128">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="3900a-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="3900a-129">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="3900a-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="3900a-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3900a-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
