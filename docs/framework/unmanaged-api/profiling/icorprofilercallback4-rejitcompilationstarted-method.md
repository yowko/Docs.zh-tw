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
ms.openlocfilehash: 074b0b11a822d2b8bcb9588484557e3e5eba69dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430202"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="f7742-102">ICorProfilerCallback4::ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="f7742-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="f7742-103">通知 profiler，及時（JIT）編譯器已開始重新編譯函式。</span><span class="sxs-lookup"><span data-stu-id="f7742-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7742-104">語法</span><span class="sxs-lookup"><span data-stu-id="f7742-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(   
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7742-105">參數</span><span class="sxs-lookup"><span data-stu-id="f7742-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f7742-106">在JIT 編譯程式已開始重新編譯之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f7742-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="f7742-107">在新版本函數的重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="f7742-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="f7742-108">[in] `true`，表示封鎖可能會導致執行時間等候呼叫執行緒從這個回呼傳回;`false`，表示封鎖作業不會影響執行時間的作業。</span><span class="sxs-lookup"><span data-stu-id="f7742-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="f7742-109">`true` 的值不會傷害執行時間，但可能會影響分析結果。</span><span class="sxs-lookup"><span data-stu-id="f7742-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7742-110">備註</span><span class="sxs-lookup"><span data-stu-id="f7742-110">Remarks</span></span>  
 <span data-ttu-id="f7742-111">您可以針對每個函式接收一對以上的 `ReJITCompilationStarted` 和[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)方法呼叫，因為執行時間會處理類別的方法。</span><span class="sxs-lookup"><span data-stu-id="f7742-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="f7742-112">例如，執行時間會開始重新編譯方法 A，但類別 B 的類別函式必須執行。</span><span class="sxs-lookup"><span data-stu-id="f7742-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="f7742-113">因此，執行時間會重新編譯類別 B 的函式，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="f7742-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="f7742-114">當此函式正在執行時，它會呼叫方法 A，這會導致再次重新編譯方法 A。</span><span class="sxs-lookup"><span data-stu-id="f7742-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="f7742-115">在此案例中，第一次重新編譯方法 A 會停止。</span><span class="sxs-lookup"><span data-stu-id="f7742-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="f7742-116">不過，這兩次嘗試重新編譯方法 A 都會使用 JIT 重新編譯事件來回報。</span><span class="sxs-lookup"><span data-stu-id="f7742-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="f7742-117">分析工具在兩個執行緒同時進行回呼的情況下，必須支援 JIT 重新編譯回呼的順序。</span><span class="sxs-lookup"><span data-stu-id="f7742-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="f7742-118">例如，執行緒 A 會呼叫 `ReJITCompilationStarted`;不過，線上程 A 呼叫[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)之前，執行緒 B 會呼叫[ICorProfilerCallback：： ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) ，並從執行緒 a 的 `ReJITCompilationStarted` 回呼中取得函數識別碼。可能會出現函式識別碼尚未生效的情況，因為分析工具尚未收到[ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)的呼叫。</span><span class="sxs-lookup"><span data-stu-id="f7742-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="f7742-119">不過，在此情況下，函數識別碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="f7742-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7742-120">需求</span><span class="sxs-lookup"><span data-stu-id="f7742-120">Requirements</span></span>  
 <span data-ttu-id="f7742-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f7742-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7742-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f7742-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f7742-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7742-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7742-124">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7742-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7742-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7742-125">See also</span></span>

- [<span data-ttu-id="f7742-126">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f7742-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f7742-127">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="f7742-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="f7742-128">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f7742-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="f7742-129">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="f7742-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)
