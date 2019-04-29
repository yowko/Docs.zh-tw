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
ms.openlocfilehash: b8f2ada73686dfbe5629e21cfc6468becbd4ccc5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597358"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="570ab-102">ICorProfilerCallback4::ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="570ab-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="570ab-103">通知分析工具在 just-in-time (JIT) 編譯器已開始重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="570ab-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570ab-104">語法</span><span class="sxs-lookup"><span data-stu-id="570ab-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="570ab-105">參數</span><span class="sxs-lookup"><span data-stu-id="570ab-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="570ab-106">[in]JIT 編譯器開始編譯函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="570ab-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="570ab-107">[in]重新編譯函式的新版本的識別碼。</span><span class="sxs-lookup"><span data-stu-id="570ab-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="570ab-108">[in]`true`表示封鎖可能會導致執行階段，等候要從此回呼; 傳回呼叫的執行緒`false`表示封鎖會不會影響執行階段的作業。</span><span class="sxs-lookup"><span data-stu-id="570ab-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="570ab-109">值為`true`不會損害執行階段，但可能會影響分析結果。</span><span class="sxs-lookup"><span data-stu-id="570ab-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="570ab-110">備註</span><span class="sxs-lookup"><span data-stu-id="570ab-110">Remarks</span></span>  
 <span data-ttu-id="570ab-111">可接收的多個配對`ReJITCompilationStarted`並[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)方法會呼叫每個函式因為執行階段控制代碼類別建構函式。</span><span class="sxs-lookup"><span data-stu-id="570ab-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="570ab-112">比方說，在執行階段開始重新編譯方法，但類別 B 的類別建構函式必須執行。</span><span class="sxs-lookup"><span data-stu-id="570ab-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="570ab-113">因此，執行階段會重新編譯類別 B 的建構函式，並執行它。</span><span class="sxs-lookup"><span data-stu-id="570ab-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="570ab-114">當建構函式執行時，它會讓方法 A，這會導致重新編譯方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="570ab-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="570ab-115">在此案例中，就會中止方法的第一次重新編譯。</span><span class="sxs-lookup"><span data-stu-id="570ab-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="570ab-116">不過，兩者會嘗試重新編譯是使用 JIT 重新編譯事件所報告的方法。</span><span class="sxs-lookup"><span data-stu-id="570ab-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="570ab-117">在其中兩個執行緒同時進行回呼的情況下，程式碼剖析工具必須支援 JIT 重新編譯回呼的序列。</span><span class="sxs-lookup"><span data-stu-id="570ab-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="570ab-118">例如，呼叫執行緒 A `ReJITCompilationStarted`; 不過，在執行緒的呼叫之前[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)，執行緒 B 呼叫[icorprofilercallback:: Exceptionsearchfunctionenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)函式識別碼從`ReJITCompilationStarted`回呼執行緒 a。它可能會顯示該函式識別碼尚未有效期不應因為呼叫[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)有尚未收到的分析工具。</span><span class="sxs-lookup"><span data-stu-id="570ab-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="570ab-119">不過，在此情況下，函式識別碼無效。</span><span class="sxs-lookup"><span data-stu-id="570ab-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="570ab-120">需求</span><span class="sxs-lookup"><span data-stu-id="570ab-120">Requirements</span></span>  
 <span data-ttu-id="570ab-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="570ab-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="570ab-122">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="570ab-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="570ab-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="570ab-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="570ab-124">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="570ab-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570ab-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="570ab-125">See also</span></span>

- [<span data-ttu-id="570ab-126">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="570ab-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="570ab-127">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="570ab-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="570ab-128">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="570ab-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="570ab-129">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="570ab-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
