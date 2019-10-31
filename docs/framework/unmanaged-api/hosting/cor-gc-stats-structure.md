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
ms.openlocfilehash: 12c00ed009e0e57436a71aed256b07a58ba68a32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138354"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="4aec8-102">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="4aec8-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="4aec8-103">提供有關 common language runtime （CLR）之垃圾收集機制的統計資料。</span><span class="sxs-lookup"><span data-stu-id="4aec8-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4aec8-104">語法</span><span class="sxs-lookup"><span data-stu-id="4aec8-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4aec8-105">Members</span><span class="sxs-lookup"><span data-stu-id="4aec8-105">Members</span></span>  
  
|<span data-ttu-id="4aec8-106">成員</span><span class="sxs-lookup"><span data-stu-id="4aec8-106">Member</span></span>|<span data-ttu-id="4aec8-107">描述</span><span class="sxs-lookup"><span data-stu-id="4aec8-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="4aec8-108">指出應該計算並傳回的域值。</span><span class="sxs-lookup"><span data-stu-id="4aec8-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="4aec8-109">指出外部要求所強制執行的垃圾收集數目。</span><span class="sxs-lookup"><span data-stu-id="4aec8-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="4aec8-110">指出每個層代所執行的垃圾收集數目。</span><span class="sxs-lookup"><span data-stu-id="4aec8-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="4aec8-111">所有堆積中認可的總 kb 數。</span><span class="sxs-lookup"><span data-stu-id="4aec8-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="4aec8-112">所有堆積中保留的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="4aec8-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="4aec8-113">層代-零堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="4aec8-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="4aec8-114">層代-單一堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="4aec8-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="4aec8-115">層代-兩個堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="4aec8-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="4aec8-116">大型物件堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="4aec8-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="4aec8-117">從層代零升級到第一代的物件大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="4aec8-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="4aec8-118">從層代1升級至第二代的物件大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="4aec8-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4aec8-119">備註</span><span class="sxs-lookup"><span data-stu-id="4aec8-119">Remarks</span></span>  
 <span data-ttu-id="4aec8-120">[ICLRGCManager：： GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法需要將 `COR_GC_STATS` 結構的 `Flags` 欄位設定為[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉的一個或多個值，以指定要設定的統計資料。</span><span class="sxs-lookup"><span data-stu-id="4aec8-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="4aec8-121">下表將此結構提供的統計資料對應至兩個[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉值，`COR_GC_COUNTS` 和 `COR_GC_MEMORYUSAGE`。</span><span class="sxs-lookup"><span data-stu-id="4aec8-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="4aec8-122">由 COR_GC_COUNTS 指定</span><span class="sxs-lookup"><span data-stu-id="4aec8-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="4aec8-123">由 COR_GC_MEMORYUSAGE 指定</span><span class="sxs-lookup"><span data-stu-id="4aec8-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="4aec8-124">使用方式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="4aec8-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="4aec8-125">需求</span><span class="sxs-lookup"><span data-stu-id="4aec8-125">Requirements</span></span>  
 <span data-ttu-id="4aec8-126">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4aec8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4aec8-127">**標頭：** GCHost .idl</span><span class="sxs-lookup"><span data-stu-id="4aec8-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="4aec8-128">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4aec8-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4aec8-129">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4aec8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aec8-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="4aec8-130">See also</span></span>

- [<span data-ttu-id="4aec8-131">裝載結構</span><span class="sxs-lookup"><span data-stu-id="4aec8-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="4aec8-132">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="4aec8-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="4aec8-133">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="4aec8-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
