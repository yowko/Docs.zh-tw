---
title: FunctionIDMapper 函式
ms.date: 03/30/2017
api_name:
- FunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper
helpviewer_keywords:
- FunctionIDMapper function [.NET Framework profiling]
ms.assetid: b8205b60-1893-4303-8cff-7ac5a00892aa
topic_type:
- apiref
ms.openlocfilehash: 17396d3038578c16b74c3717174dc0fa4dc17631
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722839"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="987b4-102">FunctionIDMapper 函式</span><span class="sxs-lookup"><span data-stu-id="987b4-102">FunctionIDMapper Function</span></span>

<span data-ttu-id="987b4-103">通知分析工具，函式的指定識別碼可能會重新對應到替代識別碼，以便用於該函式的 [FunctionEnter2](functionenter2-function.md)、 [FunctionLeave2](functionleave2-function.md)和 [FunctionTailcall2](functiontailcall2-function.md) 回呼中。</span><span class="sxs-lookup"><span data-stu-id="987b4-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="987b4-104">`FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="987b4-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="987b4-105">語法</span><span class="sxs-lookup"><span data-stu-id="987b4-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="987b4-106">參數</span><span class="sxs-lookup"><span data-stu-id="987b4-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="987b4-107">\[in] 要重新對應的函數識別碼。</span><span class="sxs-lookup"><span data-stu-id="987b4-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="987b4-108">\[out：當分析工具 `true` 想要接收、和回呼時，所設定的值 `FunctionEnter2` 指標 `FunctionLeave2` `FunctionTailcall2` ; 否則，它會將此值設定為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="987b4-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="987b4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="987b4-109">Return Value</span></span>  

 <span data-ttu-id="987b4-110">分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。</span><span class="sxs-lookup"><span data-stu-id="987b4-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="987b4-111">傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。</span><span class="sxs-lookup"><span data-stu-id="987b4-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="987b4-112">否則，null 傳回值會產生無法預測的結果，包括可能會停止進程。</span><span class="sxs-lookup"><span data-stu-id="987b4-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="987b4-113">備註</span><span class="sxs-lookup"><span data-stu-id="987b4-113">Remarks</span></span>  

 <span data-ttu-id="987b4-114">`FunctionIDMapper`函數是回呼。</span><span class="sxs-lookup"><span data-stu-id="987b4-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="987b4-115">程式碼剖析工具會執行它，以將函式識別碼重新對應至其他對分析工具更有用的識別碼。</span><span class="sxs-lookup"><span data-stu-id="987b4-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="987b4-116">`FunctionIDMapper`會傳回要用於任何指定函數的替代識別碼。</span><span class="sxs-lookup"><span data-stu-id="987b4-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="987b4-117">然後，執行引擎會藉由將此替代識別碼（除了傳統的函式識別碼）傳遞回分析工具的要求， `clientData` `FunctionEnter2` `FunctionLeave2` 以識別要呼叫攔截器的函式 `FunctionTailcall2` 。</span><span class="sxs-lookup"><span data-stu-id="987b4-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="987b4-118">您可以使用 [ICorProfilerInfo：： SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) 方法來指定函式的實作為 `FunctionIDMapper` 。</span><span class="sxs-lookup"><span data-stu-id="987b4-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="987b4-119">您 `ICorProfilerInfo::SetFunctionIDMapper` 只能呼叫一次此方法，我們建議您在 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md) 回呼中這樣做。</span><span class="sxs-lookup"><span data-stu-id="987b4-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="987b4-120">根據預設，假設分析工具會使用 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)來設定 COR_PRF_MONITOR_ENTERLEAVE 旗標，並透過 [ICorProfilerInfo：： SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) 或 [ICorProfilerInfo2：： SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)設定勾點，則應該接收 `FunctionEnter2` `FunctionLeave2` 每個函數的、和 `FunctionTailcall2` 回呼。</span><span class="sxs-lookup"><span data-stu-id="987b4-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="987b4-121">不過，分析工具可能會藉 `FunctionIDMapper` 由將設定為，以選擇性地避免針對某些函數接收這些回呼 `pbHookFunction` `false` 。</span><span class="sxs-lookup"><span data-stu-id="987b4-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="987b4-122">分析工具應可容忍程式碼剖析應用程式的多個執行緒同時呼叫相同方法/函式的情況。</span><span class="sxs-lookup"><span data-stu-id="987b4-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="987b4-123">在這種情況下，分析工具可能會收到相同的多個 `FunctionIDMapper` 回呼 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="987b4-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="987b4-124">當使用相同的多次呼叫此回呼時，分析工具應該會傳回相同的值 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="987b4-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="987b4-125">需求</span><span class="sxs-lookup"><span data-stu-id="987b4-125">Requirements</span></span>  

 <span data-ttu-id="987b4-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="987b4-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="987b4-127">**標頭：** Corprof.h .idl</span><span class="sxs-lookup"><span data-stu-id="987b4-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="987b4-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="987b4-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="987b4-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="987b4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="987b4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="987b4-130">See also</span></span>

- [<span data-ttu-id="987b4-131">SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="987b4-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="987b4-132">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="987b4-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="987b4-133">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="987b4-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="987b4-134">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="987b4-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="987b4-135">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="987b4-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="987b4-136">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="987b4-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
