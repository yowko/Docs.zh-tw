---
title: FunctionEnter2 函式
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 6cd35c180b8a322b3402b050c6d6840073010b1f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866979"
---
# <a name="functionenter2-function"></a><span data-ttu-id="ccbe9-102">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="ccbe9-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="ccbe9-103">通知分析工具控制項正傳遞至函式，並提供堆疊框架和函式引數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="ccbe9-104">此函式會取代[FunctionEnter](functionenter-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccbe9-105">語法</span><span class="sxs-lookup"><span data-stu-id="ccbe9-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccbe9-106">參數</span><span class="sxs-lookup"><span data-stu-id="ccbe9-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="ccbe9-107">中的 \[]）傳遞控制項的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="ccbe9-108">\[in]）重新對應的函式識別碼，也就是先前使用[FunctionIDMapper](functionidmapper-function.md)函數指定的 profiler。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="ccbe9-109">\[in]） `COR_PRF_FRAME_INFO` 值，指向堆疊框架的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="ccbe9-110">分析工具應該將此視為不透明的控制碼，以便在[ICorProfilerInfo2：： GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)方法中傳回給執行引擎。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="ccbe9-111">\[in]） [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)結構的指標，指定函數引數的記憶體位置。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="ccbe9-112">若要存取引數資訊，必須設定 `COR_PRF_ENABLE_FUNCTION_ARGS` 旗標。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="ccbe9-113">分析工具可以使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法來設定事件旗標。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="ccbe9-114">備註</span><span class="sxs-lookup"><span data-stu-id="ccbe9-114">Remarks</span></span>  
 <span data-ttu-id="ccbe9-115">`FunctionEnter2` 函數傳回之後，`func` 和 `argumentInfo` 參數的值無效，因為這些值可能會變更或終結。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="ccbe9-116">`FunctionEnter2` 函數是回呼;您必須加以執行。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="ccbe9-117">此執行必須使用 `__declspec`（`naked`）儲存類別屬性。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="ccbe9-118">在呼叫此函式之前，執行引擎不會儲存任何暫存器。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="ccbe9-119">輸入時，您必須儲存您所使用的所有暫存器，包括浮點單位（FPU）中的暫存器。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="ccbe9-120">結束時，您必須透過關閉其呼叫者推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="ccbe9-121">`FunctionEnter2` 的執行不應該封鎖，因為它會延遲垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="ccbe9-122">執行不應嘗試垃圾收集，因為堆疊可能不會處於垃圾收集的唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="ccbe9-123">如果嘗試垃圾收集，執行時間將會封鎖，直到 `FunctionEnter2` 傳回為止。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="ccbe9-124">此外，`FunctionEnter2` 函式不能呼叫 managed 程式碼，或以任何方式執行 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccbe9-125">需求</span><span class="sxs-lookup"><span data-stu-id="ccbe9-125">Requirements</span></span>  
 <span data-ttu-id="ccbe9-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ccbe9-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccbe9-127">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="ccbe9-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="ccbe9-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccbe9-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccbe9-129">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccbe9-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccbe9-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="ccbe9-130">See also</span></span>

- [<span data-ttu-id="ccbe9-131">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="ccbe9-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="ccbe9-132">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="ccbe9-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="ccbe9-133">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="ccbe9-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="ccbe9-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="ccbe9-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
