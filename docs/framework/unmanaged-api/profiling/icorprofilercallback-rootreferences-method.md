---
title: ICorProfilerCallback::RootReferences 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
ms.openlocfilehash: 9c96cacf508ef5c056a1ff4469247393fdfb9e9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444469"
---
# <a name="icorprofilercallbackrootreferences-method"></a><span data-ttu-id="3bcb9-102">ICorProfilerCallback::RootReferences 方法</span><span class="sxs-lookup"><span data-stu-id="3bcb9-102">ICorProfilerCallback::RootReferences Method</span></span>
<span data-ttu-id="3bcb9-103">在垃圾收集之後，使用根參考的相關資訊來通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-103">Notifies the profiler with information about root references after garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bcb9-104">語法</span><span class="sxs-lookup"><span data-stu-id="3bcb9-104">Syntax</span></span>  
  
```cpp  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bcb9-105">參數</span><span class="sxs-lookup"><span data-stu-id="3bcb9-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="3bcb9-106">在`rootRefIds` 陣列中的參考數目。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-106">[in] The number of references in the `rootRefIds` array.</span></span>  
  
 `rootRefIds`  
 <span data-ttu-id="3bcb9-107">在物件識別碼的陣列，參考堆疊上的靜態物件或物件。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-107">[in] An array of object IDs that reference either a static object or an object on the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bcb9-108">備註</span><span class="sxs-lookup"><span data-stu-id="3bcb9-108">Remarks</span></span>  
 <span data-ttu-id="3bcb9-109">`RootReferences` 和[ICorProfilerCallback2：： RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)都會呼叫來通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-109">Both `RootReferences` and [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) are called to notify the profiler.</span></span> <span data-ttu-id="3bcb9-110">分析工具通常會實作為其中之一，但不會同時執行這兩個，因為傳入的資訊 `RootReferences2` 是傳入 `RootReferences`的超集合。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-110">Profilers will normally implement one or the other, but not both, because the information passed in `RootReferences2` is a superset of that passed in `RootReferences`.</span></span>  
  
 <span data-ttu-id="3bcb9-111">`rootRefIds` 陣列可以包含 null 物件。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-111">It is possible for the `rootRefIds` array to contain a null object.</span></span> <span data-ttu-id="3bcb9-112">例如，在堆疊上宣告的所有物件參考都會被垃圾收集行程視為根，而且一律會報告。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-112">For example, all object references declared on the stack are treated as roots by the garbage collector and will always be reported.</span></span>  
  
 <span data-ttu-id="3bcb9-113">在回呼本身期間，`RootReferences` 傳回的物件識別碼無效，因為垃圾收集可能正在將物件從舊位址移至新位址。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-113">The object IDs returned by `RootReferences` are not valid during the callback itself, because the garbage collection might be in the middle of moving objects from old addresses to new addresses.</span></span> <span data-ttu-id="3bcb9-114">因此，分析工具不得嘗試在 `RootReferences` 呼叫期間檢查物件。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-114">Therefore, profilers must not attempt to inspect objects during a `RootReferences` call.</span></span> <span data-ttu-id="3bcb9-115">呼叫[ICorProfilerCallback2：： GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)時，所有物件都已移至其新位置，而且可以安全地進行檢查。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-115">When [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) is called, all objects have been moved to their new locations and can be safely inspected.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bcb9-116">需求</span><span class="sxs-lookup"><span data-stu-id="3bcb9-116">Requirements</span></span>  
 <span data-ttu-id="3bcb9-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3bcb9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bcb9-118">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3bcb9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3bcb9-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bcb9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bcb9-120">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bcb9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bcb9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3bcb9-121">See also</span></span>

- [<span data-ttu-id="3bcb9-122">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="3bcb9-122">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
