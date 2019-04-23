---
title: COR_GC_THREAD_STATS_TYPES 列舉
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c631a0a3abb3cb2a342dfd44fdffb147b742ae3c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212462"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="0c5d0-102">COR_GC_THREAD_STATS_TYPES 列舉</span><span class="sxs-lookup"><span data-stu-id="0c5d0-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="0c5d0-103">表示執行緒的記憶體回收集合統計資料。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c5d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="0c5d0-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="0c5d0-105">成員</span><span class="sxs-lookup"><span data-stu-id="0c5d0-105">Members</span></span>  
  
|<span data-ttu-id="0c5d0-106">成員</span><span class="sxs-lookup"><span data-stu-id="0c5d0-106">Member</span></span>|<span data-ttu-id="0c5d0-107">描述</span><span class="sxs-lookup"><span data-stu-id="0c5d0-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="0c5d0-108">執行緒已升級最新的記憶體回收集合中的位元組。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c5d0-109">需求</span><span class="sxs-lookup"><span data-stu-id="0c5d0-109">Requirements</span></span>  
 <span data-ttu-id="0c5d0-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0c5d0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c5d0-111">**標頭：** GCHost.idl GCHost.h</span><span class="sxs-lookup"><span data-stu-id="0c5d0-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="0c5d0-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c5d0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5d0-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c5d0-113">See also</span></span>

- [<span data-ttu-id="0c5d0-114">裝載列舉</span><span class="sxs-lookup"><span data-stu-id="0c5d0-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
