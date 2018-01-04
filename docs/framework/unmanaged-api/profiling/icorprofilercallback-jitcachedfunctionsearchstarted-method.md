---
title: "ICorProfilerCallback::JITCachedFunctionSearchStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2208a1a1637b3bb8dd7d7963ab806aeae7921dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="a9150-102">ICorProfilerCallback::JITCachedFunctionSearchStarted 方法</span><span class="sxs-lookup"><span data-stu-id="a9150-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="a9150-103">通知分析工具已用於先前使用原生映像產生器 (NGen.exe) 所編譯的函式中開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="a9150-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9150-104">語法</span><span class="sxs-lookup"><span data-stu-id="a9150-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9150-105">參數</span><span class="sxs-lookup"><span data-stu-id="a9150-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a9150-106">[in]正在執行搜尋函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="a9150-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="a9150-107">[out]`true`如果執行引擎應該使用快取的版本的函式 （如果有的話），否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="a9150-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="a9150-108">如果值為`false`，執行引擎 JIT 編譯的函式，而不是使用不是 JIT 編譯的版本。</span><span class="sxs-lookup"><span data-stu-id="a9150-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9150-109">備註</span><span class="sxs-lookup"><span data-stu-id="a9150-109">Remarks</span></span>  
 <span data-ttu-id="a9150-110">在.NET Framework 2.0 版中，`JITCachedFunctionSearchStarted`和[icorprofilercallback:: Jitcachedfunctionsearchfinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)回呼將不會進行一般 NGen 映像中的所有函式。</span><span class="sxs-lookup"><span data-stu-id="a9150-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="a9150-111">只最佳化的設定檔的 NGen 映像將映像中產生的所有函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="a9150-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="a9150-112">不過，額外負擔，因為分析工具應該要求程式碼剖析工具最佳化 NGen 影像才想要使用這些回呼強制將函式編譯在 just-in-time (JIT)。</span><span class="sxs-lookup"><span data-stu-id="a9150-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="a9150-113">否則，分析工具應該收集的資訊函式使用延遲的策略。</span><span class="sxs-lookup"><span data-stu-id="a9150-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="a9150-114">程式碼剖析工具必須支援分析的應用程式的多個執行緒會呼叫同時相同方法的情況。</span><span class="sxs-lookup"><span data-stu-id="a9150-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="a9150-115">例如，執行緒的呼叫`JITCachedFunctionSearchStarted`和分析工具會藉由設定回應*pbUseCachedFunction*為 FALSE，以強制執行 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="a9150-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="a9150-116">然後會呼叫的執行緒[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)和[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="a9150-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="a9150-117">現在執行緒 B 呼叫`JITCachedFunctionSearchStarted`相同的函式。</span><span class="sxs-lookup"><span data-stu-id="a9150-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="a9150-118">即使分析工具有另外註明其進行 JIT 編譯函式的目的，分析工具收到第二個回呼，因為執行緒 B 在分析工具已經回應執行緒的呼叫之前，會將傳送回呼`JITCachedFunctionSearchStarted`。</span><span class="sxs-lookup"><span data-stu-id="a9150-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="a9150-119">執行緒的呼叫順序取決於執行緒的排程。</span><span class="sxs-lookup"><span data-stu-id="a9150-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="a9150-120">當分析工具收到重複的回撥時，它必須設定所參考的值`pbUseCachedFunction`為相同的值為所有重複的回呼。</span><span class="sxs-lookup"><span data-stu-id="a9150-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="a9150-121">也就是說，當`JITCachedFunctionSearchStarted`多次呼叫具有相同`functionId`值，分析工具必須回應相同的每一次。</span><span class="sxs-lookup"><span data-stu-id="a9150-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9150-122">需求</span><span class="sxs-lookup"><span data-stu-id="a9150-122">Requirements</span></span>  
 <span data-ttu-id="a9150-123">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a9150-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9150-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a9150-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a9150-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9150-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9150-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9150-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9150-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="a9150-127">See Also</span></span>  
 [<span data-ttu-id="a9150-128">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="a9150-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
