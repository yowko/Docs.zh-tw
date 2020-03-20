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
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177055"
---
# <a name="functionenter2-function"></a><span data-ttu-id="7769d-102">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="7769d-102">FunctionEnter2 Function</span></span>
<span data-ttu-id="7769d-103">通知探測器控制項正在傳遞到函數，並提供有關堆疊幀和函數參數的資訊。</span><span class="sxs-lookup"><span data-stu-id="7769d-103">Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments.</span></span> <span data-ttu-id="7769d-104">此函數取代[函數Enter](functionenter-function.md)函數。</span><span class="sxs-lookup"><span data-stu-id="7769d-104">This function supersedes the [FunctionEnter](functionenter-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7769d-105">語法</span><span class="sxs-lookup"><span data-stu-id="7769d-105">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7769d-106">參數</span><span class="sxs-lookup"><span data-stu-id="7769d-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="7769d-107">\[in] 傳遞給控制項的函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7769d-107">\[in] The identifier of the function to which control is passed.</span></span>

- `clientData`

  <span data-ttu-id="7769d-108">\[in] 重新映射的函數識別碼，探測器以前使用[函數 IDMapper](functionidmapper-function.md)函數指定該識別碼。</span><span class="sxs-lookup"><span data-stu-id="7769d-108">\[in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](functionidmapper-function.md) function.</span></span>
  
- `func`

  <span data-ttu-id="7769d-109">\[in]`COR_PRF_FRAME_INFO`指向有關堆疊幀的資訊的值。</span><span class="sxs-lookup"><span data-stu-id="7769d-109">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>
  
  <span data-ttu-id="7769d-110">探測器應將此視為不透明控制碼，可在[ICorProfilerInfo2 中傳回執行引擎：：get功能Info2](icorprofilerinfo2-getfunctioninfo2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="7769d-110">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>  
  
- `argumentInfo`

  <span data-ttu-id="7769d-111">\[in] 指向[COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md)結構的指標，用於指定函數參數的記憶體中的位置。</span><span class="sxs-lookup"><span data-stu-id="7769d-111">\[in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.</span></span>

  <span data-ttu-id="7769d-112">為了訪問參數資訊，`COR_PRF_ENABLE_FUNCTION_ARGS`必須設置標誌。</span><span class="sxs-lookup"><span data-stu-id="7769d-112">In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set.</span></span> <span data-ttu-id="7769d-113">探測器可以使用[ICorProfilerInfo：：SetEventMask](icorprofilerinfo-seteventmask-method.md)方法設置事件標誌。</span><span class="sxs-lookup"><span data-stu-id="7769d-113">The profiler can use the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the event flags.</span></span>

## <a name="remarks"></a><span data-ttu-id="7769d-114">備註</span><span class="sxs-lookup"><span data-stu-id="7769d-114">Remarks</span></span>  
 <span data-ttu-id="7769d-115">`func`和`argumentInfo`參數的值在`FunctionEnter2`函數返回後無效，因為值可能會更改或被銷毀。</span><span class="sxs-lookup"><span data-stu-id="7769d-115">The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.</span></span>  
  
 <span data-ttu-id="7769d-116">函數`FunctionEnter2`是回檔;你必須實現它。</span><span class="sxs-lookup"><span data-stu-id="7769d-116">The `FunctionEnter2` function is a callback; you must implement it.</span></span> <span data-ttu-id="7769d-117">實現必須使用`__declspec`（`naked`） 存儲類屬性。</span><span class="sxs-lookup"><span data-stu-id="7769d-117">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="7769d-118">在調用此函數之前，執行引擎不會保存任何寄存器。</span><span class="sxs-lookup"><span data-stu-id="7769d-118">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="7769d-119">進入時，必須保存您使用的所有寄存器，包括浮點單元 （FPU） 中的寄存器。</span><span class="sxs-lookup"><span data-stu-id="7769d-119">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="7769d-120">在退出時，必須通過彈出其調用方推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="7769d-120">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="7769d-121">的實現不應`FunctionEnter2`阻塞，因為它將延遲垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="7769d-121">The implementation of `FunctionEnter2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="7769d-122">實現不應嘗試垃圾回收，因為堆疊可能未處於垃圾回收友好狀態。</span><span class="sxs-lookup"><span data-stu-id="7769d-122">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="7769d-123">如果嘗試垃圾回收，運行時將阻塞，直到`FunctionEnter2`返回。</span><span class="sxs-lookup"><span data-stu-id="7769d-123">If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.</span></span>  
  
 <span data-ttu-id="7769d-124">此外，`FunctionEnter2`該函數不得調用託管代碼，或以任何方式導致託管記憶體分配。</span><span class="sxs-lookup"><span data-stu-id="7769d-124">Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7769d-125">需求</span><span class="sxs-lookup"><span data-stu-id="7769d-125">Requirements</span></span>  
 <span data-ttu-id="7769d-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7769d-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7769d-127">**標題：** 科爾普羅普.伊德爾</span><span class="sxs-lookup"><span data-stu-id="7769d-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="7769d-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7769d-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7769d-129">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7769d-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7769d-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7769d-130">See also</span></span>

- [<span data-ttu-id="7769d-131">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="7769d-131">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="7769d-132">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="7769d-132">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="7769d-133">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="7769d-133">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="7769d-134">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="7769d-134">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
