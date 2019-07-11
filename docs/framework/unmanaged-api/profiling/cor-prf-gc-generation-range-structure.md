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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2f82b187a099ef7decca590da361f6b1abfa22e0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753794"
---
# <a name="corprfgcgenerationrange-structure"></a><span data-ttu-id="503f4-102">COR_PRF_GC_GENERATION_RANGE 結構</span><span class="sxs-lookup"><span data-stu-id="503f4-102">COR_PRF_GC_GENERATION_RANGE Structure</span></span>
<span data-ttu-id="503f4-103">說明正在進行記憶體回收的記憶體範圍 (亦即區塊)。</span><span class="sxs-lookup"><span data-stu-id="503f4-103">Describes a range (that is, block) of memory that is undergoing garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="503f4-104">語法</span><span class="sxs-lookup"><span data-stu-id="503f4-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="503f4-105">成員</span><span class="sxs-lookup"><span data-stu-id="503f4-105">Members</span></span>  
  
|<span data-ttu-id="503f4-106">成員</span><span class="sxs-lookup"><span data-stu-id="503f4-106">Member</span></span>|<span data-ttu-id="503f4-107">描述</span><span class="sxs-lookup"><span data-stu-id="503f4-107">Description</span></span>|  
|------------|-----------------|  
|`generation`|<span data-ttu-id="503f4-108">值為[COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)所屬的列舉，指定要產生的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="503f4-108">A value of the [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) enumeration that specifies the generation to which the block of memory belongs.</span></span>|  
|`rangeStart`|<span data-ttu-id="503f4-109">指定的記憶體區塊的開始位置的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="503f4-109">The ID of an object that specifies the starting location of the block of memory.</span></span>|  
|`rangeLength`|<span data-ttu-id="503f4-110">指定使用的記憶體區塊 （也就是在區塊內使用的記憶體數量） 部分的大小的整數指標。</span><span class="sxs-lookup"><span data-stu-id="503f4-110">A pointer to an integer that specifies the size of the used portion of the memory block (that is, the amount of memory used within the block).</span></span>|  
|`rangeLengthReserved`|<span data-ttu-id="503f4-111">為指定的記憶體區塊 （也就是保留給區塊的記憶體數量） 大小的整數指標。</span><span class="sxs-lookup"><span data-stu-id="503f4-111">A pointer to an integer that specifies the size of the memory block (that is, the amount of memory reserved for the block).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="503f4-112">備註</span><span class="sxs-lookup"><span data-stu-id="503f4-112">Remarks</span></span>  
 <span data-ttu-id="503f4-113">`rangeLength`保證是正確的值只有當[ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)或是[ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)，這兩個使用`COR_PRF_GC_GENERATION_RANGE`結構，從呼叫[ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)或[ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="503f4-113">The `rangeLength` value is guaranteed to be accurate only if [ICorProfilerInfo2::GetGenerationBounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md) or [ICorProfilerInfo2::GetObjectGeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md), both of which use the `COR_PRF_GC_GENERATION_RANGE` structure, is called from the [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) or the [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="503f4-114">需求</span><span class="sxs-lookup"><span data-stu-id="503f4-114">Requirements</span></span>  
 <span data-ttu-id="503f4-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="503f4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="503f4-116">**標頭：** CorProf.idl</span><span class="sxs-lookup"><span data-stu-id="503f4-116">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="503f4-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="503f4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="503f4-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="503f4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="503f4-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="503f4-119">See also</span></span>

- [<span data-ttu-id="503f4-120">分析結構</span><span class="sxs-lookup"><span data-stu-id="503f4-120">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
