---
title: ICorProfilerInfo2::GetObjectGeneration 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetObjectGeneration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 729ae390d36f82cbafd46385b396d6513489628e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474776"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="7264a-102">ICorProfilerInfo2::GetObjectGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="7264a-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="7264a-103">取得包含指定的物件堆積的區段。</span><span class="sxs-lookup"><span data-stu-id="7264a-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7264a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7264a-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7264a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7264a-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="7264a-106">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="7264a-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="7264a-107">[out]指標[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構，正在進行記憶體回收的層代中描述的記憶體範圍 （亦即區塊）。</span><span class="sxs-lookup"><span data-stu-id="7264a-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="7264a-108">此範圍會包含指定的物件。</span><span class="sxs-lookup"><span data-stu-id="7264a-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7264a-109">備註</span><span class="sxs-lookup"><span data-stu-id="7264a-109">Remarks</span></span>  
 <span data-ttu-id="7264a-110">`GetObjectGeneration`方法可能會從回呼中呼叫任何程式碼剖析工具，前提是尚未進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="7264a-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="7264a-111">也就是說，它可能會從回呼中呼叫任何除外之間發生[ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)並[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="7264a-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7264a-112">需求</span><span class="sxs-lookup"><span data-stu-id="7264a-112">Requirements</span></span>  
 <span data-ttu-id="7264a-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7264a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7264a-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7264a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7264a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7264a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7264a-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7264a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7264a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7264a-117">See also</span></span>
- [<span data-ttu-id="7264a-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="7264a-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7264a-119">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="7264a-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
