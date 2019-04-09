---
title: ICorProfilerCallback2::GarbageCollectionStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5f9104dded44540c47c955c15354d8d76a27650
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183062"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="c5c7c-102">ICorProfilerCallback2::GarbageCollectionStarted 方法</span><span class="sxs-lookup"><span data-stu-id="c5c7c-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="c5c7c-103">已開始記憶體回收會通知程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c7c-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5c7c-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5c7c-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5c7c-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="c5c7c-106">[in]中的項目總數`generationCollected`陣列。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="c5c7c-107">[in]布林值，也就是陣列`true`如果對應至的陣列索引的層代會收集此記憶體回收; 否則即為`false`。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="c5c7c-108">陣列索引值所[COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)列舉，指出產生。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="c5c7c-109">[in]值為[COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)引發列舉，指出記憶體回收的原因了。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c7c-110">備註</span><span class="sxs-lookup"><span data-stu-id="c5c7c-110">Remarks</span></span>  
 <span data-ttu-id="c5c7c-111">所有的回呼，屬於此回收會發生之間`GarbageCollectionStarted`回呼和對應[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="c5c7c-112">這些回呼不需要在相同的執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="c5c7c-113">它是安全的程式碼剖析工具來檢查期間其原始位置中的物件`GarbageCollectionStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="c5c7c-114">記憶體回收行程就會開始移動的物件之後傳回`GarbageCollectionStarted`。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="c5c7c-115">分析工具分析工具從此回呼傳回之後，應該考慮失效，直到它收到所有的物件識別碼`ICorProfilerCallback2::GarbageCollectionFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c7c-116">需求</span><span class="sxs-lookup"><span data-stu-id="c5c7c-116">Requirements</span></span>  
 <span data-ttu-id="c5c7c-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5c7c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c7c-118">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5c7c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5c7c-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5c7c-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c5c7c-120">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="c5c7c-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5c7c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5c7c-121">See also</span></span>

- [<span data-ttu-id="c5c7c-122">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c5c7c-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="c5c7c-123">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="c5c7c-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
