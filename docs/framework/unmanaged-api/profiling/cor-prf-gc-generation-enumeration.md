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
ms.openlocfilehash: b7a068efcf20b2028e9c193567d15b59e582febf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500919"
---
# <a name="cor_prf_gc_generation-enumeration"></a><span data-ttu-id="1aba5-102">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="1aba5-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="1aba5-103">識別垃圾收集的產生。</span><span class="sxs-lookup"><span data-stu-id="1aba5-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aba5-104">語法</span><span class="sxs-lookup"><span data-stu-id="1aba5-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3,
    COR_PRF_GC_PINNED_OBJECT_HEAP= 4
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="1aba5-105">成員</span><span class="sxs-lookup"><span data-stu-id="1aba5-105">Members</span></span>  
  
|<span data-ttu-id="1aba5-106">成員</span><span class="sxs-lookup"><span data-stu-id="1aba5-106">Member</span></span>|<span data-ttu-id="1aba5-107">說明</span><span class="sxs-lookup"><span data-stu-id="1aba5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="1aba5-108">物件會儲存為層代0。</span><span class="sxs-lookup"><span data-stu-id="1aba5-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="1aba5-109">物件會儲存為第1代。</span><span class="sxs-lookup"><span data-stu-id="1aba5-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="1aba5-110">物件會儲存為層代2。</span><span class="sxs-lookup"><span data-stu-id="1aba5-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="1aba5-111">物件會儲存在大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="1aba5-111">The object is stored in the large-object heap.</span></span>|  
|`COR_PRF_GC_PINNED_OBJECT_HEAP`|<span data-ttu-id="1aba5-112">物件會儲存在釘選的物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="1aba5-112">The object is stored in the pinned-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1aba5-113">備註</span><span class="sxs-lookup"><span data-stu-id="1aba5-113">Remarks</span></span>  
 <span data-ttu-id="1aba5-114">垃圾收集行程藉由將物件根據年齡分割成層代，來改善記憶體管理效能。</span><span class="sxs-lookup"><span data-stu-id="1aba5-114">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="1aba5-115">垃圾收集行程目前使用三個層代，編號為0、1和2，以及兩個特殊堆積區段，一個用於大型物件，一個用於釘選的物件。</span><span class="sxs-lookup"><span data-stu-id="1aba5-115">The garbage collector currently uses three generations, numbered 0, 1, and 2, and two special heap segments, one for large objects and one for pinned objects.</span></span>
  
 <span data-ttu-id="1aba5-116">其大小大於臨界值的物件會儲存在大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="1aba5-116">Objects whose size is larger than a threshold value are stored in the large-object heap.</span></span> <span data-ttu-id="1aba5-117">釘選的物件可以配置到釘選的物件堆積，以避免在一般堆積上配置它們的效能成本。</span><span class="sxs-lookup"><span data-stu-id="1aba5-117">Pinned objects can be allocated to the pinned-object heap to avoid the performance cost of allocating them on the normal heaps.</span></span> <span data-ttu-id="1aba5-118">其他已配置的物件會從屬於層代0開始。</span><span class="sxs-lookup"><span data-stu-id="1aba5-118">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="1aba5-119">在層代0中進行垃圾收集之後存在的所有物件都會升級至層代1。</span><span class="sxs-lookup"><span data-stu-id="1aba5-119">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="1aba5-120">在層代1中進行垃圾收集後存在的物件會移至層代2。</span><span class="sxs-lookup"><span data-stu-id="1aba5-120">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="1aba5-121">使用世代表示垃圾收集行程在任何時候都只能處理已設定物件的子集。</span><span class="sxs-lookup"><span data-stu-id="1aba5-121">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="1aba5-122">`COR_PRF_GC_GENERATION` [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md)結構會使用列舉型別。</span><span class="sxs-lookup"><span data-stu-id="1aba5-122">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aba5-123">規格需求</span><span class="sxs-lookup"><span data-stu-id="1aba5-123">Requirements</span></span>  
 <span data-ttu-id="1aba5-124">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1aba5-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aba5-125">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1aba5-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1aba5-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aba5-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aba5-127">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aba5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aba5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1aba5-128">See also</span></span>

- [<span data-ttu-id="1aba5-129">分析列舉</span><span class="sxs-lookup"><span data-stu-id="1aba5-129">Profiling Enumerations</span></span>](profiling-enumerations.md)
