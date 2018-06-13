---
title: ICorProfilerCallback4::ReJITCompilationStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3e21d42340378c576bfc65750fba26a257b82cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457742"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="02029-102">ICorProfilerCallback4::ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="02029-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="02029-103">通知分析工具在 just-in-time (JIT) 編譯器已啟動重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="02029-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02029-104">語法</span><span class="sxs-lookup"><span data-stu-id="02029-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02029-105">參數</span><span class="sxs-lookup"><span data-stu-id="02029-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="02029-106">[in]已開始 JIT 編譯器重新編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="02029-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="02029-107">[in]重新編譯函式的新版本的識別碼。</span><span class="sxs-lookup"><span data-stu-id="02029-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="02029-108">[in]`true`表示封鎖可能會造成執行階段從這個回呼; 傳回呼叫執行緒的等候`false`表示封鎖將不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="02029-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="02029-109">值為`true`不傷害執行階段，但可能會影響分析的結果。</span><span class="sxs-lookup"><span data-stu-id="02029-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02029-110">備註</span><span class="sxs-lookup"><span data-stu-id="02029-110">Remarks</span></span>  
 <span data-ttu-id="02029-111">很可能會收到一對以上的`ReJITCompilationStarted`和[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)方法會呼叫每個函式因為執行階段控制代碼類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="02029-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="02029-112">例如，執行階段啟動方法，重新編譯，但是類別 B 的類別建構函式必須在執行。</span><span class="sxs-lookup"><span data-stu-id="02029-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="02029-113">因此，執行階段重新編譯類別 B 的建構函式，並執行它。</span><span class="sxs-lookup"><span data-stu-id="02029-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="02029-114">建構函式執行時，它會方法 A，這會導致重新編譯一次方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="02029-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="02029-115">在此案例中，就會中止方法的第一次重新編譯。</span><span class="sxs-lookup"><span data-stu-id="02029-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="02029-116">不過，兩者會嘗試重新編譯的方法會回報 JIT 重新編譯事件。</span><span class="sxs-lookup"><span data-stu-id="02029-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="02029-117">程式碼剖析工具必須在其中兩個執行緒同時進行回呼的情況下支援 JIT 重新編譯回呼的序列。</span><span class="sxs-lookup"><span data-stu-id="02029-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="02029-118">例如，執行緒的呼叫`ReJITCompilationStarted`; 不過，執行緒的呼叫[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從`ReJITCompilationStarted`回呼執行緒 a。它可能會顯示該函式 ID 尚未有效期不應因為呼叫[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)有尚未收到分析工具。</span><span class="sxs-lookup"><span data-stu-id="02029-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="02029-119">不過，在此情況下，函式識別碼無效。</span><span class="sxs-lookup"><span data-stu-id="02029-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02029-120">需求</span><span class="sxs-lookup"><span data-stu-id="02029-120">Requirements</span></span>  
 <span data-ttu-id="02029-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02029-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02029-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02029-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02029-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02029-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02029-124">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02029-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02029-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02029-125">See Also</span></span>  
 [<span data-ttu-id="02029-126">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="02029-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="02029-127">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="02029-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="02029-128">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="02029-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="02029-129">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="02029-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
