---
title: FunctionTailcall2 函式
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a515c2622f81c666523aa012fa1e34e5251c074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452477"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="9b94a-102">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="9b94a-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="9b94a-103">通知分析工具，目前執行函式即將執行對另一個函式的 tail 呼叫，並提供相關的堆疊框架資訊。</span><span class="sxs-lookup"><span data-stu-id="9b94a-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b94a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b94a-104">Syntax</span></span>  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9b94a-105">參數</span><span class="sxs-lookup"><span data-stu-id="9b94a-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="9b94a-106">[in]目前執行的函式進行呼叫的結尾的識別項。</span><span class="sxs-lookup"><span data-stu-id="9b94a-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="9b94a-107">[in]重新對應的函式識別項，透過先前指定的程式碼剖析工具[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)，目前執行的函式即將進行呼叫的結尾。</span><span class="sxs-lookup"><span data-stu-id="9b94a-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="9b94a-108">[in]A`COR_PRF_FRAME_INFO`指向堆疊框架的相關資訊的值。</span><span class="sxs-lookup"><span data-stu-id="9b94a-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="9b94a-109">程式碼剖析工具應該將此視為不透明控制代碼可傳遞回執行引擎中[icorprofilerinfo2:: Getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9b94a-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b94a-110">備註</span><span class="sxs-lookup"><span data-stu-id="9b94a-110">Remarks</span></span>  
 <span data-ttu-id="9b94a-111">Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回做 tail 呼叫的函式的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="9b94a-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="9b94a-112">這表示[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回呼不會發行目標的 tail 呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="9b94a-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="9b94a-113">值`func`參數不是有效之後`FunctionTailcall2`函式傳回，因為可能會變更的值，或被終結。</span><span class="sxs-lookup"><span data-stu-id="9b94a-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="9b94a-114">`FunctionTailcall2`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="9b94a-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="9b94a-115">實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="9b94a-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="9b94a-116">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="9b94a-116">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="9b94a-117">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="9b94a-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="9b94a-118">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="9b94a-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9b94a-119">實作`FunctionTailcall2`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="9b94a-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="9b94a-120">實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="9b94a-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9b94a-121">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionTailcall2`傳回。</span><span class="sxs-lookup"><span data-stu-id="9b94a-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="9b94a-122">此外，`FunctionTailcall2`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="9b94a-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b94a-123">需求</span><span class="sxs-lookup"><span data-stu-id="9b94a-123">Requirements</span></span>  
 <span data-ttu-id="9b94a-124">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9b94a-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b94a-125">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="9b94a-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9b94a-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b94a-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b94a-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b94a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b94a-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b94a-128">See Also</span></span>  
 [<span data-ttu-id="9b94a-129">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="9b94a-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="9b94a-130">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="9b94a-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="9b94a-131">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="9b94a-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="9b94a-132">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="9b94a-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
