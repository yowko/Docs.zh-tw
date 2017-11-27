---
title: "ICorProfilerInfo2::GetObjectGeneration 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetObjectGeneration
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetObjectGeneration
helpviewer_keywords:
- GetObjectGeneration method [.NET Framework profiling]
- ICorProfilerInfo2::GetObjectGeneration method [.NET Framework profiling]
ms.assetid: b0d25f76-0bd5-4aa6-96cf-bfec0e1de28b
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e90139f96638dbb1a183f98e754838ff52424fc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="77f27-102">ICorProfilerInfo2::GetObjectGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="77f27-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>
<span data-ttu-id="77f27-103">取得包含指定的物件在堆積的區段。</span><span class="sxs-lookup"><span data-stu-id="77f27-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f27-104">語法</span><span class="sxs-lookup"><span data-stu-id="77f27-104">Syntax</span></span>  
  
```  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="77f27-105">參數</span><span class="sxs-lookup"><span data-stu-id="77f27-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="77f27-106">[in]物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="77f27-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="77f27-107">[out]指標[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構描述中正在進行記憶體回收的層代的記憶體範圍 （亦即區塊）。</span><span class="sxs-lookup"><span data-stu-id="77f27-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="77f27-108">此範圍包含指定的物件。</span><span class="sxs-lookup"><span data-stu-id="77f27-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77f27-109">備註</span><span class="sxs-lookup"><span data-stu-id="77f27-109">Remarks</span></span>  
 <span data-ttu-id="77f27-110">`GetObjectGeneration`方法可能會呼叫從任何分析工具回呼，前提是尚未進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="77f27-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="77f27-111">也就是說，它可能會從回呼中呼叫任何除了之間發生[icorprofilercallback2:: Garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)和[icorprofilercallback2:: Garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="77f27-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f27-112">需求</span><span class="sxs-lookup"><span data-stu-id="77f27-112">Requirements</span></span>  
 <span data-ttu-id="77f27-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77f27-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77f27-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77f27-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77f27-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77f27-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77f27-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77f27-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f27-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f27-117">See Also</span></span>  
 [<span data-ttu-id="77f27-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="77f27-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="77f27-119">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="77f27-119">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
