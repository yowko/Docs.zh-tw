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
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="9d14b-102">ICorProfilerCallback::ObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="9d14b-102">ICorProfilerCallback::ObjectReferences Method</span></span>
<span data-ttu-id="9d14b-103">通知分析工具有關指定物件所參考記憶體中的物件。</span><span class="sxs-lookup"><span data-stu-id="9d14b-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d14b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d14b-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d14b-105">參數</span><span class="sxs-lookup"><span data-stu-id="9d14b-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="9d14b-106">在參考物件之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9d14b-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="9d14b-107">在指定的物件為實例之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9d14b-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="9d14b-108">在指定物件所參考的物件數目（也就是 `objectRefIds` 陣列中的元素數目）。</span><span class="sxs-lookup"><span data-stu-id="9d14b-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="9d14b-109">在`objectId`所參考之物件的識別碼陣列。</span><span class="sxs-lookup"><span data-stu-id="9d14b-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d14b-110">備註</span><span class="sxs-lookup"><span data-stu-id="9d14b-110">Remarks</span></span>  
 <span data-ttu-id="9d14b-111">在完成垃圾收集之後，會針對堆積中剩餘的每個物件呼叫 `ObjectReferences` 方法。</span><span class="sxs-lookup"><span data-stu-id="9d14b-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="9d14b-112">如果 profiler 從這個回呼傳回錯誤，分析服務將會停止叫用此回呼，直到下一次垃圾收集為止。</span><span class="sxs-lookup"><span data-stu-id="9d14b-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="9d14b-113">`ObjectReferences` 回呼可以與[ICorProfilerCallback：： RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)回呼搭配使用，以建立執行時間的完整物件參考圖形。</span><span class="sxs-lookup"><span data-stu-id="9d14b-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="9d14b-114">Common language runtime （CLR）可確保每個物件參考只會由 `ObjectReferences` 方法回報一次。</span><span class="sxs-lookup"><span data-stu-id="9d14b-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="9d14b-115">在回呼本身期間，`ObjectReferences` 傳回的物件識別碼無效，因為垃圾收集可能是在移動物件的中間。</span><span class="sxs-lookup"><span data-stu-id="9d14b-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="9d14b-116">因此，分析工具不得嘗試在 `ObjectReferences` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="9d14b-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="9d14b-117">呼叫[ICorProfilerCallback2：： GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)時，垃圾收集會完成，而且可以安全地執行檢查。</span><span class="sxs-lookup"><span data-stu-id="9d14b-117">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="9d14b-118">Null `ClassId` 表示 `objectId` 具有正在卸載的類型。</span><span class="sxs-lookup"><span data-stu-id="9d14b-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d14b-119">需求</span><span class="sxs-lookup"><span data-stu-id="9d14b-119">Requirements</span></span>  
 <span data-ttu-id="9d14b-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9d14b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d14b-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9d14b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d14b-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d14b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d14b-123">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d14b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d14b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d14b-124">See also</span></span>

- [<span data-ttu-id="9d14b-125">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="9d14b-125">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
