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
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175183"
---
# <a name="functiontailcall2-function"></a><span data-ttu-id="9390e-102">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="9390e-102">FunctionTailcall2 Function</span></span>
<span data-ttu-id="9390e-103">通知探測器當前執行的函數即將對另一個函數執行尾調用，並提供有關堆疊幀的資訊。</span><span class="sxs-lookup"><span data-stu-id="9390e-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9390e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9390e-104">Syntax</span></span>  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9390e-105">參數</span><span class="sxs-lookup"><span data-stu-id="9390e-105">Parameters</span></span>

- `funcId`

  <span data-ttu-id="9390e-106">\[in] 即將進行尾調用的當前執行函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9390e-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `clientData`

  <span data-ttu-id="9390e-107">\[in] 重新映射的函數識別碼，探測器以前通過函數[IDMapper](functionidmapper-function.md)指定，該識別碼是當前正在執行的函數，該函數即將進行尾調用。</span><span class="sxs-lookup"><span data-stu-id="9390e-107">\[in] The remapped function identifier, which the profiler previously specified via [FunctionIDMapper](functionidmapper-function.md), of the currently executing function that is about to make a tail call.</span></span>
  
- `func`

  <span data-ttu-id="9390e-108">\[in]`COR_PRF_FRAME_INFO`指向有關堆疊幀的資訊的值。</span><span class="sxs-lookup"><span data-stu-id="9390e-108">\[in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.</span></span>

  <span data-ttu-id="9390e-109">探測器應將此視為不透明控制碼，可在[ICorProfilerInfo2 中傳回執行引擎：：get功能Info2](icorprofilerinfo2-getfunctioninfo2-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="9390e-109">The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) method.</span></span>

## <a name="remarks"></a><span data-ttu-id="9390e-110">備註</span><span class="sxs-lookup"><span data-stu-id="9390e-110">Remarks</span></span>  
 <span data-ttu-id="9390e-111">尾調用的目標函數將使用當前堆疊幀，並將直接返回到發出尾調用的函數的調用方。</span><span class="sxs-lookup"><span data-stu-id="9390e-111">The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call.</span></span> <span data-ttu-id="9390e-112">這意味著不會為作為尾調用目標的函數發出[函數Leave2](functionleave2-function.md)回檔。</span><span class="sxs-lookup"><span data-stu-id="9390e-112">This means that a [FunctionLeave2](functionleave2-function.md) callback will not be issued for a function that is the target of a tail call.</span></span>  
  
 <span data-ttu-id="9390e-113">函數返回後`FunctionTailcall2`，`func`參數的值無效，因為該值可能會更改或銷毀。</span><span class="sxs-lookup"><span data-stu-id="9390e-113">The value of the `func` parameter is not valid after the `FunctionTailcall2` function returns because the value may change or be destroyed.</span></span>  
  
 <span data-ttu-id="9390e-114">函數`FunctionTailcall2`是回檔;你必須實現它。</span><span class="sxs-lookup"><span data-stu-id="9390e-114">The `FunctionTailcall2` function is a callback; you must implement it.</span></span> <span data-ttu-id="9390e-115">實現必須使用`__declspec`（`naked`） 存儲類屬性。</span><span class="sxs-lookup"><span data-stu-id="9390e-115">The implementation must use the `__declspec`(`naked`) storage-class attribute.</span></span>  
  
 <span data-ttu-id="9390e-116">在調用此函數之前，執行引擎不會保存任何寄存器。</span><span class="sxs-lookup"><span data-stu-id="9390e-116">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="9390e-117">進入時，必須保存您使用的所有寄存器，包括浮點單元 （FPU） 中的寄存器。</span><span class="sxs-lookup"><span data-stu-id="9390e-117">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="9390e-118">在退出時，必須通過彈出其調用方推送的所有參數來還原堆疊。</span><span class="sxs-lookup"><span data-stu-id="9390e-118">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="9390e-119">的實現不應`FunctionTailcall2`阻塞，因為它將延遲垃圾回收。</span><span class="sxs-lookup"><span data-stu-id="9390e-119">The implementation of `FunctionTailcall2` should not block because it will delay garbage collection.</span></span> <span data-ttu-id="9390e-120">實現不應嘗試垃圾回收，因為堆疊可能未處於垃圾回收友好狀態。</span><span class="sxs-lookup"><span data-stu-id="9390e-120">The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="9390e-121">如果嘗試垃圾回收，運行時將阻塞，直到`FunctionTailcall2`返回。</span><span class="sxs-lookup"><span data-stu-id="9390e-121">If a garbage collection is attempted, the runtime will block until `FunctionTailcall2` returns.</span></span>  
  
 <span data-ttu-id="9390e-122">此外，`FunctionTailcall2`該函數不得調用託管代碼，或以任何方式導致託管記憶體分配。</span><span class="sxs-lookup"><span data-stu-id="9390e-122">Also, the `FunctionTailcall2` function must not call into managed code or in any way cause a managed memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9390e-123">需求</span><span class="sxs-lookup"><span data-stu-id="9390e-123">Requirements</span></span>  
 <span data-ttu-id="9390e-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9390e-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9390e-125">**標題：** 科爾普羅普.伊德爾</span><span class="sxs-lookup"><span data-stu-id="9390e-125">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="9390e-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9390e-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9390e-127">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9390e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9390e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9390e-128">See also</span></span>

- [<span data-ttu-id="9390e-129">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="9390e-129">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="9390e-130">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="9390e-130">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="9390e-131">SetEnterLeaveFunctionHooks2 方法</span><span class="sxs-lookup"><span data-stu-id="9390e-131">SetEnterLeaveFunctionHooks2 Method</span></span>](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [<span data-ttu-id="9390e-132">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="9390e-132">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
