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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b1fe219c4c852792390b48b0ea4d38adb702281
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218884"
---
# <a name="functionleave-function"></a><span data-ttu-id="77f7f-102">FunctionLeave 函式</span><span class="sxs-lookup"><span data-stu-id="77f7f-102">FunctionLeave Function</span></span>
<span data-ttu-id="77f7f-103">通知分析工具函式會傳回給呼叫者。</span><span class="sxs-lookup"><span data-stu-id="77f7f-103">Notifies the profiler that a function is about to return to the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77f7f-104">`FunctionLeave`函式在.NET Framework 2.0 中已被取代。</span><span class="sxs-lookup"><span data-stu-id="77f7f-104">The `FunctionLeave` function is deprecated in the .NET Framework 2.0.</span></span> <span data-ttu-id="77f7f-105">它會繼續運作，但會對效能帶來負面影響。</span><span class="sxs-lookup"><span data-stu-id="77f7f-105">It will continue to work, but will incur a performance penalty.</span></span> <span data-ttu-id="77f7f-106">使用[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)函式。</span><span class="sxs-lookup"><span data-stu-id="77f7f-106">Use the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) function instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f7f-107">語法</span><span class="sxs-lookup"><span data-stu-id="77f7f-107">Syntax</span></span>  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77f7f-108">參數</span><span class="sxs-lookup"><span data-stu-id="77f7f-108">Parameters</span></span>  
 `funcID`  
 <span data-ttu-id="77f7f-109">[in]函式傳回的識別項。</span><span class="sxs-lookup"><span data-stu-id="77f7f-109">[in] The identifier of the function that is returning.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77f7f-110">備註</span><span class="sxs-lookup"><span data-stu-id="77f7f-110">Remarks</span></span>  
 <span data-ttu-id="77f7f-111">`FunctionLeave`函式是回呼; 您必須實作它。</span><span class="sxs-lookup"><span data-stu-id="77f7f-111">The `FunctionLeave` function is a callback; you must implement it.</span></span> <span data-ttu-id="77f7f-112">的實作必須使用`__declspec`(`naked`) 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="77f7f-112">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="77f7f-113">呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="77f7f-113">The execution engine does not save any registers before calling this function.</span></span>  
  
-   <span data-ttu-id="77f7f-114">項目，您必須儲存所有您使用，包括與浮點單位 (FPU) 中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="77f7f-114">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
-   <span data-ttu-id="77f7f-115">結束時，您必須還原堆疊驅離其呼叫端所推送的所有參數。</span><span class="sxs-lookup"><span data-stu-id="77f7f-115">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="77f7f-116">實作`FunctionLeave`應該不會封鎖，因為它將會延遲記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="77f7f-116">The implementation of `FunctionLeave` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="77f7f-117">實作不應嘗試進行記憶體回收，因為堆疊可能無法在記憶體回收方便集合的狀態。</span><span class="sxs-lookup"><span data-stu-id="77f7f-117">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="77f7f-118">如果嘗試進行記憶體回收，則執行階段將會封鎖直到`FunctionLeave`傳回。</span><span class="sxs-lookup"><span data-stu-id="77f7f-118">If a garbage collection is attempted, the runtime will block until `FunctionLeave` returns.</span></span>  
  
 <span data-ttu-id="77f7f-119">此外，`FunctionLeave`函式不能呼叫至 managed 程式碼，或以任何方式造成 managed 的記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="77f7f-119">Also, the `FunctionLeave` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f7f-120">需求</span><span class="sxs-lookup"><span data-stu-id="77f7f-120">Requirements</span></span>  
 <span data-ttu-id="77f7f-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77f7f-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77f7f-122">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="77f7f-122">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="77f7f-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77f7f-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77f7f-124">**.NET framework 版本：** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="77f7f-124">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f7f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f7f-125">See also</span></span>

- [<span data-ttu-id="77f7f-126">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="77f7f-126">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [<span data-ttu-id="77f7f-127">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="77f7f-127">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [<span data-ttu-id="77f7f-128">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="77f7f-128">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [<span data-ttu-id="77f7f-129">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="77f7f-129">SetEnterLeaveFunctionHooks2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="77f7f-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="77f7f-130">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
