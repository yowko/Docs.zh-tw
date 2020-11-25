---
title: FunctionEnter3 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter3
helpviewer_keywords:
- FunctionEnter3 function [.NET Framework profiling]
ms.assetid: ef782c53-dae7-4990-b4ad-fddb1e690d4e
topic_type:
- apiref
ms.openlocfilehash: 98a821eabb393d8b5042647e6ef6ffce7ab10783
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722878"
---
# <a name="functionenter3-function"></a><span data-ttu-id="201a2-102">FunctionEnter3 函式</span><span class="sxs-lookup"><span data-stu-id="201a2-102">FunctionEnter3 Function</span></span>

<span data-ttu-id="201a2-103">通知分析工具，控制項正在傳遞至函式。</span><span class="sxs-lookup"><span data-stu-id="201a2-103">Notifies the profiler that control is being passed to a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="201a2-104">語法</span><span class="sxs-lookup"><span data-stu-id="201a2-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="201a2-105">參數</span><span class="sxs-lookup"><span data-stu-id="201a2-105">Parameters</span></span>

- `functionOrRemappedID`

  <span data-ttu-id="201a2-106">\[in] 要傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="201a2-106">\[in] The identifier of the function to which control is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="201a2-107">備註</span><span class="sxs-lookup"><span data-stu-id="201a2-107">Remarks</span></span>  

 <span data-ttu-id="201a2-108">回呼函式 `FunctionEnter3` 會在呼叫函數時通知分析工具，但不支援引數檢查。</span><span class="sxs-lookup"><span data-stu-id="201a2-108">The `FunctionEnter3` callback function notifies the profiler as functions are being called, but does not support argument inspection.</span></span> <span data-ttu-id="201a2-109">使用 [ICorProfilerInfo3：： SetEnterLeaveFunctionHooks3 方法](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) 來註冊此函式的實作為。</span><span class="sxs-lookup"><span data-stu-id="201a2-109">Use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="201a2-110">`FunctionEnter3`函數是回呼; 您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="201a2-110">The `FunctionEnter3` function is a callback; you must implement it.</span></span> <span data-ttu-id="201a2-111">實作為必須使用 `__declspec(naked)` 儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="201a2-111">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="201a2-112">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="201a2-112">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="201a2-113">輸入時，您必須儲存使用的所有暫存器，包括浮點數單位中的所有暫存器 (FPU) 。</span><span class="sxs-lookup"><span data-stu-id="201a2-113">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="201a2-114">在結束時，您必須藉由關閉呼叫端所推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="201a2-114">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="201a2-115">需求</span><span class="sxs-lookup"><span data-stu-id="201a2-115">Requirements</span></span>  

 <span data-ttu-id="201a2-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="201a2-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="201a2-117">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="201a2-117">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="201a2-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="201a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="201a2-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="201a2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="201a2-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="201a2-120">See also</span></span>

- [<span data-ttu-id="201a2-121">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="201a2-121">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="201a2-122">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="201a2-122">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="201a2-123">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="201a2-123">FunctionEnter3WithInfo</span></span>](functionenter3withinfo-function.md)
- [<span data-ttu-id="201a2-124">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="201a2-124">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="201a2-125">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="201a2-125">FunctionTailcall3WithInfo</span></span>](functiontailcall3withinfo-function.md)
- [<span data-ttu-id="201a2-126">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="201a2-126">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="201a2-127">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="201a2-127">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="201a2-128">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="201a2-128">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="201a2-129">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="201a2-129">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="201a2-130">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="201a2-130">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
