---
title: COR_PRF_GC_GENERATION 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION
helpviewer_keywords:
- COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type:
- apiref
ms.openlocfilehash: d01b864be231e5b0a3fd72dc2f3636a87c8cae83
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448637"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="fa6b1-102">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="fa6b1-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="fa6b1-103">Identifies a garbage-collection generation.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa6b1-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa6b1-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="fa6b1-105">Members</span><span class="sxs-lookup"><span data-stu-id="fa6b1-105">Members</span></span>  
  
|<span data-ttu-id="fa6b1-106">成員</span><span class="sxs-lookup"><span data-stu-id="fa6b1-106">Member</span></span>|<span data-ttu-id="fa6b1-107">描述</span><span class="sxs-lookup"><span data-stu-id="fa6b1-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="fa6b1-108">The object is stored as generation 0.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="fa6b1-109">The object is stored as generation 1.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="fa6b1-110">The object is stored as generation 2.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="fa6b1-111">The object is stored in the large-object heap.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa6b1-112">備註</span><span class="sxs-lookup"><span data-stu-id="fa6b1-112">Remarks</span></span>  
 <span data-ttu-id="fa6b1-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="fa6b1-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="fa6b1-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="fa6b1-116">Other allocated objects start out belonging to generation 0.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="fa6b1-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="fa6b1-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="fa6b1-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="fa6b1-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="fa6b1-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa6b1-121">需求</span><span class="sxs-lookup"><span data-stu-id="fa6b1-121">Requirements</span></span>  
 <span data-ttu-id="fa6b1-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fa6b1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa6b1-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa6b1-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa6b1-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa6b1-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa6b1-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa6b1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6b1-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="fa6b1-126">See also</span></span>

- [<span data-ttu-id="fa6b1-127">分析列舉</span><span class="sxs-lookup"><span data-stu-id="fa6b1-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
