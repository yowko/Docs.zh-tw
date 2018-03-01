---
title: "ICorProfilerCallback::MovedReferences 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d62fbdf4b6dd2acbb67b0655938990d625f8df8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmovedreferences-method"></a><span data-ttu-id="c0105-102">ICorProfilerCallback::MovedReferences 方法</span><span class="sxs-lookup"><span data-stu-id="c0105-102">ICorProfilerCallback::MovedReferences Method</span></span>
<span data-ttu-id="c0105-103">呼叫以報告壓縮記憶體回收造成的堆積中物件的新配置。</span><span class="sxs-lookup"><span data-stu-id="c0105-103">Called to report the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0105-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0105-104">Syntax</span></span>  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0105-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0105-105">Parameters</span></span>  
 `cMovedObjectIDRanges`  
 <span data-ttu-id="c0105-106">[in] 壓縮記憶體回收造成移動的連續物件區塊數目。</span><span class="sxs-lookup"><span data-stu-id="c0105-106">[in] The number of blocks of contiguous objects that moved as the result of the compacting garbage collection.</span></span> <span data-ttu-id="c0105-107">也就是 `cMovedObjectIDRanges` 的值是 `oldObjectIDRangeStart`、`newObjectIDRangeStart` 和 `cObjectIDRangeLength` 陣列的總大小。</span><span class="sxs-lookup"><span data-stu-id="c0105-107">That is, the value of `cMovedObjectIDRanges` is the total size of the `oldObjectIDRangeStart`, `newObjectIDRangeStart`, and `cObjectIDRangeLength` arrays.</span></span>  
  
 <span data-ttu-id="c0105-108">下面 `MovedReferences` 的三個引數是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="c0105-108">The next three arguments of `MovedReferences` are parallel arrays.</span></span> <span data-ttu-id="c0105-109">換句話說，`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]` 和 `cObjectIDRangeLength[i]` 全都會考量連續物件的單一區塊。</span><span class="sxs-lookup"><span data-stu-id="c0105-109">In other words, `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, and `cObjectIDRangeLength[i]` all concern a single block of contiguous objects.</span></span>  
  
 `oldObjectIDRangeStart`  
 <span data-ttu-id="c0105-110">[in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊舊的 (記憶體回收前) 開始位址。</span><span class="sxs-lookup"><span data-stu-id="c0105-110">[in] An array of `ObjectID` values, each of which is the old (pre-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `newObjectIDRangeStart`  
 <span data-ttu-id="c0105-111">[in] 一個 `ObjectID` 值的陣列，其中每一個都是記憶體中連續即時物件之區塊新的 (記憶體回收後) 開始位址。</span><span class="sxs-lookup"><span data-stu-id="c0105-111">[in] An array of `ObjectID` values, each of which is the new (post-garbage collection) starting address of a block of contiguous, live objects in memory.</span></span>  
  
 `cObjectIDRangeLength`  
 <span data-ttu-id="c0105-112">[in] 一個整數的陣列，其中每一個都是記憶體中連續物件區塊的大小。</span><span class="sxs-lookup"><span data-stu-id="c0105-112">[in] An array of integers, each of which is the size of a block of contiguous objects in memory.</span></span>  
  
 <span data-ttu-id="c0105-113">已指定大小給 `oldObjectIDRangeStart` 和 `newObjectIDRangeStart` 陣列中被參考的每個區塊。</span><span class="sxs-lookup"><span data-stu-id="c0105-113">A size is specified for each block that is referenced in the `oldObjectIDRangeStart` and `newObjectIDRangeStart` arrays.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0105-114">備註</span><span class="sxs-lookup"><span data-stu-id="c0105-114">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0105-115">對於在 64 位元平台上大於 4 GB 的物件，這個方法會報告大小為 `MAX_ULONG`。</span><span class="sxs-lookup"><span data-stu-id="c0105-115">This method reports sizes as `MAX_ULONG` for objects that are greater than 4 GB on 64-bit platforms.</span></span> <span data-ttu-id="c0105-116">若要取得大於 4 GB 的物件大小，請使用[icorprofilercallback4:: Movedreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)方法改為。</span><span class="sxs-lookup"><span data-stu-id="c0105-116">To get the size of objects that are larger than 4 GB, use the [ICorProfilerCallback4::MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="c0105-117">壓縮記憶體回收行程會回收無作用物件所佔用的記憶體，且會壓縮釋放的空間。</span><span class="sxs-lookup"><span data-stu-id="c0105-117">A compacting garbage collector reclaims the memory occupied by dead objects and compacts that freed space.</span></span> <span data-ttu-id="c0105-118">如此一來，即時物件可能在堆積中移動，且先前通知所散發 `ObjectID` 的值可能會變更。</span><span class="sxs-lookup"><span data-stu-id="c0105-118">As a result, live objects might be moved within the heap, and `ObjectID` values distributed by previous notifications might change.</span></span>  
  
 <span data-ttu-id="c0105-119">假定現有 `ObjectID` 的值 (`oldObjectID`) 位於下列範圍內：</span><span class="sxs-lookup"><span data-stu-id="c0105-119">Assume that an existing `ObjectID` value (`oldObjectID`) lies within the following range:</span></span>  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 <span data-ttu-id="c0105-120">在此情況下，從範圍開頭到物件開頭的位移如下所示：</span><span class="sxs-lookup"><span data-stu-id="c0105-120">In this case, the offset from the start of the range to the start of the object is as follows:</span></span>  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 <span data-ttu-id="c0105-121">對於位於下列範圍內的任何 `i` 值：</span><span class="sxs-lookup"><span data-stu-id="c0105-121">For any value of `i` that is in the following range:</span></span>  
  
 <span data-ttu-id="c0105-122">0 <= `i` < `cMovedObjectIDRanges`</span><span class="sxs-lookup"><span data-stu-id="c0105-122">0 <= `i` < `cMovedObjectIDRanges`</span></span>  
  
 <span data-ttu-id="c0105-123">您可以計算新的 `ObjectID`，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c0105-123">you can calculate the new `ObjectID` as follows:</span></span>  
  
 <span data-ttu-id="c0105-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span><span class="sxs-lookup"><span data-stu-id="c0105-124">`newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)</span></span>  
  
 <span data-ttu-id="c0105-125">`MovedReferences` 方法在自行回呼期間所傳遞的 `ObjectID` 值都無效，因為記憶體回收可能正在將物件從舊位置移至新位置。</span><span class="sxs-lookup"><span data-stu-id="c0105-125">None of the `ObjectID` values passed by `MovedReferences` are valid during the callback itself, because the garbage collection might be in the middle of moving objects from old locations to new locations.</span></span> <span data-ttu-id="c0105-126">因此，分析工具不應嘗試在 `MovedReferences` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="c0105-126">Therefore, profilers should not attempt to inspect objects during a `MovedReferences` call.</span></span> <span data-ttu-id="c0105-127">A [icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)回呼表示所有物件都已都移至其新位置，而且可以執行檢查。</span><span class="sxs-lookup"><span data-stu-id="c0105-127">A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback indicates that all objects have been moved to their new locations and inspection can be performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0105-128">需求</span><span class="sxs-lookup"><span data-stu-id="c0105-128">Requirements</span></span>  
 <span data-ttu-id="c0105-129">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0105-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0105-130">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0105-130">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0105-131">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0105-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0105-132">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0105-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0105-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="c0105-133">See Also</span></span>  
 [<span data-ttu-id="c0105-134">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c0105-134">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="c0105-135">MovedReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="c0105-135">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [<span data-ttu-id="c0105-136">分析介面</span><span class="sxs-lookup"><span data-stu-id="c0105-136">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c0105-137">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="c0105-137">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
