---
title: COR_PRF_GC_GENERATION_RANGE 結構
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
ms.openlocfilehash: 682aac9729519e0861ae6e6f60df78a30063c278
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867201"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="4d8ed-102">COR_PRF_GC_GENERATION_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="4d8ed-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="4d8ed-103">說明正在進行記憶體回收的記憶體範圍 (亦即區塊)。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d8ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d8ed-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="4d8ed-105">Members</span><span class="sxs-lookup"><span data-stu-id="4d8ed-105">Members</span></span>  
  
|<span data-ttu-id="4d8ed-106">成員</span><span class="sxs-lookup"><span data-stu-id="4d8ed-106">Member</span></span>|<span data-ttu-id="4d8ed-107">描述</span><span class="sxs-lookup"><span data-stu-id="4d8ed-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="4d8ed-108">[COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md)列舉的值，指定記憶體區塊所屬的世代。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="4d8ed-109">物件的識別碼，指定記憶體區塊的開始位置。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="4d8ed-110">整數的指標，指定記憶體區塊所使用部分的大小（也就是區塊中使用的記憶體數量）。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="4d8ed-111">整數的指標，指定記憶體區塊的大小（也就是為區塊保留的記憶體數量）。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d8ed-112">備註</span><span class="sxs-lookup"><span data-stu-id="4d8ed-112">Remarks</span></span>  
 <span data-ttu-id="4d8ed-113">只有在從[ICorProfilerCallback2：： GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)或[ICorProfilerCallback2：： GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)方法呼叫[ICorProfilerInfo2：： GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md)或[ICorProfilerInfo2：： GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md)（兩者都使用 `COR_PRF_GC_GENERATION_RANGE` 結構）時，`rangeLength` 值才保證是正確的。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d8ed-114">需求</span><span class="sxs-lookup"><span data-stu-id="4d8ed-114">Requirements</span></span>  
 <span data-ttu-id="4d8ed-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d8ed-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d8ed-116">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="4d8ed-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="4d8ed-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d8ed-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d8ed-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d8ed-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d8ed-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="4d8ed-119">See also</span></span>

- [<span data-ttu-id="4d8ed-120">分析結構</span><span class="sxs-lookup"><span data-stu-id="4d8ed-120">Profiling Structures</span></span>](profiling-structures.md)
