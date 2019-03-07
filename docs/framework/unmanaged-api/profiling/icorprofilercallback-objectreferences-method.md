---
title: ICorProfilerCallback::ObjectReferences 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9659f37f0ae9297837dbc4b1602cb00b8eff2fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471443"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="e340b-102">ICorProfilerCallback::ObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="e340b-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="e340b-103">通知分析工具有關記憶體中所指定的物件所參考的物件。</span><span class="sxs-lookup"><span data-stu-id="e340b-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e340b-104">語法</span><span class="sxs-lookup"><span data-stu-id="e340b-104">Syntax</span></span>  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="e340b-105">參數</span><span class="sxs-lookup"><span data-stu-id="e340b-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e340b-106">[in]物件所參考物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e340b-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="e340b-107">[in]類別的指定的物件的執行個體識別碼。</span><span class="sxs-lookup"><span data-stu-id="e340b-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="e340b-108">[in]所指定的物件參考的物件數目 (也就是中的元素數目`objectRefIds`陣列)。</span><span class="sxs-lookup"><span data-stu-id="e340b-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="e340b-109">[in]所參考的物件識別碼的陣列`objectId`。</span><span class="sxs-lookup"><span data-stu-id="e340b-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e340b-110">備註</span><span class="sxs-lookup"><span data-stu-id="e340b-110">Remarks</span></span>  
 <span data-ttu-id="e340b-111">`ObjectReferences`為進行記憶體回收完成後，在堆積中剩餘的每個物件呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e340b-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="e340b-112">如果分析工具從此回呼傳回錯誤，將會叫用這個回呼，直到下一個記憶體回收來中止的程式碼剖析的服務。</span><span class="sxs-lookup"><span data-stu-id="e340b-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="e340b-113">`ObjectReferences`回呼可以用於搭配[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)回呼，以建立完整的物件參考圖形的執行階段。</span><span class="sxs-lookup"><span data-stu-id="e340b-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="e340b-114">Common language runtime (CLR) 可確保每個物件參考由一次報告`ObjectReferences`方法。</span><span class="sxs-lookup"><span data-stu-id="e340b-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="e340b-115">所傳回的物件識別碼`ObjectReferences`不本身的回呼期間有效，因為記憶體回收可能正在移動物件。</span><span class="sxs-lookup"><span data-stu-id="e340b-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="e340b-116">因此，程式碼剖析工具不得嘗試期間檢查物件`ObjectReferences`呼叫。</span><span class="sxs-lookup"><span data-stu-id="e340b-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="e340b-117">當[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)呼叫時，記憶體回收集合完畢，並且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="e340b-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="e340b-118">Null`ClassId`表示`objectId`正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="e340b-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e340b-119">需求</span><span class="sxs-lookup"><span data-stu-id="e340b-119">Requirements</span></span>  
 <span data-ttu-id="e340b-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e340b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e340b-121">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e340b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e340b-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e340b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e340b-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e340b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e340b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e340b-124">See also</span></span>
- [<span data-ttu-id="e340b-125">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e340b-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
