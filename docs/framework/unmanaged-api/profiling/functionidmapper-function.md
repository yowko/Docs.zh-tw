---
title: "FunctionIDMapper 函式"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24e48ecb551a5faacc7da94b857b2e260f5aeca0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="functionidmapper-function"></a><span data-ttu-id="543cb-102">FunctionIDMapper 函式</span><span class="sxs-lookup"><span data-stu-id="543cb-102">FunctionIDMapper Function</span></span>
<span data-ttu-id="543cb-103">通知分析工具函式的指定的識別碼可能會重新對應至替代識別碼，以用於[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)， [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)，和[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="543cb-103">Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function.</span></span> <span data-ttu-id="543cb-104">`FunctionIDMapper` 也可讓分析工具指出它是否要接收該函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="543cb-104">`FunctionIDMapper` also enables the profiler to indicate whether it wants to receive callbacks for that function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="543cb-105">語法</span><span class="sxs-lookup"><span data-stu-id="543cb-105">Syntax</span></span>  
  
```  
UINT_PTR __stdcall FunctionIDMapper (  
    [in]  FunctionID  funcId,   
    [out] BOOL       *pbHookFunction  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="543cb-106">參數</span><span class="sxs-lookup"><span data-stu-id="543cb-106">Parameters</span></span>  
 `funcId`  
 <span data-ttu-id="543cb-107">[in] 要重新對應的函式識別項。</span><span class="sxs-lookup"><span data-stu-id="543cb-107">[in] The function identifier to be remapped.</span></span>  
  
 `pbHookFunction`  
 <span data-ttu-id="543cb-108">[out]分析工具會設定為值的指標`true`如果它要接收`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`回呼; 否則它將此值設`false`。</span><span class="sxs-lookup"><span data-stu-id="543cb-108">[out] A pointer to a value that the profiler sets to `true` if it wants to receive `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks; otherwise, it sets this value to `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="543cb-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="543cb-109">Return Value</span></span>  
 <span data-ttu-id="543cb-110">分析工具會傳回一個值，執行引擎會使用該值做為替代函式識別項。</span><span class="sxs-lookup"><span data-stu-id="543cb-110">The profiler returns a value that the execution engine uses as an alternative function identifier.</span></span> <span data-ttu-id="543cb-111">傳回值不可為 null，除非 `false` 傳回在 `pbHookFunction` 中。</span><span class="sxs-lookup"><span data-stu-id="543cb-111">The return value cannot be null unless `false` is returned in `pbHookFunction`.</span></span> <span data-ttu-id="543cb-112">否則，傳回的 null 值會產生無法預期的結果，包括可能暫止處理程序。</span><span class="sxs-lookup"><span data-stu-id="543cb-112">Otherwise, a null return value will produce unpredictable results, including possibly halting the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="543cb-113">備註</span><span class="sxs-lookup"><span data-stu-id="543cb-113">Remarks</span></span>  
 <span data-ttu-id="543cb-114">`FunctionIDMapper`函式是回呼。</span><span class="sxs-lookup"><span data-stu-id="543cb-114">The `FunctionIDMapper` function is a callback.</span></span> <span data-ttu-id="543cb-115">它是由某些其他識別碼，程式碼剖析工具更有用的函式識別碼重新對應的程式碼剖析工具實作。</span><span class="sxs-lookup"><span data-stu-id="543cb-115">It is implemented by the profiler to remap a function ID to some other identifier that is more useful for the profiler.</span></span> <span data-ttu-id="543cb-116">`FunctionIDMapper`傳回要用於指定的函式的替代 ID。</span><span class="sxs-lookup"><span data-stu-id="543cb-116">The `FunctionIDMapper` returns the alternate ID to be used for any given function.</span></span> <span data-ttu-id="543cb-117">執行引擎藉由傳遞回程式碼剖析工具中的這個替代識別碼，除了傳統的函式 ID，然後接受分析工具的要求`clientData`參數`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`攔截程序，來識別正在呼叫攔截函式。</span><span class="sxs-lookup"><span data-stu-id="543cb-117">The execution engine then honors the profiler's request by passing this alternate ID, in addition to the traditional function ID, back to the profiler in the `clientData` parameter of the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` hooks, to identify the function for which the hook is being called.</span></span>  
  
 <span data-ttu-id="543cb-118">您可以使用[icorprofilerinfo:: Setfunctionidmapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)方法，以指定的實作`FunctionIDMapper`函式。</span><span class="sxs-lookup"><span data-stu-id="543cb-118">You can use the [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) method to specify the implementation of the `FunctionIDMapper` function.</span></span> <span data-ttu-id="543cb-119">您可以呼叫`ICorProfilerInfo::SetFunctionIDMapper`方法一次，所以我們建議，請在[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="543cb-119">You can call the `ICorProfilerInfo::SetFunctionIDMapper` method only once, and we recommend that you do so in the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
 <span data-ttu-id="543cb-120">根據預設，它會假設，分析工具，設定 COR_PRF_MONITOR_ENTERLEAVE 旗標使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)，它會設定攔截程序，透過和[icorprofilerinfo:: Setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)或[icorprofilerinfo2:: Setenterleavefunctionhooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)，應該會收到`FunctionEnter2`， `FunctionLeave2`，和`FunctionTailcall2`每個函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="543cb-120">By default, it is assumed that a profiler that sets the COR_PRF_MONITOR_ENTERLEAVE flag by using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md), and which sets hooks via [ICorProfilerInfo::SetEnterLeaveFunctionHooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) or [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), should receive the `FunctionEnter2`, `FunctionLeave2`, and `FunctionTailcall2` callbacks for every function.</span></span> <span data-ttu-id="543cb-121">不過，分析工具可能會實作`FunctionIDMapper`以選擇性地避免特定接收這些回呼函式藉由設定`pbHookFunction`至`false`。</span><span class="sxs-lookup"><span data-stu-id="543cb-121">However, profilers may implement `FunctionIDMapper` to selectively avoid receiving these callbacks for certain functions by setting `pbHookFunction` to `false`.</span></span>  
  
 <span data-ttu-id="543cb-122">程式碼剖析工具應該分析應用程式的多個執行緒所呼叫同時相同的方法/函式的情況下容錯。</span><span class="sxs-lookup"><span data-stu-id="543cb-122">Profilers should be tolerant of cases where multiple threads of a profiled application are calling the same method/function simultaneously.</span></span> <span data-ttu-id="543cb-123">在這種情況下，分析工具可能會收到多個`FunctionIDMapper`相同的回呼`FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="543cb-123">In such cases, the profiler may receive multiple `FunctionIDMapper` callbacks for the same `FunctionID`.</span></span> <span data-ttu-id="543cb-124">程式碼剖析工具應該先確定要從此回呼傳回相同的值，多次呼叫具有相同時`FunctionID`。</span><span class="sxs-lookup"><span data-stu-id="543cb-124">The profiler should be certain to return the same values from this callback when it is called multiple times with the same `FunctionID`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="543cb-125">需求</span><span class="sxs-lookup"><span data-stu-id="543cb-125">Requirements</span></span>  
 <span data-ttu-id="543cb-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="543cb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="543cb-127">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="543cb-127">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="543cb-128">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="543cb-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="543cb-129">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="543cb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="543cb-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="543cb-130">See Also</span></span>  
 [<span data-ttu-id="543cb-131">SetFunctionIDMapper 方法</span><span class="sxs-lookup"><span data-stu-id="543cb-131">SetFunctionIDMapper Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [<span data-ttu-id="543cb-132">FunctionIDMapper2 函式</span><span class="sxs-lookup"><span data-stu-id="543cb-132">FunctionIDMapper2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 [<span data-ttu-id="543cb-133">FunctionEnter2 函式</span><span class="sxs-lookup"><span data-stu-id="543cb-133">FunctionEnter2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [<span data-ttu-id="543cb-134">FunctionLeave2 函式</span><span class="sxs-lookup"><span data-stu-id="543cb-134">FunctionLeave2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [<span data-ttu-id="543cb-135">FunctionTailcall2 函式</span><span class="sxs-lookup"><span data-stu-id="543cb-135">FunctionTailcall2 Function</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [<span data-ttu-id="543cb-136">分析全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="543cb-136">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
