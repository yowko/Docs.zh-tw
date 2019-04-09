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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a4b56270318a05d0e5a480fdb56eb45593d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177732"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="71f16-102">COR_GC_THREAD_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="71f16-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="71f16-103">包含有關記憶體回收的每個執行緒統計資料。</span><span class="sxs-lookup"><span data-stu-id="71f16-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f16-104">語法</span><span class="sxs-lookup"><span data-stu-id="71f16-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="71f16-105">成員</span><span class="sxs-lookup"><span data-stu-id="71f16-105">Members</span></span>  
  
|<span data-ttu-id="71f16-106">成員</span><span class="sxs-lookup"><span data-stu-id="71f16-106">Member</span></span>|<span data-ttu-id="71f16-107">描述</span><span class="sxs-lookup"><span data-stu-id="71f16-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="71f16-108">目前與相關聯的執行緒上配置的記憶體位元組數目`COR_GC_THREAD_STATS`執行個體。</span><span class="sxs-lookup"><span data-stu-id="71f16-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="71f16-109">每次在層代 0 記憶體回收時清除這個數字為零。</span><span class="sxs-lookup"><span data-stu-id="71f16-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="71f16-110">位元組數目提升至更高的層代最新的回收。</span><span class="sxs-lookup"><span data-stu-id="71f16-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71f16-111">備註</span><span class="sxs-lookup"><span data-stu-id="71f16-111">Remarks</span></span>  
 <span data-ttu-id="71f16-112">[Iclrtask:: Getmemstats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)會採用輸出參數的型別`COR_GC_THREAD_STATS`。</span><span class="sxs-lookup"><span data-stu-id="71f16-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f16-113">需求</span><span class="sxs-lookup"><span data-stu-id="71f16-113">Requirements</span></span>  
 <span data-ttu-id="71f16-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="71f16-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f16-115">**標頭：** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="71f16-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="71f16-116">**LIBRARY:** 包含做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="71f16-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="71f16-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="71f16-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="71f16-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71f16-118">See also</span></span>

- [<span data-ttu-id="71f16-119">裝載結構</span><span class="sxs-lookup"><span data-stu-id="71f16-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="71f16-120">IHostTask 介面</span><span class="sxs-lookup"><span data-stu-id="71f16-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
