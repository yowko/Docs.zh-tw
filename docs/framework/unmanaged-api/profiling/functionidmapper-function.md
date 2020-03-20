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
ms.openlocfilehash: 0cf2014d7007593c51868eff0b488fdab136e362
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175170"
---
# <a name="functionidmapper-function"></a><span data-ttu-id="36bc4-102">FunctionIDMapper 函式</span><span class="sxs-lookup"><span data-stu-id="36bc4-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="36bc4-103">通知探測器，函數的給定識別碼可以重新映射到要用於該函數[的函數Enter2、](functionenter2-function.md)[函數Leave2](functionleave2-function.md)和[函數尾聲2](functiontailcall2-function.md)回檔中使用的替代 ID。</span><span class="sxs-lookup"><span data-stu-id="36bc4-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](functionenter2-function.md), [FunctionLeave2](functionleave2-function.md), and [FunctionTailcall2](functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="36bc4-104">`FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="36bc4-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36bc4-105">語法</span><span class="sxs-lookup"><span data-stu-id="36bc4-105">Syntax</span></span>  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36bc4-106">參數</span><span class="sxs-lookup"><span data-stu-id="36bc4-106">Parameters</span></span>

- `funcId`

  <span data-ttu-id="36bc4-107">\[in] 要重新映射的函數識別碼。</span><span class="sxs-lookup"><span data-stu-id="36bc4-107">\[in] The function identifier to be remapped.</span></span>

- `pbHookFunction`

  <span data-ttu-id="36bc4-108">\[out_ 指向探測器`true`在要接收`FunctionEnter2`時`FunctionLeave2`設置的值的指標， `FunctionTailcall2`否則，它將此值設置為`false`。</span><span class="sxs-lookup"><span data-stu-id="36bc4-108">\[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>

## <a name="return-value"></a><span data-ttu-id="36bc4-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="36bc4-109">Return Value</span></span>  
 <span data-ttu-id="36bc4-110">分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。</span><span class="sxs-lookup"><span data-stu-id="36bc4-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="36bc4-111">傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。</span><span class="sxs-lookup"><span data-stu-id="36bc4-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="36bc4-112">否則，空傳回值將生成不可預知的結果，包括可能停止該過程。</span><span class="sxs-lookup"><span data-stu-id="36bc4-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36bc4-113">備註</span><span class="sxs-lookup"><span data-stu-id="36bc4-113">Remarks</span></span>  
 <span data-ttu-id="36bc4-114">該`FunctionIDMapper`函數是回檔。</span><span class="sxs-lookup"><span data-stu-id="36bc4-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="36bc4-115">探測器實現了它將函數 ID 重新映射到對探測器更有用的其他識別碼。</span><span class="sxs-lookup"><span data-stu-id="36bc4-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="36bc4-116">返回`FunctionIDMapper`用於任何給定函數的備用 ID。</span><span class="sxs-lookup"><span data-stu-id="36bc4-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="36bc4-117">然後，執行引擎通過將此備用 ID（除了傳統的函數`clientData`ID）傳遞給`FunctionEnter2`、`FunctionLeave2`和`FunctionTailcall2`掛鉤參數中的探測器來標識為其調用掛鉤的功能來回應探測器的請求。</span><span class="sxs-lookup"><span data-stu-id="36bc4-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="36bc4-118">您可以使用[ICorProfilerInfo：：Set功能IDMapper](icorprofilerinfo-setfunctionidmapper-method.md)方法來指定`FunctionIDMapper`函數的實現。</span><span class="sxs-lookup"><span data-stu-id="36bc4-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="36bc4-119">您只能調用該方法`ICorProfilerInfo::SetFunctionIDMapper`一次，我們建議您在[ICorProfiler 回檔：：初始化](icorprofilercallback-initialize-method.md)回檔中調用該方法。</span><span class="sxs-lookup"><span data-stu-id="36bc4-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="36bc4-120">預設情況下，假定使用[ICorProfilerInfo：：setEventMask](icorprofilerinfo-seteventmask-method.md)設置COR_PRF_MONITOR_ENTERLEAVE標誌的探測器，並且通過[ICorProfilerInfo 設置掛鉤：設置EnterLeave函數Hooks](icorprofilerinfo-setenterleavefunctionhooks-method.md)或[ICorProfilerInfo2：SetEnterLeave函數Hooks2，](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)應接收 每個函數的`FunctionEnter2`、`FunctionLeave2`和`FunctionTailcall2`回檔。</span><span class="sxs-lookup"><span data-stu-id="36bc4-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="36bc4-121">但是，探測器可以通過`FunctionIDMapper`設置為`pbHookFunction`有選擇地避免接收某些函數的回檔`false`。</span><span class="sxs-lookup"><span data-stu-id="36bc4-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="36bc4-122">探測器應容忍設定檔應用程式的多個執行緒同時調用同一方法/函數的情況。</span><span class="sxs-lookup"><span data-stu-id="36bc4-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="36bc4-123">在這種情況下，探測器可能會收到同`FunctionIDMapper``FunctionID`一的多個回檔。</span><span class="sxs-lookup"><span data-stu-id="36bc4-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="36bc4-124">當同調用多次回檔時，探測器應確定應從此回檔返回相同的`FunctionID`值。</span><span class="sxs-lookup"><span data-stu-id="36bc4-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36bc4-125">需求</span><span class="sxs-lookup"><span data-stu-id="36bc4-125">Requirements</span></span>  
 <span data-ttu-id="36bc4-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="36bc4-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36bc4-127">**標題：** 科爾普羅普.伊德爾</span><span class="sxs-lookup"><span data-stu-id="36bc4-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="36bc4-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36bc4-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36bc4-129">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36bc4-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bc4-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36bc4-130">See also</span></span>

- [<span data-ttu-id="36bc4-131">SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="36bc4-131">SetFunctionIDMapper Method</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="36bc4-132">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="36bc4-132">FunctionIDMapper2 Function</span></span>](functionidmapper2-function.md)
- [<span data-ttu-id="36bc4-133">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="36bc4-133">FunctionEnter2 Function</span></span>](functionenter2-function.md)
- [<span data-ttu-id="36bc4-134">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="36bc4-134">FunctionLeave2 Function</span></span>](functionleave2-function.md)
- [<span data-ttu-id="36bc4-135">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="36bc4-135">FunctionTailcall2 Function</span></span>](functiontailcall2-function.md)
- [<span data-ttu-id="36bc4-136">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="36bc4-136">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
