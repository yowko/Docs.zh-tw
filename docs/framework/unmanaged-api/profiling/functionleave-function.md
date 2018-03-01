---
title: "FunctionLeave 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 14b8c1c5d36178e672bee363a192cd4eae435467
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="functionleave-function"></a><span data-ttu-id="62703-102">FunctionLeave 函式</span><span class="sxs-lookup"><span data-stu-id="62703-102">FunctionLeave Function</span></span>
<span data-ttu-id="62703-103">通知分析工具函式是要傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="62703-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="62703-104">`FunctionLeave`函式.NET Framework 2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="62703-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="62703-105">它將繼續運作，但會產生對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="62703-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="62703-106">使用[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="62703-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62703-107">語法</span><span class="sxs-lookup"><span data-stu-id="62703-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62703-108">參數</span><span class="sxs-lookup"><span data-stu-id="62703-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="62703-109">[in]函式傳回的識別項。</span><span class="sxs-lookup"><span data-stu-id="62703-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62703-110">備註</span><span class="sxs-lookup"><span data-stu-id="62703-110">Remarks</span></span>  
 <span data-ttu-id="62703-111">`FunctionLeave`函式是回呼，您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="62703-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="62703-112">實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="62703-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="62703-113">執行引擎不會呼叫此函數之前儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="62703-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="62703-114">進入時，您必須儲存所有您使用，包括浮點數的單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="62703-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="62703-115">結束時，您必須還原堆疊取出關閉推入其呼叫端的所有參數。</span><span class="sxs-lookup"><span data-stu-id="62703-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="62703-116">實作`FunctionLeave`不應該封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="62703-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="62703-117">實作不應嘗試在記憶體回收，因為堆疊可能不在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="62703-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="62703-118">如果嘗試在記憶體回收時，執行階段將會封鎖直到`FunctionLeave`傳回。</span><span class="sxs-lookup"><span data-stu-id="62703-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="62703-119">此外，`FunctionLeave`函式不可以呼叫至 managed 程式碼或任何方式發生原因的 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="62703-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62703-120">需求</span><span class="sxs-lookup"><span data-stu-id="62703-120">Requirements</span></span>  
 <span data-ttu-id="62703-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62703-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62703-122">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="62703-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="62703-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62703-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62703-124">**.NET framework 版本：** 1.1、 1.0</span><span class="sxs-lookup"><span data-stu-id="62703-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62703-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="62703-125">See Also</span></span>  
 [<span data-ttu-id="62703-126">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="62703-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="62703-127">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="62703-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="62703-128">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="62703-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="62703-129">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="62703-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [<span data-ttu-id="62703-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="62703-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
