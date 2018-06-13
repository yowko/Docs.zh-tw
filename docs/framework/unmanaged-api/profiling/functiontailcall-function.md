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
ms.openlocfilehash: 11cf96f5957d41e0647c309a7b0bb08fc9b31c91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452100"
---
# <a name="functiontailcall-function"></a><span data-ttu-id="3d692-102">FunctionTailcall 函式</span><span class="sxs-lookup"><span data-stu-id="3d692-102">FunctionTailcall Function</span></span>
<span data-ttu-id="3d692-103">通知分析工具目前執行函式即將執行對另一個函式的 tail 呼叫。</span><span class="sxs-lookup"><span data-stu-id="3d692-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d692-104">`FunctionTailcall`函式.NET Framework 2.0 版中已被取代。</span><span class="sxs-lookup"><span data-stu-id="3d692-104">The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="3d692-105">它將繼續運作，但會產生對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="3d692-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="3d692-106">使用[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="3d692-106">Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d692-107">語法</span><span class="sxs-lookup"><span data-stu-id="3d692-107">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d692-108">參數</span><span class="sxs-lookup"><span data-stu-id="3d692-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="3d692-109">[in]目前執行的函式進行呼叫的結尾的識別項。</span><span class="sxs-lookup"><span data-stu-id="3d692-109">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d692-110">備註</span><span class="sxs-lookup"><span data-stu-id="3d692-110">Remarks</span></span>  
 <span data-ttu-id="3d692-111">Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回做 tail 呼叫的函式的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3d692-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="3d692-112">這表示[FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)回呼不會發行目標的 tail 呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="3d692-112">This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="3d692-113">`FunctionTailcall`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="3d692-113">The `FunctionTailcall` function is a callback; you must implement it.</span></span> <span data-ttu-id="3d692-114">實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="3d692-114">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="3d692-115">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="3d692-115">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="3d692-116">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="3d692-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="3d692-117">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="3d692-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="3d692-118">實作`FunctionTailcall`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3d692-118">The implementation of `FunctionTailcall` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="3d692-119">實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="3d692-119">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="3d692-120">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionTailcall`傳回。</span><span class="sxs-lookup"><span data-stu-id="3d692-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.</span></span>  
  
 <span data-ttu-id="3d692-121">此外，`FunctionTailcall`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="3d692-121">Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d692-122">需求</span><span class="sxs-lookup"><span data-stu-id="3d692-122">Requirements</span></span>  
 <span data-ttu-id="3d692-123">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d692-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d692-124">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="3d692-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3d692-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d692-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d692-126">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="3d692-126">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d692-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d692-127">See Also</span></span>  
 [<span data-ttu-id="3d692-128">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="3d692-128">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="3d692-129">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="3d692-129">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="3d692-130">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="3d692-130">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="3d692-131">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="3d692-131">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
