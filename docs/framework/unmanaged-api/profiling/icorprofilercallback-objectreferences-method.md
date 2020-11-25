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
ms.openlocfilehash: 9485e3ca657ab108d2bcc9d00b1c475f8ee3c086
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703950"
---
# <a name="icorprofilercallbackobjectreferences-method"></a><span data-ttu-id="098bd-102">ICorProfilerCallback::ObjectReferences 方法</span><span class="sxs-lookup"><span data-stu-id="098bd-102">ICorProfilerCallback::ObjectReferences Method</span></span>

<span data-ttu-id="098bd-103">通知分析工具有關指定物件正在參考之記憶體中的物件。</span><span class="sxs-lookup"><span data-stu-id="098bd-103">Notifies the profiler about objects in memory that are being referenced by the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="098bd-104">語法</span><span class="sxs-lookup"><span data-stu-id="098bd-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="098bd-105">參數</span><span class="sxs-lookup"><span data-stu-id="098bd-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="098bd-106">在參考物件之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="098bd-106">[in] The ID of the object that is referencing objects.</span></span>  
  
 `classId`  
 <span data-ttu-id="098bd-107">在指定之物件是實例之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="098bd-107">[in] The ID of the class that the specified object is an instance of.</span></span>  
  
 `cObjectRefs`  
 <span data-ttu-id="098bd-108">在指定之物件所參考的物件數目 (也就是陣列中的元素數目 `objectRefIds`) 。</span><span class="sxs-lookup"><span data-stu-id="098bd-108">[in] The number of objects referenced by the specified object (that is, the number of elements in the `objectRefIds` array).</span></span>  
  
 `objectRefIds`  
 <span data-ttu-id="098bd-109">在所參考之物件的識別碼陣列 `objectId` 。</span><span class="sxs-lookup"><span data-stu-id="098bd-109">[in] An array of IDs of objects that are being referenced by `objectId`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="098bd-110">備註</span><span class="sxs-lookup"><span data-stu-id="098bd-110">Remarks</span></span>  

 <span data-ttu-id="098bd-111">在 `ObjectReferences` 垃圾收集完成之後，會針對堆積中剩餘的每個物件呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="098bd-111">The `ObjectReferences` method is called for each object remaining in the heap after a garbage collection has completed.</span></span> <span data-ttu-id="098bd-112">如果分析工具傳回此回呼的錯誤，程式碼剖析服務將會停止叫用此回呼，直到下一次垃圾收集為止。</span><span class="sxs-lookup"><span data-stu-id="098bd-112">If the profiler returns an error from this callback, the profiling services will discontinue invoking this callback until the next garbage collection.</span></span>  
  
 <span data-ttu-id="098bd-113">`ObjectReferences`回呼可以搭配[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)回呼使用，以建立執行時間的完整物件參考圖形。</span><span class="sxs-lookup"><span data-stu-id="098bd-113">The `ObjectReferences` callback can be used in conjunction with the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) callback to create a complete object reference graph for the runtime.</span></span> <span data-ttu-id="098bd-114">Common language runtime (CLR) 可確保每個物件參考只會由方法回報一次 `ObjectReferences` 。</span><span class="sxs-lookup"><span data-stu-id="098bd-114">The common language runtime (CLR) ensures that each object reference is reported only once by the `ObjectReferences` method.</span></span>  
  
 <span data-ttu-id="098bd-115">在 `ObjectReferences` 回呼本身期間，傳回的物件識別碼不是有效的，因為垃圾收集可能在移動物件的中間。</span><span class="sxs-lookup"><span data-stu-id="098bd-115">The object IDs returned by `ObjectReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects.</span></span> <span data-ttu-id="098bd-116">因此，分析工具不能在呼叫期間嘗試檢查物件 `ObjectReferences` 。</span><span class="sxs-lookup"><span data-stu-id="098bd-116">Therefore, profilers must not attempt to inspect objects during an `ObjectReferences` call.</span></span> <span data-ttu-id="098bd-117">當呼叫 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) 時，垃圾收集會完成，而且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="098bd-117">When [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) is called, the garbage collection is complete and inspection can be safely done.</span></span>  
  
 <span data-ttu-id="098bd-118">Null `ClassId` 表示 `objectId` 具有正在卸載的型別。</span><span class="sxs-lookup"><span data-stu-id="098bd-118">A null `ClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="098bd-119">需求</span><span class="sxs-lookup"><span data-stu-id="098bd-119">Requirements</span></span>  

 <span data-ttu-id="098bd-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="098bd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="098bd-121">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="098bd-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="098bd-122">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="098bd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="098bd-123">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="098bd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="098bd-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="098bd-124">See also</span></span>

- [<span data-ttu-id="098bd-125">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="098bd-125">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
