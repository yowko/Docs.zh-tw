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
ms.openlocfilehash: 4ba404692bef84c0522a799c61f07eac341eaab4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703840"
---
# <a name="icorprofilerinfo2getobjectgeneration-method"></a><span data-ttu-id="5f13a-102">ICorProfilerInfo2::GetObjectGeneration 方法</span><span class="sxs-lookup"><span data-stu-id="5f13a-102">ICorProfilerInfo2::GetObjectGeneration Method</span></span>

<span data-ttu-id="5f13a-103">取得包含指定物件之堆積的區段。</span><span class="sxs-lookup"><span data-stu-id="5f13a-103">Gets the segment of the heap that contains the specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f13a-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f13a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectGeneration(  
    [in] ObjectID objectId,  
    [out] COR_PRF_GC_GENERATION_RANGE *range);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f13a-105">參數</span><span class="sxs-lookup"><span data-stu-id="5f13a-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="5f13a-106">在物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5f13a-106">[in] The ID of the object.</span></span>  
  
 `range`  
 <span data-ttu-id="5f13a-107">擴展 [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) 結構的指標，其描述範圍 (也就是在產生中進行垃圾收集的區塊) 記憶體。</span><span class="sxs-lookup"><span data-stu-id="5f13a-107">[out] A pointer to a [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure, which describes a range (that is, a block) of memory within the generation that is undergoing garbage collection.</span></span> <span data-ttu-id="5f13a-108">此範圍包含指定的物件。</span><span class="sxs-lookup"><span data-stu-id="5f13a-108">This range contains the specified object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f13a-109">備註</span><span class="sxs-lookup"><span data-stu-id="5f13a-109">Remarks</span></span>  

 <span data-ttu-id="5f13a-110">`GetObjectGeneration`如果垃圾收集不在進行中，則可以從任何分析工具回呼呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="5f13a-110">The `GetObjectGeneration` method may be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="5f13a-111">也就是說，它可以從任何回呼呼叫，除了 [ICorProfilerCallback2：： GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) 和 [ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)之間發生的回呼。</span><span class="sxs-lookup"><span data-stu-id="5f13a-111">That is, it may be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f13a-112">需求</span><span class="sxs-lookup"><span data-stu-id="5f13a-112">Requirements</span></span>  

 <span data-ttu-id="5f13a-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5f13a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f13a-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5f13a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5f13a-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f13a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f13a-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f13a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f13a-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f13a-117">See also</span></span>

- [<span data-ttu-id="5f13a-118">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="5f13a-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="5f13a-119">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="5f13a-119">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
