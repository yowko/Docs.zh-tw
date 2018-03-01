---
title: "COR_GC_STAT_TYPES 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="ed2ed-102">COR_GC_STAT_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="ed2ed-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="ed2ed-103">指定要記錄的回收統計資料。</span><span class="sxs-lookup"><span data-stu-id="ed2ed-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed2ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="ed2ed-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="ed2ed-105">備註</span><span class="sxs-lookup"><span data-stu-id="ed2ed-105">Remarks</span></span>  
 <span data-ttu-id="ed2ed-106">此列舉會指定哪些統計資料中的[COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)結構是所要設定[iclrgcmanager:: Getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="ed2ed-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="ed2ed-107">成員</span><span class="sxs-lookup"><span data-stu-id="ed2ed-107">Members</span></span>  
  
|<span data-ttu-id="ed2ed-108">成員</span><span class="sxs-lookup"><span data-stu-id="ed2ed-108">Member</span></span>|<span data-ttu-id="ed2ed-109">描述</span><span class="sxs-lookup"><span data-stu-id="ed2ed-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="ed2ed-110">記錄每個層代的回收次數執行。</span><span class="sxs-lookup"><span data-stu-id="ed2ed-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="ed2ed-111">記錄的記憶體使用量和記憶體回收集合大小的統計資料。</span><span class="sxs-lookup"><span data-stu-id="ed2ed-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ed2ed-112">需求</span><span class="sxs-lookup"><span data-stu-id="ed2ed-112">Requirements</span></span>  
 <span data-ttu-id="ed2ed-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ed2ed-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed2ed-114">**標頭：** GCHost.idl、 GCHost.h</span><span class="sxs-lookup"><span data-stu-id="ed2ed-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="ed2ed-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed2ed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed2ed-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ed2ed-116">See Also</span></span>  
 [<span data-ttu-id="ed2ed-117">COR_GC_STATS 結構</span><span class="sxs-lookup"><span data-stu-id="ed2ed-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="ed2ed-118">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="ed2ed-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
