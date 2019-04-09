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
ms.openlocfilehash: 64e362be57a96bbe0f61b964ab413234f30d0ed1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143776"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="dd659-102">ICorProfilerInfo2::GetObjectGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="dd659-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="dd659-103">取得包含指定的物件堆積的區段。</span><span class="sxs-lookup"><span data-stu-id="dd659-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd659-104">語法</span><span class="sxs-lookup"><span data-stu-id="dd659-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd659-105">參數</span><span class="sxs-lookup"><span data-stu-id="dd659-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="dd659-106">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="dd659-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="dd659-107">[out]指標[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構，正在進行記憶體回收的層代中描述的記憶體範圍 （亦即區塊）。</span><span class="sxs-lookup"><span data-stu-id="dd659-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="dd659-108">此範圍會包含指定的物件。</span><span class="sxs-lookup"><span data-stu-id="dd659-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dd659-109">備註</span><span class="sxs-lookup"><span data-stu-id="dd659-109">Remarks</span></span>  
 <span data-ttu-id="dd659-110">`GetObjectGeneration`方法可能會從回呼中呼叫任何程式碼剖析工具，前提是尚未進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="dd659-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="dd659-111">也就是說，它可能會從回呼中呼叫任何除外之間發生[ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)並[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="dd659-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd659-112">需求</span><span class="sxs-lookup"><span data-stu-id="dd659-112">Requirements</span></span>  
 <span data-ttu-id="dd659-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dd659-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd659-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dd659-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dd659-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd659-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="dd659-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="dd659-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dd659-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd659-117">See also</span></span>

- [<span data-ttu-id="dd659-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="dd659-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="dd659-119">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="dd659-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
