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
ms.openlocfilehash: 4bd12feb47352d9bb78aa8ef056072f9bdc6fba3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710322"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="30ab4-102">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="30ab4-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="30ab4-103">指定要記錄的記憶體回收的統計資料。</span><span class="sxs-lookup"><span data-stu-id="30ab4-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ab4-104">語法</span><span class="sxs-lookup"><span data-stu-id="30ab4-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="30ab4-105">備註</span><span class="sxs-lookup"><span data-stu-id="30ab4-105">Remarks</span></span>  
 <span data-ttu-id="30ab4-106">此列舉會指定在哪些統計資料[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構是由設定[iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="30ab4-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="30ab4-107">成員</span><span class="sxs-lookup"><span data-stu-id="30ab4-107">Members</span></span>  
  
|<span data-ttu-id="30ab4-108">成員</span><span class="sxs-lookup"><span data-stu-id="30ab4-108">Member</span></span>|<span data-ttu-id="30ab4-109">描述</span><span class="sxs-lookup"><span data-stu-id="30ab4-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="30ab4-110">記錄執行每個層代記憶體回收的數目。</span><span class="sxs-lookup"><span data-stu-id="30ab4-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="30ab4-111">記錄的記憶體使用量和記憶體回收集合大小統計資料。</span><span class="sxs-lookup"><span data-stu-id="30ab4-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30ab4-112">需求</span><span class="sxs-lookup"><span data-stu-id="30ab4-112">Requirements</span></span>  
 <span data-ttu-id="30ab4-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="30ab4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30ab4-114">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="30ab4-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="30ab4-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30ab4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ab4-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30ab4-116">See also</span></span>
- [<span data-ttu-id="30ab4-117">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="30ab4-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="30ab4-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="30ab4-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
