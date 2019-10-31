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
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136977"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="9fb2e-102">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="9fb2e-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="9fb2e-103">包含有關垃圾收集的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="9fb2e-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="9fb2e-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="9fb2e-105">Members</span><span class="sxs-lookup"><span data-stu-id="9fb2e-105">Members</span></span>  
  
|<span data-ttu-id="9fb2e-106">成員</span><span class="sxs-lookup"><span data-stu-id="9fb2e-106">Member</span></span>|<span data-ttu-id="9fb2e-107">描述</span><span class="sxs-lookup"><span data-stu-id="9fb2e-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="9fb2e-108">在與目前 `COR_GC_THREAD_STATS` 實例相關聯的執行緒上配置的記憶體位元組數目。</span><span class="sxs-lookup"><span data-stu-id="9fb2e-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="9fb2e-109">每次發生層代零垃圾收集時，這個數位就會清除為零。</span><span class="sxs-lookup"><span data-stu-id="9fb2e-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="9fb2e-110">在最近一次垃圾收集時，升級至較高層代的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="9fb2e-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fb2e-111">備註</span><span class="sxs-lookup"><span data-stu-id="9fb2e-111">Remarks</span></span>  
 <span data-ttu-id="9fb2e-112">[ICLRTask：： GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)接受 `COR_GC_THREAD_STATS`類型的輸出參數。</span><span class="sxs-lookup"><span data-stu-id="9fb2e-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb2e-113">需求</span><span class="sxs-lookup"><span data-stu-id="9fb2e-113">Requirements</span></span>  
 <span data-ttu-id="9fb2e-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9fb2e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb2e-115">**標頭：** GCHost .idl</span><span class="sxs-lookup"><span data-stu-id="9fb2e-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="9fb2e-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="9fb2e-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fb2e-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb2e-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="9fb2e-118">See also</span></span>

- [<span data-ttu-id="9fb2e-119">裝載結構</span><span class="sxs-lookup"><span data-stu-id="9fb2e-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="9fb2e-120">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="9fb2e-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
