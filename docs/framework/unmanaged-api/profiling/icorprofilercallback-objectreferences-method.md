---
title: "ICorProfilerCallback::ObjectReferences 方法"
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
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30b8f6b5f424ff81ace36baa8d2ae39e0a2f1d1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="255ba-102">ICorProfilerCallback::ObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="255ba-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="255ba-103">通知分析工具有關記憶體中所指定的物件所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="255ba-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="255ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="255ba-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="255ba-105">參數</span><span class="sxs-lookup"><span data-stu-id="255ba-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="255ba-106">[in]參考物件的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="255ba-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="255ba-107">[in]類別的指定的物件的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="255ba-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="255ba-108">[in]所指定的物件參考的物件數目 (亦即中的元素數目`objectRefIds`陣列)。</span><span class="sxs-lookup"><span data-stu-id="255ba-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="255ba-109">[in]所參考的物件識別碼的陣列`objectId`。</span><span class="sxs-lookup"><span data-stu-id="255ba-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="255ba-110">備註</span><span class="sxs-lookup"><span data-stu-id="255ba-110">Remarks</span></span>  
 <span data-ttu-id="255ba-111">`ObjectReferences`方法針對每個物件在堆積中剩餘的記憶體回收完成之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="255ba-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="255ba-112">如果分析工具從此回呼傳回錯誤，程式碼剖析服務將中止直到下一個記憶體回收叫用這個回呼。</span><span class="sxs-lookup"><span data-stu-id="255ba-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="255ba-113">`ObjectReferences`回呼可以用於搭配[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)回呼，以建立完整的物件參考圖形，執行階段。</span><span class="sxs-lookup"><span data-stu-id="255ba-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="255ba-114">Common language runtime (CLR) 可確保每個物件參考由一次報告`ObjectReferences`方法。</span><span class="sxs-lookup"><span data-stu-id="255ba-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="255ba-115">所傳回的物件識別碼`ObjectReferences`不自行，回呼期間有效，因為記憶體回收可能正在將物件移。</span><span class="sxs-lookup"><span data-stu-id="255ba-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="255ba-116">因此，分析工具必須不嘗試期間檢查物件`ObjectReferences`呼叫。</span><span class="sxs-lookup"><span data-stu-id="255ba-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="255ba-117">當[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)呼叫時，記憶體回收集合已完成，而且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="255ba-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="255ba-118">Null`ClassId`表示`objectId`正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="255ba-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="255ba-119">需求</span><span class="sxs-lookup"><span data-stu-id="255ba-119">Requirements</span></span>  
 <span data-ttu-id="255ba-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="255ba-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="255ba-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="255ba-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="255ba-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="255ba-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="255ba-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="255ba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="255ba-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="255ba-124">See Also</span></span>  
 [<span data-ttu-id="255ba-125">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="255ba-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
