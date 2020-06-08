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
ms.openlocfilehash: 91fb902aab678e29c6e74380e3576fa5c4ae62d4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500886"
---
# <a name="cor_prf_gc_generation_range-structure"></a><span data-ttu-id="3d11e-102">COR_PRF_GC_GENERATION_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="3d11e-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="3d11e-103">說明正在進行記憶體回收的記憶體範圍 (亦即區塊)。</span><span class="sxs-lookup"><span data-stu-id="3d11e-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d11e-104">語法</span><span class="sxs-lookup"><span data-stu-id="3d11e-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="3d11e-105">成員</span><span class="sxs-lookup"><span data-stu-id="3d11e-105">Members</span></span>  
  
|<span data-ttu-id="3d11e-106">成員</span><span class="sxs-lookup"><span data-stu-id="3d11e-106">Member</span></span>|<span data-ttu-id="3d11e-107">說明</span><span class="sxs-lookup"><span data-stu-id="3d11e-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="3d11e-108">[COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md)列舉的值，指定記憶體區塊所屬的世代。</span><span class="sxs-lookup"><span data-stu-id="3d11e-108">A value of the [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="3d11e-109">物件的識別碼，指定記憶體區塊的開始位置。</span><span class="sxs-lookup"><span data-stu-id="3d11e-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="3d11e-110">整數的指標，指定記憶體區塊所使用部分的大小（也就是區塊中使用的記憶體數量）。</span><span class="sxs-lookup"><span data-stu-id="3d11e-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="3d11e-111">整數的指標，指定記憶體區塊的大小（也就是為區塊保留的記憶體數量）。</span><span class="sxs-lookup"><span data-stu-id="3d11e-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d11e-112">備註</span><span class="sxs-lookup"><span data-stu-id="3d11e-112">Remarks</span></span>  
 <span data-ttu-id="3d11e-113">`rangeLength`只有在從 ICorProfilerCallback2：： GarbageCollectionStarted 或 ICorProfilerCallback2：： GarbageCollectionFinished 方法呼叫[ICorProfilerInfo2：： GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md)或[ICorProfilerInfo2：： GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md)（兩者都使用 `COR_PRF_GC_GENERATION_RANGE` 結構）時[ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) ，才保證此值為[ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)精確。</span><span class="sxs-lookup"><span data-stu-id="3d11e-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d11e-114">規格需求</span><span class="sxs-lookup"><span data-stu-id="3d11e-114">Requirements</span></span>  
 <span data-ttu-id="3d11e-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3d11e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d11e-116">**標頭：** Corprof.idl .idl</span><span class="sxs-lookup"><span data-stu-id="3d11e-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="3d11e-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d11e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d11e-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d11e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d11e-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d11e-119">See also</span></span>

- [<span data-ttu-id="3d11e-120">分析結構</span><span class="sxs-lookup"><span data-stu-id="3d11e-120">Profiling Structures</span></span>](profiling-structures.md)
