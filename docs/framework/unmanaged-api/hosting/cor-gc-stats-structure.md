---
title: COR_GC_STATS 結構
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 630c365c8710388ae3e913bedece0fb710da7cd9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768131"
---
# <a name="corgcstats-structure"></a><span data-ttu-id="19bd2-102">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="19bd2-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="19bd2-103">提供 common language runtime (CLR) 記憶體回收機制的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="19bd2-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19bd2-104">語法</span><span class="sxs-lookup"><span data-stu-id="19bd2-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="19bd2-105">成員</span><span class="sxs-lookup"><span data-stu-id="19bd2-105">Members</span></span>  
  
|<span data-ttu-id="19bd2-106">成員</span><span class="sxs-lookup"><span data-stu-id="19bd2-106">Member</span></span>|<span data-ttu-id="19bd2-107">說明</span><span class="sxs-lookup"><span data-stu-id="19bd2-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="19bd2-108">表示欄位值，應該會計算並傳回。</span><span class="sxs-lookup"><span data-stu-id="19bd2-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="19bd2-109">指出所強制的外部要求記憶體回收數目。</span><span class="sxs-lookup"><span data-stu-id="19bd2-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="19bd2-110">表示執行每個層代的回收數目。</span><span class="sxs-lookup"><span data-stu-id="19bd2-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="19bd2-111">認可所有堆積中的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="19bd2-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="19bd2-112">保留所有堆積中的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="19bd2-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="19bd2-113">以 kb 為單位的層代 0 堆積大小。</span><span class="sxs-lookup"><span data-stu-id="19bd2-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="19bd2-114">以 kb 為單位，產生一個堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="19bd2-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="19bd2-115">以 kb 為單位，產生兩個堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="19bd2-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="19bd2-116">以 kb 為單位，大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="19bd2-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="19bd2-117">大小 （kb），從層代 0 提升至其中一個層代的物件。</span><span class="sxs-lookup"><span data-stu-id="19bd2-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="19bd2-118">大小 （kb），從一個層代升級至兩個層代的物件。</span><span class="sxs-lookup"><span data-stu-id="19bd2-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19bd2-119">備註</span><span class="sxs-lookup"><span data-stu-id="19bd2-119">Remarks</span></span>  
 <span data-ttu-id="19bd2-120">[Iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法需要`Flags`欄位`COR_GC_STATS`設為一或多個值的結構[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)来指定其列舉型別設定要統計資料。</span><span class="sxs-lookup"><span data-stu-id="19bd2-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="19bd2-121">下表對應至兩個這個結構所提供的統計資料[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉值`COR_GC_COUNTS`和`COR_GC_MEMORYUSAGE`。</span><span class="sxs-lookup"><span data-stu-id="19bd2-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="19bd2-122">指定 COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="19bd2-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="19bd2-123">指定 COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="19bd2-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="19bd2-124">使用方式的範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="19bd2-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="19bd2-125">需求</span><span class="sxs-lookup"><span data-stu-id="19bd2-125">Requirements</span></span>  
 <span data-ttu-id="19bd2-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="19bd2-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19bd2-127">**標頭：** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="19bd2-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="19bd2-128">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="19bd2-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="19bd2-129">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19bd2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bd2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19bd2-130">See also</span></span>

- [<span data-ttu-id="19bd2-131">裝載結構</span><span class="sxs-lookup"><span data-stu-id="19bd2-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="19bd2-132">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="19bd2-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="19bd2-133">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="19bd2-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
