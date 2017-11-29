---
title: "COR_PRF_GC_GENERATION 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION
helpviewer_keywords: COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a296dd333579f9d0e734b7c00a8adb648605295d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="0ee3f-102">COR_PRF_GC_GENERATION 列舉</span><span class="sxs-lookup"><span data-stu-id="0ee3f-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="0ee3f-103">指出記憶體回收產生。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee3f-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ee3f-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="0ee3f-105">成員</span><span class="sxs-lookup"><span data-stu-id="0ee3f-105">Members</span></span>  
  
|<span data-ttu-id="0ee3f-106">成員</span><span class="sxs-lookup"><span data-stu-id="0ee3f-106">Member</span></span>|<span data-ttu-id="0ee3f-107">說明</span><span class="sxs-lookup"><span data-stu-id="0ee3f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="0ee3f-108">此物件會儲存成層代 0。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="0ee3f-109">此物件會儲存為第 1 代。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="0ee3f-110">此物件會儲存為第 2 代。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="0ee3f-111">此物件會儲存大型物件堆積中。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ee3f-112">備註</span><span class="sxs-lookup"><span data-stu-id="0ee3f-112">Remarks</span></span>  
 <span data-ttu-id="0ee3f-113">記憶體回收行程會提升成根據年齡層代將物件的記憶體管理效能。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="0ee3f-114">記憶體回收行程目前會使用三個層代，編號 0、 1 和 2，再加上用於大型物件堆積的特殊區段。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="0ee3f-115">其大小大於特定值的物件會儲存在大型物件堆積。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="0ee3f-116">其他已配置的物件屬於層代 0 開始。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="0ee3f-117">存在層代 0 記憶體回收後的所有物件會都提升至層代 1。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="0ee3f-118">已存在之後層代 1 中發生記憶體回收的物件將移至第 2 代。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="0ee3f-119">層代的使用，表示記憶體回收行程必須一次使用的配置物件的子集。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="0ee3f-120">`COR_PRF_GC_GENERATION`項列舉供[COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ee3f-121">需求</span><span class="sxs-lookup"><span data-stu-id="0ee3f-121">Requirements</span></span>  
 <span data-ttu-id="0ee3f-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ee3f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ee3f-123">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ee3f-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ee3f-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ee3f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ee3f-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ee3f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ee3f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ee3f-126">See Also</span></span>  
 [<span data-ttu-id="0ee3f-127">分析列舉</span><span class="sxs-lookup"><span data-stu-id="0ee3f-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
