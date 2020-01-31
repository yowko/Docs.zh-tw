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
ms.openlocfilehash: 4eff8472e353c4e5fd2505b281cc9efc89f013fc
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867204"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="34008-102">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="34008-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="34008-103">識別垃圾收集的產生。</span><span class="sxs-lookup"><span data-stu-id="34008-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34008-104">語法</span><span class="sxs-lookup"><span data-stu-id="34008-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="34008-105">Members</span><span class="sxs-lookup"><span data-stu-id="34008-105">Members</span></span>  
  
|<span data-ttu-id="34008-106">成員</span><span class="sxs-lookup"><span data-stu-id="34008-106">Member</span></span>|<span data-ttu-id="34008-107">描述</span><span class="sxs-lookup"><span data-stu-id="34008-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="34008-108">物件會儲存為層代0。</span><span class="sxs-lookup"><span data-stu-id="34008-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="34008-109">物件會儲存為第1代。</span><span class="sxs-lookup"><span data-stu-id="34008-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="34008-110">物件會儲存為層代2。</span><span class="sxs-lookup"><span data-stu-id="34008-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="34008-111">物件會儲存在大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="34008-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34008-112">備註</span><span class="sxs-lookup"><span data-stu-id="34008-112">Remarks</span></span>  
 <span data-ttu-id="34008-113">垃圾收集行程藉由將物件根據年齡分割成層代，來改善記憶體管理效能。</span><span class="sxs-lookup"><span data-stu-id="34008-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="34008-114">垃圾收集行程目前使用三個層代，編號為0、1和2，再加上用於大型物件的特殊堆積區段。</span><span class="sxs-lookup"><span data-stu-id="34008-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="34008-115">其大小大於特定值的物件會儲存在大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="34008-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="34008-116">其他已配置的物件會從屬於層代0開始。</span><span class="sxs-lookup"><span data-stu-id="34008-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="34008-117">在層代0中進行垃圾收集之後存在的所有物件都會升級至層代1。</span><span class="sxs-lookup"><span data-stu-id="34008-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="34008-118">在層代1中進行垃圾收集後存在的物件會移至層代2。</span><span class="sxs-lookup"><span data-stu-id="34008-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="34008-119">使用世代表示垃圾收集行程在任何時候都只能處理已設定物件的子集。</span><span class="sxs-lookup"><span data-stu-id="34008-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="34008-120">[COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)結構會使用 `COR_PRF_GC_GENERATION` 列舉。</span><span class="sxs-lookup"><span data-stu-id="34008-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34008-121">需求</span><span class="sxs-lookup"><span data-stu-id="34008-121">Requirements</span></span>  
 <span data-ttu-id="34008-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="34008-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34008-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="34008-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="34008-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34008-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34008-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34008-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34008-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="34008-126">See also</span></span>

- [<span data-ttu-id="34008-127">分析列舉</span><span class="sxs-lookup"><span data-stu-id="34008-127">Profiling Enumerations</span></span>](profiling-enumerations.md)
