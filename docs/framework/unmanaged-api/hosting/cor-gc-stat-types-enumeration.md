---
title: COR_GC_STAT_TYPES 列舉
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fdfe33c5b488d8f464001a86233124d4e7df0ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779076"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="5bd3e-102">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="5bd3e-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="5bd3e-103">指定要記錄的記憶體回收的統計資料。</span><span class="sxs-lookup"><span data-stu-id="5bd3e-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bd3e-104">語法</span><span class="sxs-lookup"><span data-stu-id="5bd3e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="5bd3e-105">備註</span><span class="sxs-lookup"><span data-stu-id="5bd3e-105">Remarks</span></span>  
 <span data-ttu-id="5bd3e-106">此列舉會指定在哪些統計資料[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構是由設定[iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5bd3e-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="5bd3e-107">成員</span><span class="sxs-lookup"><span data-stu-id="5bd3e-107">Members</span></span>  
  
|<span data-ttu-id="5bd3e-108">成員</span><span class="sxs-lookup"><span data-stu-id="5bd3e-108">Member</span></span>|<span data-ttu-id="5bd3e-109">說明</span><span class="sxs-lookup"><span data-stu-id="5bd3e-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="5bd3e-110">記錄執行每個層代記憶體回收的數目。</span><span class="sxs-lookup"><span data-stu-id="5bd3e-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="5bd3e-111">記錄的記憶體使用量和記憶體回收集合大小統計資料。</span><span class="sxs-lookup"><span data-stu-id="5bd3e-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5bd3e-112">需求</span><span class="sxs-lookup"><span data-stu-id="5bd3e-112">Requirements</span></span>  
 <span data-ttu-id="5bd3e-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5bd3e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bd3e-114">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="5bd3e-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="5bd3e-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bd3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd3e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd3e-116">See also</span></span>

- [<span data-ttu-id="5bd3e-117">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="5bd3e-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="5bd3e-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="5bd3e-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
