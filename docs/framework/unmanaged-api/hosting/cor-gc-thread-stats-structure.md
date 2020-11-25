---
title: COR_GC_THREAD_STATS 結構
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 25a90965dc5466b7cf1a07140705424cf2ba4cd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699231"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="f1bb0-102">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="f1bb0-102">COR_GC_THREAD_STATS Structure</span></span>

<span data-ttu-id="f1bb0-103">包含與垃圾收集相關的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bb0-104">語法</span><span class="sxs-lookup"><span data-stu-id="f1bb0-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="f1bb0-105">成員</span><span class="sxs-lookup"><span data-stu-id="f1bb0-105">Members</span></span>  
  
|<span data-ttu-id="f1bb0-106">member</span><span class="sxs-lookup"><span data-stu-id="f1bb0-106">Member</span></span>|<span data-ttu-id="f1bb0-107">描述</span><span class="sxs-lookup"><span data-stu-id="f1bb0-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="f1bb0-108">在與目前實例相關聯的執行緒上配置的記憶體位元組數目 `COR_GC_THREAD_STATS` 。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="f1bb0-109">每次發生層代零垃圾收集時，這個數位就會清除為零。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="f1bb0-110">在最近的垃圾收集上提升為較高世代的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1bb0-111">備註</span><span class="sxs-lookup"><span data-stu-id="f1bb0-111">Remarks</span></span>  

 <span data-ttu-id="f1bb0-112">[ICLRTask：： GetMemStats](iclrtask-getmemstats-method.md) 接受型別為的 output 參數 `COR_GC_THREAD_STATS` 。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1bb0-113">需求</span><span class="sxs-lookup"><span data-stu-id="f1bb0-113">Requirements</span></span>  

 <span data-ttu-id="f1bb0-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f1bb0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1bb0-115">**標頭：** GCHost .idl</span><span class="sxs-lookup"><span data-stu-id="f1bb0-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="f1bb0-116">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="f1bb0-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1bb0-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1bb0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bb0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1bb0-118">See also</span></span>

- [<span data-ttu-id="f1bb0-119">裝載結構</span><span class="sxs-lookup"><span data-stu-id="f1bb0-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="f1bb0-120">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="f1bb0-120">IHostTask Interface</span></span>](ihosttask-interface.md)
