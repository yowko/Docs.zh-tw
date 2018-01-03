---
title: "COR_GC_STATS 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 02a775be4976760b354a492e7252a67ef04eace9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstats-structure"></a><span data-ttu-id="625a5-102">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="625a5-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="625a5-103">提供有關 common language runtime (CLR) 記憶體回收機制統計資料。</span><span class="sxs-lookup"><span data-stu-id="625a5-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="625a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="625a5-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="625a5-105">成員</span><span class="sxs-lookup"><span data-stu-id="625a5-105">Members</span></span>  
  
|<span data-ttu-id="625a5-106">成員</span><span class="sxs-lookup"><span data-stu-id="625a5-106">Member</span></span>|<span data-ttu-id="625a5-107">描述</span><span class="sxs-lookup"><span data-stu-id="625a5-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="625a5-108">表示要計算及傳回的欄位值。</span><span class="sxs-lookup"><span data-stu-id="625a5-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="625a5-109">指出所強制的外部要求的記憶體回收數目。</span><span class="sxs-lookup"><span data-stu-id="625a5-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="625a5-110">表示執行每個層代的回收次數。</span><span class="sxs-lookup"><span data-stu-id="625a5-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="625a5-111">認可所有堆積中的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="625a5-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="625a5-112">保留所有堆積中的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="625a5-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="625a5-113">以 kb 為單位，層代 0 堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="625a5-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="625a5-114">以 kb 為單位，產生一個堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="625a5-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="625a5-115">以 kb 為單位，產生兩個堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="625a5-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="625a5-116">以 kb 為單位，在大型物件堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="625a5-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="625a5-117">大小，以 kb 為單位，從層代 0 提升至其中一個層代的物件。</span><span class="sxs-lookup"><span data-stu-id="625a5-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="625a5-118">大小，以 kb 為單位，從一個層代升級至兩個層代的物件。</span><span class="sxs-lookup"><span data-stu-id="625a5-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="625a5-119">備註</span><span class="sxs-lookup"><span data-stu-id="625a5-119">Remarks</span></span>  
 <span data-ttu-id="625a5-120">[Iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法需要`Flags`欄位`COR_GC_STATS`結構來設定的一或多個值[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)以指定的列舉設定為統計資料。</span><span class="sxs-lookup"><span data-stu-id="625a5-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="625a5-121">下表將對應到兩個此結構所提供的統計資料[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列舉值`COR_GC_COUNTS`和`COR_GC_MEMORYUSAGE`。</span><span class="sxs-lookup"><span data-stu-id="625a5-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="625a5-122">指定 COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="625a5-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="625a5-123">指定 COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="625a5-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="625a5-124">使用方式的範例如下所示：</span><span class="sxs-lookup"><span data-stu-id="625a5-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="625a5-125">需求</span><span class="sxs-lookup"><span data-stu-id="625a5-125">Requirements</span></span>  
 <span data-ttu-id="625a5-126">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="625a5-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="625a5-127">**標頭：** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="625a5-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="625a5-128">**程式庫：**包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="625a5-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="625a5-129">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="625a5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625a5-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="625a5-130">See Also</span></span>  
 [<span data-ttu-id="625a5-131">裝載結構</span><span class="sxs-lookup"><span data-stu-id="625a5-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="625a5-132">自動管理記憶體</span><span class="sxs-lookup"><span data-stu-id="625a5-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="625a5-133">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="625a5-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
