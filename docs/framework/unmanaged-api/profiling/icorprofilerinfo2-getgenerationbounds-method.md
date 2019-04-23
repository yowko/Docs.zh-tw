---
title: ICorProfilerInfo2::GetGenerationBounds 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110374"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a><span data-ttu-id="24159-102">ICorProfilerInfo2::GetGenerationBounds 方法</span><span class="sxs-lookup"><span data-stu-id="24159-102">ICorProfilerInfo2::GetGenerationBounds Method</span></span>
<span data-ttu-id="24159-103">取得記憶體區域，也就是堆積的區段，會組成各種記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="24159-103">Gets the memory regions, which are segments of the heap, that make up the various garbage collection generations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24159-104">語法</span><span class="sxs-lookup"><span data-stu-id="24159-104">Syntax</span></span>  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24159-105">參數</span><span class="sxs-lookup"><span data-stu-id="24159-105">Parameters</span></span>  
 `cObjectRanges`  
 <span data-ttu-id="24159-106">[in] 對於 `ranges` 陣列，呼叫端所配置的項目數目 。</span><span class="sxs-lookup"><span data-stu-id="24159-106">[in] The number of elements allocated by the caller for the `ranges` array.</span></span>  
  
 `pcObjectRanges`  
 <span data-ttu-id="24159-107">[out] 指定範圍總數的整數指標，其中某些或全部都將在 `ranges` 陣列傳回。</span><span class="sxs-lookup"><span data-stu-id="24159-107">[out] A pointer to an integer that specifies the total number of ranges, some or all of which will be returned in the `ranges` array.</span></span>  
  
 `ranges`  
 <span data-ttu-id="24159-108">[out]陣列[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構，其中每個正在進行記憶體回收的層代中描述的記憶體範圍 （亦即區塊）。</span><span class="sxs-lookup"><span data-stu-id="24159-108">[out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24159-109">備註</span><span class="sxs-lookup"><span data-stu-id="24159-109">Remarks</span></span>  
 <span data-ttu-id="24159-110">`GetGenerationBounds` 方法可以從任何分析工具回呼中呼叫，前提是尚未進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="24159-110">The `GetGenerationBounds` method can be called from any profiler callback, provided that garbage collection is not in progress.</span></span> <span data-ttu-id="24159-111">也就是它可以從回呼中呼叫任何除外之間發生[ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)並[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)。</span><span class="sxs-lookup"><span data-stu-id="24159-111">That is, it can be called from any callback except those that occur between [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) and [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).</span></span>  
  
 <span data-ttu-id="24159-112">多數層代移位發生在記憶體回收期間。</span><span class="sxs-lookup"><span data-stu-id="24159-112">Most shifting of generations takes place during garbage collections.</span></span> <span data-ttu-id="24159-113">層代可能會在回收之間成長，但通常不會移動。</span><span class="sxs-lookup"><span data-stu-id="24159-113">Generations might grow between collections but generally do not move around.</span></span> <span data-ttu-id="24159-114">因此，呼叫 `GetGenerationBounds` 最有趣的地方位於 `ICorProfilerCallback2::GarbageCollectionStarted` 和 `ICorProfilerCallback2::GarbageCollectionFinished`。</span><span class="sxs-lookup"><span data-stu-id="24159-114">Therefore, the most interesting places to call `GetGenerationBounds` are in `ICorProfilerCallback2::GarbageCollectionStarted` and `ICorProfilerCallback2::GarbageCollectionFinished`.</span></span>  
  
 <span data-ttu-id="24159-115">在程式啟動期間，某些物件會由 Common Language Runtime (CLR) 本身所配置，通常在層代 3 和 0 中。</span><span class="sxs-lookup"><span data-stu-id="24159-115">During program startup, some objects are allocated by the common language runtime (CLR) itself, generally in generations 3 and 0.</span></span> <span data-ttu-id="24159-116">因此，Managed 程式碼開始執行時，這些層代將已包含物件。</span><span class="sxs-lookup"><span data-stu-id="24159-116">Thus, by the time managed code starts executing, these generations will already contain objects.</span></span> <span data-ttu-id="24159-117">除了由記憶體回收行程所產生的 Dummy 物件之外，層代 1 和 2 通常是空的。</span><span class="sxs-lookup"><span data-stu-id="24159-117">Generations 1 and 2 will normally be empty, except for dummy objects that are generated by the garbage collector.</span></span> <span data-ttu-id="24159-118">(Dummy 物件的大小在 32 位元 CLR 實作中為 12 個位元組；64 位元實作中的大小較大)。您也可能會看到層代 2 範圍，位於原生映像產生器 (NGen.exe) 模組產生之模組內。</span><span class="sxs-lookup"><span data-stu-id="24159-118">(The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe).</span></span> <span data-ttu-id="24159-119">在此情況下，第 2 代中的物件是*凍結物件*，而在 NGen.exe 執行時而非由記憶體回收行程配置。</span><span class="sxs-lookup"><span data-stu-id="24159-119">In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.</span></span>  
  
 <span data-ttu-id="24159-120">這個函式會使用呼叫端配置的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="24159-120">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24159-121">需求</span><span class="sxs-lookup"><span data-stu-id="24159-121">Requirements</span></span>  
 <span data-ttu-id="24159-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24159-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24159-123">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24159-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24159-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24159-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24159-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24159-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24159-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24159-126">See also</span></span>

- [<span data-ttu-id="24159-127">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="24159-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="24159-128">ICorProfilerInfo2 介面</span><span class="sxs-lookup"><span data-stu-id="24159-128">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="24159-129">分析介面</span><span class="sxs-lookup"><span data-stu-id="24159-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="24159-130">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="24159-130">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
