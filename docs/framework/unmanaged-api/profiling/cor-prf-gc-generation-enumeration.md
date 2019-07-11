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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74e70f58600205d44a9ba052981b2cc67b3a44ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753816"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="09e85-102">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="09e85-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="09e85-103">識別記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="09e85-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e85-104">語法</span><span class="sxs-lookup"><span data-stu-id="09e85-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="09e85-105">成員</span><span class="sxs-lookup"><span data-stu-id="09e85-105">Members</span></span>  
  
|<span data-ttu-id="09e85-106">成員</span><span class="sxs-lookup"><span data-stu-id="09e85-106">Member</span></span>|<span data-ttu-id="09e85-107">描述</span><span class="sxs-lookup"><span data-stu-id="09e85-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="09e85-108">此物件會儲存成層代 0。</span><span class="sxs-lookup"><span data-stu-id="09e85-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="09e85-109">物件會儲存為第 1 代。</span><span class="sxs-lookup"><span data-stu-id="09e85-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="09e85-110">此物件會儲存為第 2 代。</span><span class="sxs-lookup"><span data-stu-id="09e85-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="09e85-111">此物件會儲存大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="09e85-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09e85-112">備註</span><span class="sxs-lookup"><span data-stu-id="09e85-112">Remarks</span></span>  
 <span data-ttu-id="09e85-113">記憶體回收行程會提高成根據年齡層代將物件的記憶體管理效能。</span><span class="sxs-lookup"><span data-stu-id="09e85-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="09e85-114">記憶體回收行程目前使用三個層代，編號 0、 1 和 2，以及用於大型物件堆積的特殊區段。</span><span class="sxs-lookup"><span data-stu-id="09e85-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="09e85-115">其大小大於特定值的物件會儲存在大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="09e85-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="09e85-116">其他已配置的物件屬於層代 0 開始。</span><span class="sxs-lookup"><span data-stu-id="09e85-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="09e85-117">發生在層代 0 記憶體回收後存在的所有物件會都提升至層代 1。</span><span class="sxs-lookup"><span data-stu-id="09e85-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="09e85-118">存在之後發生在第 1 代記憶體回收的物件將移至第 2 代。</span><span class="sxs-lookup"><span data-stu-id="09e85-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="09e85-119">層代的使用，表示記憶體回收行程必須一次使用的配置的物件子集。</span><span class="sxs-lookup"><span data-stu-id="09e85-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="09e85-120">`COR_PRF_GC_GENERATION`列舉由[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="09e85-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e85-121">需求</span><span class="sxs-lookup"><span data-stu-id="09e85-121">Requirements</span></span>  
 <span data-ttu-id="09e85-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09e85-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09e85-123">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="09e85-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="09e85-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="09e85-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09e85-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09e85-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e85-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09e85-126">See also</span></span>

- [<span data-ttu-id="09e85-127">分析列舉</span><span class="sxs-lookup"><span data-stu-id="09e85-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
