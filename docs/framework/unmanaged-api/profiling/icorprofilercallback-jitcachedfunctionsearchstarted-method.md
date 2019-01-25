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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9036746fcf0150875ab534fdb774ed3633cf96ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698335"
---
# <a name="icorprofilercallbackjitcachedfunctionsearchstarted-method"></a><span data-ttu-id="09b10-102">ICorProfilerCallback::JITCachedFunctionSearchStarted 方法</span><span class="sxs-lookup"><span data-stu-id="09b10-102">ICorProfilerCallback::JITCachedFunctionSearchStarted Method</span></span>
<span data-ttu-id="09b10-103">通知分析工具對於先前使用 原生映像產生器 (NGen.exe) 所編譯的函式已開始搜尋。</span><span class="sxs-lookup"><span data-stu-id="09b10-103">Notifies the profiler that a search has started for a function that was compiled previously using the Native Image Generator (NGen.exe).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b10-104">語法</span><span class="sxs-lookup"><span data-stu-id="09b10-104">Syntax</span></span>  
  
```  
HRESULT JITCachedFunctionSearchStarted(  
    [in]  FunctionID functionId,  
    [out] BOOL *pbUseCachedFunction);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09b10-105">參數</span><span class="sxs-lookup"><span data-stu-id="09b10-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="09b10-106">[in]正在執行搜尋函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="09b10-106">[in] The ID of the function for which the search is being performed.</span></span>  
  
 `pbUseCachedFunction`  
 <span data-ttu-id="09b10-107">[out]`true`如果執行引擎應該使用快取的版本的函式 （如果有的話），否則為`false`。</span><span class="sxs-lookup"><span data-stu-id="09b10-107">[out] `true` if the execution engine should use the cached version of a function (if available); otherwise `false`.</span></span> <span data-ttu-id="09b10-108">如果值為`false`，執行引擎的 JIT 編譯的函式，而不是使用不是 JIT 編譯的版本。</span><span class="sxs-lookup"><span data-stu-id="09b10-108">If the value is `false`, the execution engine JIT-compiles the function instead of using a version that is not JIT-compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09b10-109">備註</span><span class="sxs-lookup"><span data-stu-id="09b10-109">Remarks</span></span>  
 <span data-ttu-id="09b10-110">在.NET Framework 2.0 版中，`JITCachedFunctionSearchStarted`並[icorprofilercallback:: Jitcachedfunctionsearchfinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)回呼將不會進行一般的 NGen 影像中的所有函式。</span><span class="sxs-lookup"><span data-stu-id="09b10-110">In the .NET Framework version 2.0, the `JITCachedFunctionSearchStarted` and [ICorProfilerCallback::JITCachedFunctionSearchFinished Method](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md) callbacks will not be made for all functions in regular NGen images.</span></span> <span data-ttu-id="09b10-111">只適用於設定檔的 NGen 映像會產生映像中的所有函式的回呼。</span><span class="sxs-lookup"><span data-stu-id="09b10-111">Only NGen images optimized for a profile will generate callbacks for all functions in the image.</span></span> <span data-ttu-id="09b10-112">不過，由於額外的負荷，分析工具應該要求程式碼剖析工具最佳化 NGen 影像才想要使用這些回呼強制函式會編譯在 just-in-time (JIT)。</span><span class="sxs-lookup"><span data-stu-id="09b10-112">However, due to the additional overhead, a profiler should request profiler-optimized NGen images only if it intends to use these callbacks to force a function to be compiled just-in-time (JIT).</span></span> <span data-ttu-id="09b10-113">分析工具，否則為要使用延遲的策略用於蒐集函式資訊使用。</span><span class="sxs-lookup"><span data-stu-id="09b10-113">Otherwise, the profiler should use a lazy strategy for gathering function information.</span></span>  
  
 <span data-ttu-id="09b10-114">程式碼剖析工具必須支援多個執行緒的分析的應用程式會呼叫同時相同方法的情況。</span><span class="sxs-lookup"><span data-stu-id="09b10-114">Profilers must support cases where multiple threads of a profiled application are calling the same method simultaneously.</span></span> <span data-ttu-id="09b10-115">例如，呼叫執行緒 A`JITCachedFunctionSearchStarted`和分析工具會藉由設定回應*pbUseCachedFunction*為 FALSE，以強制執行 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="09b10-115">For example, thread A calls `JITCachedFunctionSearchStarted` and the profiler responds by setting *pbUseCachedFunction*to FALSE to force JIT compilation.</span></span> <span data-ttu-id="09b10-116">接著會呼叫的執行緒[icorprofilercallback:: Jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)並[icorprofilercallback:: Jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="09b10-116">Thread A then calls [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) and [ICorProfilerCallback::JITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md).</span></span>  
  
 <span data-ttu-id="09b10-117">現在執行緒 B 呼叫`JITCachedFunctionSearchStarted`相同函式。</span><span class="sxs-lookup"><span data-stu-id="09b10-117">Now thread B calls `JITCachedFunctionSearchStarted` for the same function.</span></span> <span data-ttu-id="09b10-118">即使分析工具已宣稱其欲 JIT 編譯的函式，分析工具收到第二個回撥，因為執行緒 B 在執行緒 A 的呼叫已回應的程式碼剖析工具之前，會將傳送回呼`JITCachedFunctionSearchStarted`。</span><span class="sxs-lookup"><span data-stu-id="09b10-118">Even though the profiler has stated its intention to JIT-compile the function, the profiler receives the second callback because thread B sends the callback before the profiler has responded to thread A's call to `JITCachedFunctionSearchStarted`.</span></span> <span data-ttu-id="09b10-119">執行緒呼叫的順序取決於如何排程執行緒。</span><span class="sxs-lookup"><span data-stu-id="09b10-119">The order in which the threads make calls depends on how the threads are scheduled.</span></span>  
  
 <span data-ttu-id="09b10-120">當分析工具收到重複的回呼時，它必須設定所參考的值`pbUseCachedFunction`相同的值為所有重複的回呼。</span><span class="sxs-lookup"><span data-stu-id="09b10-120">When the profiler receives duplicate callbacks, it must set the value referenced by `pbUseCachedFunction` to the same value for all the duplicate callbacks.</span></span> <span data-ttu-id="09b10-121">也就是說，當`JITCachedFunctionSearchStarted`多次呼叫相同`functionId`值，分析工具必須回應相同的每一次。</span><span class="sxs-lookup"><span data-stu-id="09b10-121">That is, when `JITCachedFunctionSearchStarted` is called multiple times with the same `functionId` value, the profiler must respond the same each time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09b10-122">需求</span><span class="sxs-lookup"><span data-stu-id="09b10-122">Requirements</span></span>  
 <span data-ttu-id="09b10-123">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09b10-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b10-124">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09b10-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09b10-125">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09b10-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09b10-126">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b10-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b10-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09b10-127">See also</span></span>
- [<span data-ttu-id="09b10-128">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="09b10-128">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
