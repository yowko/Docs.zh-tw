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
ms.openlocfilehash: 0178e2a7877803644bb25e6700306d7ac2ef2d4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215887"
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="50fe0-102">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="50fe0-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="50fe0-103">識別記憶體回收層代。</span><span class="sxs-lookup"><span data-stu-id="50fe0-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50fe0-104">語法</span><span class="sxs-lookup"><span data-stu-id="50fe0-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="50fe0-105">成員</span><span class="sxs-lookup"><span data-stu-id="50fe0-105">Members</span></span>  
  
|<span data-ttu-id="50fe0-106">成員</span><span class="sxs-lookup"><span data-stu-id="50fe0-106">Member</span></span>|<span data-ttu-id="50fe0-107">描述</span><span class="sxs-lookup"><span data-stu-id="50fe0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="50fe0-108">此物件會儲存成層代 0。</span><span class="sxs-lookup"><span data-stu-id="50fe0-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="50fe0-109">物件會儲存為第 1 代。</span><span class="sxs-lookup"><span data-stu-id="50fe0-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="50fe0-110">此物件會儲存為第 2 代。</span><span class="sxs-lookup"><span data-stu-id="50fe0-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="50fe0-111">此物件會儲存大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="50fe0-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50fe0-112">備註</span><span class="sxs-lookup"><span data-stu-id="50fe0-112">Remarks</span></span>  
 <span data-ttu-id="50fe0-113">記憶體回收行程會提高成根據年齡層代將物件的記憶體管理效能。</span><span class="sxs-lookup"><span data-stu-id="50fe0-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="50fe0-114">記憶體回收行程目前使用三個層代，編號 0、 1 和 2，以及用於大型物件堆積的特殊區段。</span><span class="sxs-lookup"><span data-stu-id="50fe0-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="50fe0-115">其大小大於特定值的物件會儲存在大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="50fe0-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="50fe0-116">其他已配置的物件屬於層代 0 開始。</span><span class="sxs-lookup"><span data-stu-id="50fe0-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="50fe0-117">發生在層代 0 記憶體回收後存在的所有物件會都提升至層代 1。</span><span class="sxs-lookup"><span data-stu-id="50fe0-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="50fe0-118">存在之後發生在第 1 代記憶體回收的物件將移至第 2 代。</span><span class="sxs-lookup"><span data-stu-id="50fe0-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="50fe0-119">層代的使用，表示記憶體回收行程必須一次使用的配置的物件子集。</span><span class="sxs-lookup"><span data-stu-id="50fe0-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="50fe0-120">`COR_PRF_GC_GENERATION`列舉由[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="50fe0-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50fe0-121">需求</span><span class="sxs-lookup"><span data-stu-id="50fe0-121">Requirements</span></span>  
 <span data-ttu-id="50fe0-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="50fe0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50fe0-123">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="50fe0-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="50fe0-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50fe0-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="50fe0-125">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="50fe0-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="50fe0-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50fe0-126">See also</span></span>

- [<span data-ttu-id="50fe0-127">分析列舉</span><span class="sxs-lookup"><span data-stu-id="50fe0-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
