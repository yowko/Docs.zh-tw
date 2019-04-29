---
title: ICorProfilerCallback4::MovedReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d368c88503853d0620f28f02f88a6d887c1aa681
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597819"
---
# <a name="icorprofilercallback4movedreferences2-method"></a><span data-ttu-id="7e676-102">ICorProfilerCallback4::MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="7e676-102">ICorProfilerCallback4::MovedReferences2 Method</span></span>
<span data-ttu-id="7e676-103">呼叫以報告壓縮記憶體回收造成的堆積中物件的新配置。</span><span class="sxs-lookup"><span data-stu-id="7e676-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span> <span data-ttu-id="7e676-104">如果分析工具已實作，會呼叫這個方法[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7e676-104">This method is called if the profiler has implemented the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface.</span></span> <span data-ttu-id="7e676-105">此回呼會取代[icorprofilercallback:: Movedreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)方法，因為它會報告更大範圍的物件，其長度超過在 ULONG 中能表示。</span><span class="sxs-lookup"><span data-stu-id="7e676-105">This callback replaces the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, because it can report larger ranges of objects whose lengths exceed what can be expressed in a ULONG.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e676-106">語法</span><span class="sxs-lookup"><span data-stu-id="7e676-106">Syntax</span></span>  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e676-107">參數</span><span class="sxs-lookup"><span data-stu-id="7e676-107">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="7e676-108">[in] 壓縮記憶體回收造成移動的連續物件區塊數目。</span><span class="sxs-lookup"><span data-stu-id="7e676-108">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="7e676-109">也就是 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的總大小。</span><span class="sxs-lookup"><span data-stu-id="7e676-109">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="7e676-110">下面 `MovedReferences2` 的三個引數是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="7e676-110">The next three arguments of `MovedReferences2` are parallel arrays.</span></span> <span data-ttu-id="7e676-111">換句話說，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 全都會考量連續物件的單一區塊。</span><span class="sxs-lookup"><span data-stu-id="7e676-111">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="7e676-112">[in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊舊的 (記憶體回收前) 開始位址。</span><span class="sxs-lookup"><span data-stu-id="7e676-112">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="7e676-113">[in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊新的 (記憶體回收後) 開始位址。</span><span class="sxs-lookup"><span data-stu-id="7e676-113">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="7e676-114">[in] 一個整數的陣列，其中每一個都是記憶體中連續物件區塊的大小。</span><span class="sxs-lookup"><span data-stu-id="7e676-114">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="7e676-115">已指定大小給 `oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 陣列中被參考的每個區塊。</span><span class="sxs-lookup"><span data-stu-id="7e676-115">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e676-116">備註</span><span class="sxs-lookup"><span data-stu-id="7e676-116">Remarks</span></span>  
 <span data-ttu-id="7e676-117">壓縮記憶體回收行程會回收無作用物件所佔用的記憶體，且會壓縮釋放的空間。</span><span class="sxs-lookup"><span data-stu-id="7e676-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="7e676-118">如此一來，即時物件可能在堆積中移動，且先前通知所散發 `ObjectID` 的值可能會變更。</span><span class="sxs-lookup"><span data-stu-id="7e676-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="7e676-119">假定現有 `ObjectID` 的值 (`oldObjectID`) 位於下列範圍內：</span><span class="sxs-lookup"><span data-stu-id="7e676-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="7e676-120">在此情況下，從範圍開頭到物件開頭的位移如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e676-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="7e676-121">對於位於下列範圍內的任何 `i` 值：</span><span class="sxs-lookup"><span data-stu-id="7e676-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="7e676-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="7e676-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="7e676-123">您可以計算新的 `ObjectID`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7e676-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="7e676-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="7e676-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="7e676-125">`MovedReferences2` 方法在回呼自己期間所傳遞的 `ObjectID` 值都無效，因為記憶體回收行程可能正在將物件從舊位置移至新位置。</span><span class="sxs-lookup"><span data-stu-id="7e676-125">None of the `ObjectID` values passed by `MovedReferences2` are valid during the callback itself, because the garbage collector might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="7e676-126">因此，分析工具不應嘗試在 `MovedReferences2` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="7e676-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences2` call.</span></span> <span data-ttu-id="7e676-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)回呼表示所有物件都已都移至其新位置，而且可以執行檢查。</span><span class="sxs-lookup"><span data-stu-id="7e676-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
 <span data-ttu-id="7e676-128">如果分析工具同時實作[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)並[ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)介面`MovedReferences2`方法之前呼叫[ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)方法，但只有當`MovedReferences2`方法會傳回成功。</span><span class="sxs-lookup"><span data-stu-id="7e676-128">If the profiler implements both the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interfaces, the `MovedReferences2` method is called before the [ICorProfilerCallback::MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) method, but only if the `MovedReferences2` method returns successfully.</span></span> <span data-ttu-id="7e676-129">分析工具可傳回 HRESULT，表示 `MovedReferences2` 方法中的失敗，以避免呼叫第二個方法。</span><span class="sxs-lookup"><span data-stu-id="7e676-129">Profilers can return an HRESULT that indicates failure from the `MovedReferences2` method, to avoid calling the second method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e676-130">需求</span><span class="sxs-lookup"><span data-stu-id="7e676-130">Requirements</span></span>  
 <span data-ttu-id="7e676-131">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e676-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e676-132">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e676-132">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e676-133">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e676-133">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e676-134">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e676-134">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e676-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e676-135">See also</span></span>

- [<span data-ttu-id="7e676-136">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7e676-136">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7e676-137">MovedReferences 方法</span><span class="sxs-lookup"><span data-stu-id="7e676-137">MovedReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)
- [<span data-ttu-id="7e676-138">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="7e676-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [<span data-ttu-id="7e676-139">分析介面</span><span class="sxs-lookup"><span data-stu-id="7e676-139">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7e676-140">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="7e676-140">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
