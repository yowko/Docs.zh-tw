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
ms.openlocfilehash: 63a8d212a61bd73f44995f0e057eeff96f9a5554
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731939"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="64311-102">ICorProfilerCallback2::GarbageCollectionStarted 方法</span><span class="sxs-lookup"><span data-stu-id="64311-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>

<span data-ttu-id="64311-103">通知程式碼分析工具已開始垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="64311-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64311-104">語法</span><span class="sxs-lookup"><span data-stu-id="64311-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64311-105">參數</span><span class="sxs-lookup"><span data-stu-id="64311-105">Parameters</span></span>  

 `cGenerations`  
 <span data-ttu-id="64311-106">在陣列中的總專案數 `generationCollected` 。</span><span class="sxs-lookup"><span data-stu-id="64311-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="64311-107">在布林值的陣列， `true` 如果這個垃圾收集正在收集對應至陣列索引的產生，則為，否則為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="64311-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="64311-108">陣列是以 [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) 列舉的值來編制索引，這表示產生。</span><span class="sxs-lookup"><span data-stu-id="64311-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="64311-109">在 [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) 列舉的值，指出引發垃圾收集的原因。</span><span class="sxs-lookup"><span data-stu-id="64311-109">[in] A value of the [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64311-110">備註</span><span class="sxs-lookup"><span data-stu-id="64311-110">Remarks</span></span>  

 <span data-ttu-id="64311-111">`GarbageCollectionStarted`回呼和對應的[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)回呼之間會發生與此垃圾收集相關的所有回呼。</span><span class="sxs-lookup"><span data-stu-id="64311-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="64311-112">這些回呼不需要出現在相同的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="64311-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="64311-113">分析工具可以安全地在回呼期間檢查其原始位置中的物件 `GarbageCollectionStarted` 。</span><span class="sxs-lookup"><span data-stu-id="64311-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="64311-114">垃圾收集行程會在傳回之後開始移動物件 `GarbageCollectionStarted` 。</span><span class="sxs-lookup"><span data-stu-id="64311-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="64311-115">在分析工具從此回呼傳回之後，分析工具應該考慮所有物件識別碼都無效，直到收到 `ICorProfilerCallback2::GarbageCollectionFinished` 回呼為止。</span><span class="sxs-lookup"><span data-stu-id="64311-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64311-116">需求</span><span class="sxs-lookup"><span data-stu-id="64311-116">Requirements</span></span>  

 <span data-ttu-id="64311-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="64311-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64311-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64311-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64311-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64311-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64311-120">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64311-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64311-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64311-121">See also</span></span>

- [<span data-ttu-id="64311-122">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="64311-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="64311-123">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="64311-123">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
