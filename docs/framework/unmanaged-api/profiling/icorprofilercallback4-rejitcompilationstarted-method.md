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
ms.openlocfilehash: 43db4ce0ba7a95a029e6c4928f55a99df9085164
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730249"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="92617-102">ICorProfilerCallback4::ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="92617-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>

<span data-ttu-id="92617-103">通知分析工具，及時 (JIT) 編譯器已開始重新編譯函數。</span><span class="sxs-lookup"><span data-stu-id="92617-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92617-104">語法</span><span class="sxs-lookup"><span data-stu-id="92617-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92617-105">參數</span><span class="sxs-lookup"><span data-stu-id="92617-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="92617-106">在JIT 編譯程式已開始重新編譯的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="92617-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="92617-107">在新版本函數的重新編譯識別碼。</span><span class="sxs-lookup"><span data-stu-id="92617-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="92617-108">[in] `true` 若要指出封鎖可能會導致執行時間等候呼叫執行緒從此回呼傳回; `false` 表示封鎖不會影響執行時間的操作。</span><span class="sxs-lookup"><span data-stu-id="92617-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="92617-109">的值 `true` 不會危害執行時間，但可能會影響分析結果。</span><span class="sxs-lookup"><span data-stu-id="92617-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92617-110">備註</span><span class="sxs-lookup"><span data-stu-id="92617-110">Remarks</span></span>  

 <span data-ttu-id="92617-111">您可以針對每個函式接收一對以上的 `ReJITCompilationStarted` [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) 方法呼叫，因為執行時間處理類別的函式的方式。</span><span class="sxs-lookup"><span data-stu-id="92617-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="92617-112">例如，執行時間會開始重新編譯方法 A，但必須執行類別 B 的類別函式。</span><span class="sxs-lookup"><span data-stu-id="92617-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="92617-113">因此，執行時間會重新編譯類別 B 的函式並加以執行。</span><span class="sxs-lookup"><span data-stu-id="92617-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="92617-114">當此函式正在執行時，它會呼叫方法 A，這會導致重新編譯方法 A。</span><span class="sxs-lookup"><span data-stu-id="92617-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="92617-115">在此案例中，第一次重新編譯方法 A 會暫停。</span><span class="sxs-lookup"><span data-stu-id="92617-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="92617-116">不過，這兩個嘗試重新編譯方法 A 都會以 JIT 重新編譯事件來回報。</span><span class="sxs-lookup"><span data-stu-id="92617-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="92617-117">當兩個執行緒同時進行回呼時，分析工具必須支援 JIT 重新編譯回呼的順序。</span><span class="sxs-lookup"><span data-stu-id="92617-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="92617-118">例如，執行緒 A 呼叫， `ReJITCompilationStarted` 但是線上程 a 呼叫 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md)之前，執行緒 B 會使用執行緒 A 的回呼中的函式識別碼來呼叫 [ICorProfilerCallback：： ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) `ReJITCompilationStarted` 。這可能會出現，因為分析工具尚未收到 [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) 的呼叫，所以函式識別碼應該尚未有效。</span><span class="sxs-lookup"><span data-stu-id="92617-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="92617-119">不過，在此情況下，函數識別碼是有效的。</span><span class="sxs-lookup"><span data-stu-id="92617-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92617-120">需求</span><span class="sxs-lookup"><span data-stu-id="92617-120">Requirements</span></span>  

 <span data-ttu-id="92617-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="92617-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92617-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92617-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92617-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92617-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92617-124">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92617-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92617-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92617-125">See also</span></span>

- [<span data-ttu-id="92617-126">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="92617-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="92617-127">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="92617-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="92617-128">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="92617-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="92617-129">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="92617-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
