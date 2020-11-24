---
title: ICorProfilerCallback::JITCachedFunctionSearchStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITCachedFunctionSearchStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITCachedFunctionSearchStarted
helpviewer_keywords:
- JITCachedFunctionSearchStarted method [.NET Framework profiling]
- ICorProfilerCallback::JITCachedFunctionSearchStarted method [.NET Framework profiling]
ms.assetid: 5cba642c-0d80-48ee-889d-198c5044d821
topic_type:
- apiref
ms.openlocfilehash: 938da4e3b7cc45c24dcac872ab504755116197a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684001"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="8ef37-102">ICorProfilerCallback::JITCachedFunctionSearchStarted 方法</span><span class="sxs-lookup"><span data-stu-id="8ef37-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>

<span data-ttu-id="8ef37-103">通知分析工具，已開始針對先前使用原生映射產生器 ( # A0) 編譯的函式進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="8ef37-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ef37-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ef37-104">Syntax</span></span>  
  
```cpp  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ef37-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ef37-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="8ef37-106">\[in] 正在執行搜尋的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="8ef37-106">\[in] The ID of the function for which the search is being performed.</span></span>

- `pbUseCachedFunction`

  <span data-ttu-id="8ef37-107">\[out] `true` 如果執行引擎應使用函式的快取版本 (if 可用) ，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="8ef37-107">\[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="8ef37-108">如果值為 `false` ，執行引擎會 JIT 編譯函式，而不是使用非 JIT 編譯的版本。</span><span class="sxs-lookup"><span data-stu-id="8ef37-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="8ef37-109">備註</span><span class="sxs-lookup"><span data-stu-id="8ef37-109">Remarks</span></span>  

 <span data-ttu-id="8ef37-110">在 .NET Framework 2.0 版中，不會對 `JITCachedFunctionSearchStarted` 一般 NGen 影像中的所有函數進行和 [ICorProfilerCallback：： JITCachedFunctionSearchFinished 方法](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="8ef37-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="8ef37-111">只有針對設定檔優化的 NGen 映射才會產生映射中所有函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="8ef37-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="8ef37-112">不過，由於額外的額外負荷，分析工具應該只在想要使用這些回呼來強制將函式編譯為即時 (JIT) 時，才要求 profiler 優化的 NGen 映射。</span><span class="sxs-lookup"><span data-stu-id="8ef37-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="8ef37-113">否則，分析工具應該使用延遲策略來收集函數資訊。</span><span class="sxs-lookup"><span data-stu-id="8ef37-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="8ef37-114">分析工具必須支援已分析之應用程式的多個執行緒同時呼叫相同方法的情況。</span><span class="sxs-lookup"><span data-stu-id="8ef37-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="8ef37-115">例如，執行緒 A 呼叫，而分析工具會 `JITCachedFunctionSearchStarted` 將 *pbUseCachedFunction* 設定為 FALSE 以強制 JIT 編譯，以進行回應。</span><span class="sxs-lookup"><span data-stu-id="8ef37-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction* to FALSE to force JIT compilation.</span></span> <span data-ttu-id="8ef37-116">執行緒 A 接著會呼叫 [ICorProfilerCallback：： JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) 和 [ICorProfilerCallback：： JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef37-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="8ef37-117">現線上程 B 會呼叫相同的函式 `JITCachedFunctionSearchStarted` 。</span><span class="sxs-lookup"><span data-stu-id="8ef37-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="8ef37-118">雖然分析工具已陳述了函式的 JIT 編譯意圖，但分析工具會收到第二個回呼，因為執行緒 B 會在分析工具回應執行緒 A 的呼叫之前傳送回呼 `JITCachedFunctionSearchStarted` 。</span><span class="sxs-lookup"><span data-stu-id="8ef37-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="8ef37-119">執行緒進行呼叫的順序取決於執行緒的排程方式。</span><span class="sxs-lookup"><span data-stu-id="8ef37-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="8ef37-120">當分析工具接收重複的回呼時，它必須針對所有重複的回呼，將所參考的值設定 `pbUseCachedFunction` 為相同的值。</span><span class="sxs-lookup"><span data-stu-id="8ef37-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="8ef37-121">也就是說，當 `JITCachedFunctionSearchStarted` 使用相同的值呼叫多次時，分析工具 `functionId` 必須每次都有相同的回應。</span><span class="sxs-lookup"><span data-stu-id="8ef37-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ef37-122">需求</span><span class="sxs-lookup"><span data-stu-id="8ef37-122">Requirements</span></span>  

 <span data-ttu-id="8ef37-123">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ef37-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ef37-124">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8ef37-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8ef37-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ef37-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ef37-126">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ef37-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ef37-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ef37-127">See also</span></span>

- [<span data-ttu-id="8ef37-128">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8ef37-128">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
