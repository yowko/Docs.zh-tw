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
ms.openlocfilehash: be257930ca0fad658afa75d6efa4573d4f888a2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177086"
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="7f15d-102">ICorProfilerCallback4::ReJITCompilationStarted 方法</span><span class="sxs-lookup"><span data-stu-id="7f15d-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="7f15d-103">通知探測器及時 （JIT） 編譯器已開始重新編譯函數。</span><span class="sxs-lookup"><span data-stu-id="7f15d-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f15d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f15d-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationStarted(
    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f15d-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f15d-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="7f15d-106">[在]JIT 編譯器已開始重新編譯的函數的 ID。</span><span class="sxs-lookup"><span data-stu-id="7f15d-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="7f15d-107">[在]函數的新版本的重新編譯 ID。</span><span class="sxs-lookup"><span data-stu-id="7f15d-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="7f15d-108">[在]`true`指示阻塞可能導致運行時等待調用執行緒從此回檔返回;`false`指示阻塞不會影響運行時的操作。</span><span class="sxs-lookup"><span data-stu-id="7f15d-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="7f15d-109">值`true`不會損害運行時，但可能會影響分析結果。</span><span class="sxs-lookup"><span data-stu-id="7f15d-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f15d-110">備註</span><span class="sxs-lookup"><span data-stu-id="7f15d-110">Remarks</span></span>  
 <span data-ttu-id="7f15d-111">由於運行時處理類建構函式的方式，可以為每個`ReJITCompilationStarted`函數接收多對和[ReJIT 編譯完成](icorprofilercallback4-rejitcompilationfinished-method.md)方法調用。</span><span class="sxs-lookup"><span data-stu-id="7f15d-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="7f15d-112">例如，運行時開始重新編譯方法 A，但需要運行類 B 的類建構函式。</span><span class="sxs-lookup"><span data-stu-id="7f15d-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="7f15d-113">因此，運行時重新編譯類 B 的建構函式並運行它。</span><span class="sxs-lookup"><span data-stu-id="7f15d-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="7f15d-114">當建構函式運行時，它會調用方法 A，這將導致方法 A 再次重新編譯。</span><span class="sxs-lookup"><span data-stu-id="7f15d-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="7f15d-115">在這種情況下，方法 A 的第一次重新編譯將停止。</span><span class="sxs-lookup"><span data-stu-id="7f15d-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="7f15d-116">但是，使用 JIT 重新編譯附隨報告重新編譯方法 A 的嘗試。</span><span class="sxs-lookup"><span data-stu-id="7f15d-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="7f15d-117">在兩個執行緒同時進行回檔的情況下，探測器必須支援 JIT 重新編譯回檔的順序。</span><span class="sxs-lookup"><span data-stu-id="7f15d-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="7f15d-118">例如，執行緒 A`ReJITCompilationStarted`調用 ;但是，線上程 A 調用[ReJIT 編譯完成](icorprofilercallback4-rejitcompilationfinished-method.md)之前，執行緒 B 調用[ICorProfiler 回檔：：異常搜索功能Enter](icorprofilercallback-exceptionsearchfunctionenter-method.md)與執行緒 A 回檔中的`ReJITCompilationStarted`函數 ID。似乎函數 ID 尚未有效，因為探測器尚未收到對[ReJIT 編譯完成的](icorprofilercallback4-rejitcompilationfinished-method.md)調用。</span><span class="sxs-lookup"><span data-stu-id="7f15d-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="7f15d-119">但是，在這種情況下，函數 ID 有效。</span><span class="sxs-lookup"><span data-stu-id="7f15d-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f15d-120">需求</span><span class="sxs-lookup"><span data-stu-id="7f15d-120">Requirements</span></span>  
 <span data-ttu-id="7f15d-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7f15d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f15d-122">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7f15d-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f15d-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f15d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f15d-124">**.NET 框架版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f15d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f15d-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f15d-125">See also</span></span>

- [<span data-ttu-id="7f15d-126">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7f15d-126">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="7f15d-127">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="7f15d-127">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="7f15d-128">JITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7f15d-128">JITCompilationFinished Method</span></span>](icorprofilercallback-jitcompilationfinished-method.md)
- [<span data-ttu-id="7f15d-129">ReJITCompilationFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7f15d-129">ReJITCompilationFinished Method</span></span>](icorprofilercallback4-rejitcompilationfinished-method.md)
