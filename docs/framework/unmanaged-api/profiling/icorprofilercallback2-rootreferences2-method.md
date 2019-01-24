---
title: ICorProfilerCallback2::RootReferences2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4383bf8b7369f5906fe4664056f1cd938f04584
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54607536"
---
# <a name="icorprofilercallback2rootreferences2-method"></a><span data-ttu-id="f3a0d-102">ICorProfilerCallback2::RootReferences2 方法</span><span class="sxs-lookup"><span data-stu-id="f3a0d-102">ICorProfilerCallback2::RootReferences2 Method</span></span>
<span data-ttu-id="f3a0d-103">進行記憶體回收發生後，請通知分析工具之根參考。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-103">Notifies the profiler about root references after a garbage collection has occurred.</span></span> <span data-ttu-id="f3a0d-104">這個方法是擴充功能[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-104">This method is an extension of the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a0d-105">語法</span><span class="sxs-lookup"><span data-stu-id="f3a0d-105">Syntax</span></span>  
  
```  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3a0d-106">參數</span><span class="sxs-lookup"><span data-stu-id="f3a0d-106">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="f3a0d-107">[in]中的項目數`rootRefIds`， `rootKinds`， `rootFlags`，和`rootIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-107">[in] The number of elements in the `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="f3a0d-108">[in]物件識別碼，其中每個參考的靜態物件或堆疊上的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-108">[in] An array of object IDs, each of which references either a static object or an object on the stack.</span></span> <span data-ttu-id="f3a0d-109">中的項目`rootKinds`陣列提供要分類中的對應元素的資訊`rootRefIds`陣列。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-109">Elements in the `rootKinds` array provide information to classify corresponding elements in the `rootRefIds` array.</span></span>  
  
 `rootKinds`  
 <span data-ttu-id="f3a0d-110">[in]陣列[COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)值，指出記憶體回收根目錄的類型。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-110">[in] An array of [COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md) values that indicate the type of the garbage collection root.</span></span>  
  
 `rootFlags`  
 <span data-ttu-id="f3a0d-111">[in]陣列[COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)描述記憶體回收根目錄屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-111">[in] An array of [COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md) values that describe the properties of a garbage collection root.</span></span>  
  
 `rootIds`  
 <span data-ttu-id="f3a0d-112">[in]值指向包含記憶體回收根目錄，根據的值的其他資訊的整數的陣列的 UINT_PTR`rootKinds`參數。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-112">[in] An array of UINT_PTR values that point to an integer that contains additional information about the garbage collection root, depending on the value of the `rootKinds` parameter.</span></span>  
  
 <span data-ttu-id="f3a0d-113">如果根型別是堆疊，根識別碼是包含變數的函式。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-113">If the type of the root is a stack, the root ID is for the function that contains the variable.</span></span> <span data-ttu-id="f3a0d-114">如果該根識別碼為 0，函數就會是內部，CLR 不具名函式。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-114">If that root ID is 0, the function is an unnamed function that is internal to the CLR.</span></span> <span data-ttu-id="f3a0d-115">如果根型別是控制代碼，根識別碼很適合記憶體回收控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-115">If the type of the root is a handle, the root ID is for the garbage collection handle.</span></span> <span data-ttu-id="f3a0d-116">對於其他根型別，ID 會是不透明值，而且應該被忽略。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-116">For the other root types, the ID is an opaque value and should be ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3a0d-117">備註</span><span class="sxs-lookup"><span data-stu-id="f3a0d-117">Remarks</span></span>  
 <span data-ttu-id="f3a0d-118">`rootRefIds`， `rootKinds`， `rootFlags`，和`rootIds`陣列是平行陣列。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-118">The `rootRefIds`, `rootKinds`, `rootFlags`, and `rootIds` arrays are parallel arrays.</span></span> <span data-ttu-id="f3a0d-119">亦即`rootRefIds[i]`， `rootKinds[i]`， `rootFlags[i]`，和`rootIds[i]`全都會考量相同的根。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-119">That is, `rootRefIds[i]`, `rootKinds[i]`, `rootFlags[i]`, and `rootIds[i]` all concern the same root.</span></span>  
  
 <span data-ttu-id="f3a0d-120">兩者`RootReferences`和`RootReferences2`呼叫以通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-120">Both `RootReferences` and `RootReferences2` are called to notify the profiler.</span></span> <span data-ttu-id="f3a0d-121">程式碼剖析工具將通常實作其中一種方法或其他的但非兩者，因為傳入的資訊`RootReferences2`傳入的超集`RootReferences`。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-121">Profilers will normally implement one method or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="f3a0d-122">中的項目可能`rootRefIds`成為零，表示對應的根目錄參考為 null，且不是指在 managed 堆積上的物件。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-122">It is possible for entries in `rootRefIds` to be zero, which implies that the corresponding root reference is null and does not refer to an object on the managed heap.</span></span>  
  
 <span data-ttu-id="f3a0d-123">所傳回的物件識別碼`RootReferences2`不本身的回呼期間有效，因為記憶體回收可能正在將物件從舊位址移到新的位址。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-123">The object IDs returned by `RootReferences2` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="f3a0d-124">因此，分析工具不應嘗試在 `RootReferences2` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-124">Therefore, profilers should not attempt to inspect objects during a `RootReferences2` call.</span></span> <span data-ttu-id="f3a0d-125">當[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)是呼叫，所有物件都已移至其新位置和可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-125">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3a0d-126">需求</span><span class="sxs-lookup"><span data-stu-id="f3a0d-126">Requirements</span></span>  
 <span data-ttu-id="f3a0d-127">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f3a0d-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3a0d-128">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f3a0d-128">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f3a0d-129">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3a0d-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3a0d-130">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3a0d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a0d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3a0d-131">See also</span></span>
- [<span data-ttu-id="f3a0d-132">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="f3a0d-132">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="f3a0d-133">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="f3a0d-133">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
