---
title: "ICorProfilerCallback2::RootReferences2 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.RootReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8a0b2e23ba586e7a20ed11de6433b2d87cbe7219
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="1c057-102">ICorProfilerCallback2::RootReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="1c057-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="1c057-103">在記憶體回收發生後，請通知根參考的相關程式碼剖析工具。</span><span class="sxs-lookup"><span data-stu-id="1c057-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="1c057-104">這個方法是延伸[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1c057-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c057-105">語法</span><span class="sxs-lookup"><span data-stu-id="1c057-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c057-106">參數</span><span class="sxs-lookup"><span data-stu-id="1c057-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="1c057-107">[in]中的項目數`rootRefIds`， `rootKinds`， `rootFlags`，和`rootIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="1c057-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="1c057-108">[in]陣列的物件識別碼，其中每個參考的靜態物件或物件在堆疊上。</span><span class="sxs-lookup"><span data-stu-id="1c057-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="1c057-109">中的項目`rootKinds`陣列提供資訊給分類中的對應元素`rootRefIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="1c057-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="1c057-110">[in]陣列[COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)值，表示記憶體回收根目錄的類型。</span><span class="sxs-lookup"><span data-stu-id="1c057-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="1c057-111">[in]陣列[COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)描述記憶體回收根目錄屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1c057-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="1c057-112">[in]UINT_PTR 陣列值會指向包含記憶體回收根目錄，根據的值的其他資訊的整數`rootKinds`參數。</span><span class="sxs-lookup"><span data-stu-id="1c057-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="1c057-113">如果根型別是指堆疊，根 ID 就是包含變數的函式。</span><span class="sxs-lookup"><span data-stu-id="1c057-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="1c057-114">如果該根識別碼為 0，函式是 CLR 內部未命名函式。</span><span class="sxs-lookup"><span data-stu-id="1c057-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="1c057-115">如果根型別是控制代碼，根識別碼就是記憶體回收控制代碼。</span><span class="sxs-lookup"><span data-stu-id="1c057-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="1c057-116">對於其他根類型識別碼是不透明值，應予忽略。</span><span class="sxs-lookup"><span data-stu-id="1c057-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c057-117">備註</span><span class="sxs-lookup"><span data-stu-id="1c057-117">Remarks</span></span>  
 <span data-ttu-id="1c057-118">`rootRefIds`， `rootKinds`， `rootFlags`，和`rootIds`是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="1c057-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="1c057-119">也就是說， `rootRefIds[i]`， `rootKinds[i]`， `rootFlags[i]`，和`rootIds[i]`全都會考量位於相同的根目錄。</span><span class="sxs-lookup"><span data-stu-id="1c057-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="1c057-120">同時`RootReferences`和`RootReferences2`呼叫以通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="1c057-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="1c057-121">分析工具將通常實作一種方法或另一個，但不可同時因為資訊傳入`RootReferences2`為傳入的超集`RootReferences`。</span><span class="sxs-lookup"><span data-stu-id="1c057-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="1c057-122">中的項目可能會`rootRefIds`成為零，表示對應的根參考為 null，且不是指受管理的堆積上的物件。</span><span class="sxs-lookup"><span data-stu-id="1c057-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="1c057-123">所傳回的物件識別碼`RootReferences2`不自行，回呼期間有效，因為記憶體回收可能正在將物件從舊位址移到新的位址。</span><span class="sxs-lookup"><span data-stu-id="1c057-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="1c057-124">因此，分析工具不應嘗試在 `RootReferences2` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="1c057-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="1c057-125">當[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)是呼叫，所有物件都已移至其新位置並且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="1c057-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c057-126">需求</span><span class="sxs-lookup"><span data-stu-id="1c057-126">Requirements</span></span>  
 <span data-ttu-id="1c057-127">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1c057-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c057-128">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c057-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c057-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c057-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c057-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c057-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c057-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c057-131">See Also</span></span>  
 [<span data-ttu-id="1c057-132">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="1c057-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="1c057-133">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="1c057-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
