---
title: "ICorProfilerCallback2::GarbageCollectionStarted 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b721b990312f9acda5c9e0208f998793735d2cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a><span data-ttu-id="55a39-102">ICorProfilerCallback2::GarbageCollectionStarted 方法</span><span class="sxs-lookup"><span data-stu-id="55a39-102">ICorProfilerCallback2::GarbageCollectionStarted Method</span></span>
<span data-ttu-id="55a39-103">通知記憶體回收已啟動程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="55a39-103">Notifies the code profiler that garbage collection has started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55a39-104">語法</span><span class="sxs-lookup"><span data-stu-id="55a39-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="55a39-105">參數</span><span class="sxs-lookup"><span data-stu-id="55a39-105">Parameters</span></span>  
 `cGenerations`  
 <span data-ttu-id="55a39-106">[in]中的項目總數`generationCollected`陣列。</span><span class="sxs-lookup"><span data-stu-id="55a39-106">[in] The total number of entries in the `generationCollected` array.</span></span>  
  
 `generationCollected`  
 <span data-ttu-id="55a39-107">[in]布林值陣列，也就是`true`如果正在收集此記憶體回收; 否則對應於的陣列索引的層代`false`。</span><span class="sxs-lookup"><span data-stu-id="55a39-107">[in] An array of Boolean values, which are `true` if the generation that corresponds to the array index is being collected by this garbage collection; otherwise, `false`.</span></span>  
  
 <span data-ttu-id="55a39-108">陣列編製索引的值[COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)列舉，指出產生。</span><span class="sxs-lookup"><span data-stu-id="55a39-108">The array is indexed by a value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration, which indicates the generation.</span></span>  
  
 `reason`  
 <span data-ttu-id="55a39-109">[in]值為[COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)已包含列舉值，指出記憶體回收的原因。</span><span class="sxs-lookup"><span data-stu-id="55a39-109">[in] A value of the [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) enumeration that indicates the reason the garbage collection was induced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55a39-110">備註</span><span class="sxs-lookup"><span data-stu-id="55a39-110">Remarks</span></span>  
 <span data-ttu-id="55a39-111">所有的回呼屬於此回收會發生之間`GarbageCollectionStarted`回呼和對應[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="55a39-111">All callbacks that pertain to this garbage collection will occur between the `GarbageCollectionStarted` callback and the corresponding [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) callback.</span></span> <span data-ttu-id="55a39-112">這些回呼不需要在相同執行緒上發生。</span><span class="sxs-lookup"><span data-stu-id="55a39-112">These callbacks need not occur on the same thread.</span></span>  
  
 <span data-ttu-id="55a39-113">它是安全的程式碼剖析工具來檢查期間其原始位置中的物件`GarbageCollectionStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="55a39-113">It is safe for the profiler to inspect objects in their original locations during the `GarbageCollectionStarted` callback.</span></span> <span data-ttu-id="55a39-114">記憶體回收行程就會開始移動的物件之後從傳回`GarbageCollectionStarted`。</span><span class="sxs-lookup"><span data-stu-id="55a39-114">The garbage collector will begin moving objects after the return from `GarbageCollectionStarted`.</span></span> <span data-ttu-id="55a39-115">程式碼剖析工具分析工具從此回呼傳回之後，應該考慮所有可能無效，直到其接收到的物件識別碼`ICorProfilerCallback2::GarbageCollectionFinished`回呼。</span><span class="sxs-lookup"><span data-stu-id="55a39-115">After the profiler has returned from this callback, the profiler should consider all object IDs to be invalid until it receives a `ICorProfilerCallback2::GarbageCollectionFinished` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55a39-116">需求</span><span class="sxs-lookup"><span data-stu-id="55a39-116">Requirements</span></span>  
 <span data-ttu-id="55a39-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="55a39-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55a39-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55a39-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55a39-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55a39-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55a39-120">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55a39-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a39-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="55a39-121">See Also</span></span>  
 [<span data-ttu-id="55a39-122">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="55a39-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="55a39-123">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="55a39-123">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
