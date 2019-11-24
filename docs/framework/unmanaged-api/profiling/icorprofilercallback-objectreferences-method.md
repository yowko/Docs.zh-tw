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
ms.openlocfilehash: 4f8cfd912a3d6f66f5f2586a8942c7ce9bd52a63
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445882"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="49171-102">ICorProfilerCallback::ObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="49171-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="49171-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span><span class="sxs-lookup"><span data-stu-id="49171-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49171-104">語法</span><span class="sxs-lookup"><span data-stu-id="49171-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="49171-105">參數</span><span class="sxs-lookup"><span data-stu-id="49171-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="49171-106">[in] The ID of the object that is referencing objects.</span><span class="sxs-lookup"><span data-stu-id="49171-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="49171-107">[in] The ID of the class that the specified object is an instance of.</span><span class="sxs-lookup"><span data-stu-id="49171-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="49171-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span><span class="sxs-lookup"><span data-stu-id="49171-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="49171-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span><span class="sxs-lookup"><span data-stu-id="49171-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49171-110">備註</span><span class="sxs-lookup"><span data-stu-id="49171-110">Remarks</span></span>  
 <span data-ttu-id="49171-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span><span class="sxs-lookup"><span data-stu-id="49171-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="49171-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span><span class="sxs-lookup"><span data-stu-id="49171-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="49171-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span><span class="sxs-lookup"><span data-stu-id="49171-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="49171-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span><span class="sxs-lookup"><span data-stu-id="49171-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="49171-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span><span class="sxs-lookup"><span data-stu-id="49171-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="49171-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span><span class="sxs-lookup"><span data-stu-id="49171-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="49171-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span><span class="sxs-lookup"><span data-stu-id="49171-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="49171-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span><span class="sxs-lookup"><span data-stu-id="49171-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49171-119">需求</span><span class="sxs-lookup"><span data-stu-id="49171-119">Requirements</span></span>  
 <span data-ttu-id="49171-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="49171-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49171-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="49171-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="49171-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49171-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49171-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49171-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49171-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="49171-124">See also</span></span>

- [<span data-ttu-id="49171-125">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="49171-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
