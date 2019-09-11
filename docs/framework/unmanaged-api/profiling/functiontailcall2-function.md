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
ms.openlocfilehash: 9495624f7eca57a79518036937a5fb63d01d9c4b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70851217"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="fbcb7-102">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="fbcb7-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="fbcb7-103">通知分析工具，目前正在執行的函式即將執行另一個函式的尾呼叫，並提供堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbcb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="fbcb7-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbcb7-105">參數</span><span class="sxs-lookup"><span data-stu-id="fbcb7-105">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="fbcb7-106">在即將進行 tail 呼叫之目前正在執行之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-106">[in] The identifier of the currently executing function that is about to make a tail call.</span></span>  
  
 `clientData`  
 <span data-ttu-id="fbcb7-107">在程式碼剖析工具先前透過[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)指定的重新對應函式識別碼，這是即將進行 tail 呼叫的目前正在執行之函式。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-107">[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>  
  
 `func`  
 <span data-ttu-id="fbcb7-108">在`COR_PRF_FRAME_INFO`值，指向堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-108">[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>  
  
 <span data-ttu-id="fbcb7-109">分析工具應該將此視為不透明的控制碼，以便在[ICorProfilerInfo2：： GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)方法中傳回給執行引擎。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbcb7-110">備註</span><span class="sxs-lookup"><span data-stu-id="fbcb7-110">Remarks</span></span>  
 <span data-ttu-id="fbcb7-111">Tail 呼叫的目標函式會使用目前的堆疊框架，並會直接傳回呼叫端呼叫之函式的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="fbcb7-112">這表示不會針對做為 tail 呼叫目標的函式發出[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-112">This means that a [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="fbcb7-113">在函式傳回`func` `FunctionTailcall2`之後，參數的值無效，因為此值可能會變更或損毀。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="fbcb7-114">`FunctionTailcall2`函式是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="fbcb7-115">此執行必須使用`__declspec`（`naked`）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="fbcb7-116">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="fbcb7-117">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="fbcb7-118">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="fbcb7-119">的執行`FunctionTailcall2`不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="fbcb7-120">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="fbcb7-121">如果嘗試垃圾收集，執行時間將會封鎖，直到`FunctionTailcall2`傳回為止。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="fbcb7-122">此外，函`FunctionTailcall2`式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbcb7-123">需求</span><span class="sxs-lookup"><span data-stu-id="fbcb7-123">Requirements</span></span>  
 <span data-ttu-id="fbcb7-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fbcb7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbcb7-125">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="fbcb7-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="fbcb7-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fbcb7-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fbcb7-127">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbcb7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbcb7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbcb7-128">See also</span></span>

- [<span data-ttu-id="fbcb7-129">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="fbcb7-129">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="fbcb7-130">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="fbcb7-130">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="fbcb7-131">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="fbcb7-131">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="fbcb7-132">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="fbcb7-132">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
