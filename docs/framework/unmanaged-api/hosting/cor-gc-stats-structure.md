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
ms.openlocfilehash: 53a70c53a06ac55a2dab7c646018d63189ee0b36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726219"
---
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="33330-102">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="33330-102">COR_GC_STATS Structure</span></span>

<span data-ttu-id="33330-103">提供 common language runtime (CLR) 之垃圾收集機制的相關統計資料。</span><span class="sxs-lookup"><span data-stu-id="33330-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33330-104">語法</span><span class="sxs-lookup"><span data-stu-id="33330-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="33330-105">成員</span><span class="sxs-lookup"><span data-stu-id="33330-105">Members</span></span>  
  
|<span data-ttu-id="33330-106">member</span><span class="sxs-lookup"><span data-stu-id="33330-106">Member</span></span>|<span data-ttu-id="33330-107">描述</span><span class="sxs-lookup"><span data-stu-id="33330-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="33330-108">指出應該計算和傳回的域值。</span><span class="sxs-lookup"><span data-stu-id="33330-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="33330-109">指出外部要求強制執行的垃圾收集數目。</span><span class="sxs-lookup"><span data-stu-id="33330-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="33330-110">指出針對每個層代執行的垃圾收集數目。</span><span class="sxs-lookup"><span data-stu-id="33330-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="33330-111">所有堆積中認可的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="33330-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="33330-112">所有堆積中保留的 kb 總數。</span><span class="sxs-lookup"><span data-stu-id="33330-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="33330-113">層代零堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="33330-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="33330-114">第一個堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="33330-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="33330-115">第2代堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="33330-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="33330-116">大型物件堆積的大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="33330-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="33330-117">從層代零升級到層代1的物件大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="33330-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="33330-118">從層代1提升至層代二的物件大小（以 kb 為單位）。</span><span class="sxs-lookup"><span data-stu-id="33330-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33330-119">備註</span><span class="sxs-lookup"><span data-stu-id="33330-119">Remarks</span></span>  

 <span data-ttu-id="33330-120">[ICLRGCManager：： GetStats](iclrgcmanager-getstats-method.md)方法需要將 `Flags` 結構的欄位 `COR_GC_STATS` 設定為[COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md)列舉的一或多個值，以指定要設定的統計資料。</span><span class="sxs-lookup"><span data-stu-id="33330-120">The [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="33330-121">下表將此結構提供的統計資料對應至兩個 [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) 列舉值 `COR_GC_COUNTS` 和 `COR_GC_MEMORYUSAGE` 。</span><span class="sxs-lookup"><span data-stu-id="33330-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="33330-122">由 COR_GC_COUNTS 指定</span><span class="sxs-lookup"><span data-stu-id="33330-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="33330-123">由 COR_GC_MEMORYUSAGE 指定</span><span class="sxs-lookup"><span data-stu-id="33330-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="33330-124">使用方式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="33330-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="33330-125">需求</span><span class="sxs-lookup"><span data-stu-id="33330-125">Requirements</span></span>  

 <span data-ttu-id="33330-126">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33330-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33330-127">**標頭：** GCHost .idl</span><span class="sxs-lookup"><span data-stu-id="33330-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="33330-128">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="33330-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33330-129">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33330-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33330-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33330-130">See also</span></span>

- [<span data-ttu-id="33330-131">裝載結構</span><span class="sxs-lookup"><span data-stu-id="33330-131">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="33330-132">自動記憶體管理</span><span class="sxs-lookup"><span data-stu-id="33330-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="33330-133">記憶體回收</span><span class="sxs-lookup"><span data-stu-id="33330-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
